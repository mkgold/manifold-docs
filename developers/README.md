# Developers

Manifold is an open source web application, covered under version 3 of the the General Public License (GPL). It is primarily written in Javascript (ES6) and Ruby. We encourage developers in the broader academic community to contribute and pull requests are always welcome. All Manifold related code is stored on Github, under the ManifoldScholar Github Organization. The primary repository for the Manifold application, including the server-side and client-side components, is located at https://github.com/ManifoldScholar/manifold.

## Overview

Manifold is a web application that runs primarily on Ruby on Rails and a Node/Express server. The Rails application is responsible solely for backend API services and the ingestion and storage of Manifold texts and resources. The Node + Express application is responsible for the initial page render, which is universal (or, isomorphic). The client-side component of Manifold is a single page javascript application built on React and Redux. The API server stores its data in a Postgres database. The backend server is built to run in a Linux environment, and our developers test and host it on Ubuntu 14 and Ubuntu 16 LTS versions. It is probably possible to run Manifold in a Windows environment, but your mileage my vary.
