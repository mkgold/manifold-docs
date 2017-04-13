# Configuration

In an effort to make Manifold applicable to a wide range of publishing use cases, much of Manifold's functionality can be configured and customized. 

## Configuration Locations

Manifold's configuration is stored in two primary places: 1\) the environment, and 2\) a settings model stored in the database. 

In the root directory of a Manifold installation, there is a file called `.env`. This file includes constants that are made available to both the client and the server application, as well as all associated background services when Manifold is started. While a sample version of this file—`.env.sample`—is stored in the Manifold source code repository, this file is not tracked and can be modified in each Manifold installation. 

The Manifold backend also provides administrative users with the ability to modify some settings on the fly. These settings typically do not require that Manifold services be started and stopped for changes to take effect. However, you will likely need to reload the page in your browser to force the client application to fetch updated settings.

## Third-Party Integrations

Manifold is able to integrate with external services provided by Facebook, Twitter, and Google for social sharing, authentication, and analytics. These integrations take place over public, documented APIs offered by the third party providers, and generally speaking require API keys for authentication. Details on how to acquire those keys are included below.

* [Facebook oAuth and Sharing Integration](/external-services/facebook.md)
* [Twitter oAuth and Sharing Integration](/external-services/twitter.md)
* [Google oAuth Integration](/external-services/google.md)
* [Google Analytics Integration](/external-services/google-analytics.md)
* Typekit \(to be written\)



