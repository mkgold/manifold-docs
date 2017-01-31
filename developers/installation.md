# Installation

_Nota bene_: Manifold is very much a work in progress, and the installation story will likely change as we move toward a stable release. We'll update this document durign development, in an effort to keep it fairly current, but expect things to be in flux for a while. In the future, we expect to provide Docker containers and Vagrant boxes with Manifold pre-configured, to make it easier to get up and running.

### Requirements

In ortder to run Manifold, you'll need the most recent stable version of Ruby, and the most recent LTS version of Node. We track the versions we target in the repository's [.ruby-version](https://github.com/ManifoldScholar/manifold/blob/development/api/.ruby-version) and [.node-version](https://github.com/ManifoldScholar/manifold/blob/development/client/.node-version) files. At the time of writing, we expect the host to be running Ruby 2.2.3 and Node 4.5.0. These installation documents do not cover installing Ruby or Node. That said, the Manifold development team generally uses [Rbenv](https://github.com/rbenv/rbenv) and [Nodenv](https://github.com/nodenv/nodenv) to manage Ruby and Node executables in our OSX development environments.

You will also need a functioning installation of Postgres. We use Homebrew to manage our OSX Postgres installation. The Postgres website provides instructions on [installing Postgres on OSX](https://www.postgresql.org/download/macosx/). There are also a number of helpful resources online about running Postgres in a development environment, [such as this one.](https://www.codefellows.org/blog/three-battle-tested-ways-to-install-postgresql/)

Manifold search relies on ElasticSearch, which in turn relies on Java. On our development, staging, and production hosts, we are running ElasticSearch 5.1.x and Java 8. As with other dependencies, we've had good luck installing ElasticSearch with Homebrew on our development machines. 

Finally, you'll want to have Redis installed for processing background jobs. Again, we've had good luck installing it with Homebrew: `brew install redis`

### 1. Clone the repository

Because we rely heavily on Boxen for configuring our development environments, we typically store our projects in `~\/src`, and these instructions will follow that convention. Of course, you can put it wherever you prefer. Start off by cloning the remote repository:

```
cd ~/src
git clone https://github.com/ManifoldScholar/manifold.git
cd ~/src/manifold
```

### 2. Install top-level dependencies \(optional\)

We deploy Manifold to staging and production servers using Capistrano. The global deployment configuration is stored in /config. The Gemfile in the root of the repository includes Capistrano related dependencies. If you plan on deploying with Capistrano, you'll need to install these dependencies with bundler"

`bundle install`

### 3. Install API dependencies

We'll start the API server \(Rails\) before we setup and start the client application. The API is like most Rails projects, and to run it you'll need to install gem dependenceies, create the database, run migrations, and start the server.

```
cd ~/src/manifold/api
bundle install
rake db:create
rake db:migrate
rake db:seed
cp .env.sampl .env
```

### 4. Setup the API Environment

Note the last command, in which you copy and rename the sample .env file. In keeping with the [principals of a 12-factor app](https://12factor.net/), we use dotenv to [store configuration in the environment](https://12factor.net/config). You'll need to update this .env file to contain other environment-specific configuration as follows:

```
export API_DOMAIN={the domain you want to serve the API on}
export APP_SOCKET_PATH={path to where the socket should be placed, optional}
export API_PORT={port you want to run the API on. Defaults to 3008} 
export SECRET_KEY={your key}
export RAILS_DB_USER={db username}
export RAILS_DB_PASS={db password}
export RAILS_DB_NAME={db name}
```

Our team typically serves Rails apps on unix sockets during development, and proxies to them using Nginx. We do this, rather than running the Rails app on a specific port as is the norm, so that we can access the various projects we're working on via the domain name during development. We recognize that this workflow may not work for you, which is why we also provide it as a socket. The API\_DOMAIN variable is necessary so that links to content on the API server \(such as EPUB resources\) can be generated. If, for example, you're running the API locally on port 3008, you'd want API\_DOMAIN to be "[http://127.0.0.1](http://127.0.0.1)" and the API\_PORT to be "3008".

### 5. Start the API server

Go ahead and start the API server.

```
cd ~/src/manifold/api
./bin/puma
```

If all goes according to plan, you should see output more or less like this, depending on your environment:

```
Puma starting in single mode...
* Version 3.6.0 (ruby 2.2.3-p173), codename: Sleepy Sunday Serenity
* Min threads: 0, max threads: 16
* Environment: development
* Listening on unix:///opt/boxen/data/project-sockets/manifold-api
* Listening on tcp://127.0.0.1:3008
* Starting control server on unix:///opt/boxen/data/project-sockets/manifold-api-control
Use Ctrl-C to stop
```

### 6. Import some EPUBs

Eventually, Manifold will have a backend interface for adding texts to projects. Until that is completed, this takes place through the command line interface. Drop some EPUB files in ~/src/manifold/user\_texts and execute a rake task to ingest them into the application:

```
rake ingest:user_texts
```

### 7. Install client dependencies

Navigate to the client directory and install NPM dependencies. If you don't have NPM installed, [go ahead and install it](http://blog.npmjs.org/post/85484771375/how-to-install-npm).

```
cd ~/src/manifold/client
npm install
```

The initial installation of NPM packages could take a few minutes, so be patient!

### 8. Start the client server

From the client directory, start the client server. There are a number of commands in the `/client/package.json` that we use for starting servers, building assets, etc. Go ahead and start the server:

```
npm run start
```

You'll see a bit of output, including this summary:

```
🎉 MANIFOLD WEBPACK SERVER
-------------------------------------------------------------------------------
Manifold Asset Server, a.k.a. Webpack, is listening at http://127.0.0.1:3001

🌎 MANIFOLD REST API
-------------------------------------------------------------------------------
The Manifold client expects to find the API at the following paths:

http://manifold-api.dev:80/api
http://manifold-api.dev:80/system

📚 UNIVERSAL CLIENT SERVER
-------------------------------------------------------------------------------
Manifold Client is listening at http://127.0.0.1:3002
```

This should start the Manifold client app on port 3000. Visit [http://localhost:3000](http://localhost:3000) and see if it worked!

Depending on how you run the API, you may need to update /client/.env to point to it. There's a variable in the client environment, MANIFOLD\_API\_URL, that tells the client how where to locate the API backend. Adjust this environment variable to match your approach to running the API.

