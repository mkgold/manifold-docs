# Installation

_Nota bene_: Manifold is very much a work in progress, and the installation story will likely change as we move toward a stable release. We'll update this document durign development, in an effort to keep it fairly current, but expect things to be in flux for a while. In the future, we expect to provide Docker containers and Vagrant boxes with Manifold pre-configured, to make it easier to get up and running.

### Requirements

In ortder to run Manifold, you'll need the most recent stable version of Ruby, and the most recent LTS version of Node. We track the versions we target in the repository's [.ruby-version](https://github.com/ManifoldScholar/manifold/blob/development/api/.ruby-version) and [.node-version](https://github.com/ManifoldScholar/manifold/blob/development/client/.node-version) files. At the time of writing, we expect the host to be running Ruby 2.2.3 and Node 4.5.0. These installation documents do not cover installing Ruby or Node. That said, the Manifold development team generally uses [Rbenv](https://github.com/rbenv/rbenv) and [Nodenv](https://github.com/nodenv/nodenv) to manage Ruby and Node executables in our OSX development environments.

You will also need a functioning installation of Postgres. We use Homebrew to manage our OSX Postgres installation. The Postgres website provides instructions on [installing Postgres on OSX](https://www.postgresql.org/download/macosx/). There are also a number of helpful resources online about running Postgres in a development environment, [such as this one.](https://www.codefellows.org/blog/three-battle-tested-ways-to-install-postgresql/)

Finally, you'll want to have Redis installed for processing background jobs. Again, we've had good luck installing it with Homebrew: `brew install redis`

### 1. Clone the repository

Because we rely heavily on Boxen for configuring our development environments, we typically store our projects in `~\/src`, and these instructions will follow that convention. Of course, you can put it wherever you prefer. Start off by cloning the remote repository:

```
cd ~/src
git clone https://github.com/ManifoldScholar/manifold.git
```


### 2. 

