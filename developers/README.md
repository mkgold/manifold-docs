# Manifold for Developers

Manifold is an [open source web application](https://github.com/ManifoldScholar/manifold/blob/development/LICENSE.md), covered under the the General Public License v3 \(GPL\). It is primarily written in Javascript \(ES6\) and Ruby. We encourage developers in the broader academic community to contribute and pull requests are always welcome. All Manifold related code is stored on Github, under the [ManifoldScholar Github Organization](https://github.com/ManifoldScholar). The [primary repository](https://github.com/ManifoldScholar/manifold) for the Manifold application, including the [server-side](https://github.com/ManifoldScholar/manifold/tree/development/api) and [client-side](https://github.com/ManifoldScholar/manifold/tree/development/client) components, is located at [https:\/\/github.com\/ManifoldScholar\/manifold](https://github.com/ManifoldScholar/manifold).

### Overview

Manifold is a web application that runs primarily on [Ruby on Rails](http://rubyonrails.org/) and a [Node](https://nodejs.org/en/) / [Express](https://expressjs.com/) server. The Rails application is responsible solely for backend API services and the ingestion and storage of Manifold texts and resources. The Node + Express application is responsible for the initial page render, which is universal \(or, isomorphic\). The client-side component of Manifold is a single page javascript application built on [React](https://facebook.github.io/react/) and [Redux](http://redux.js.org/). The API server stores its data in a [Postgres](https://www.postgresql.org/) database. The backend server is built to run in a Linux environment, and our developers test and host it on Ubuntu 14 and Ubuntu 16 LTS versions. It is probably possible to run Manifold in a Windows environment, but your mileage my vary.

The following diagram provides a high level overview of Manifold's architecture.

![](/assets/diagram-manifold.jpg)

### Contributing

To contribute to Manifold, you'll want to setup a local development environment. Read the [Installation guide](/developers/installation.md) to learn how to install Manifold in your local development environment.

