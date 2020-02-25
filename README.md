# IMS: Volto Frontend

Volto frontend based on [eea/volto-starter-kit](eea/volto-starter-kit)

## Documentation

A training on how to create your own website using Volto is available as part of the Plone training at [https://training.plone.org/5/volto/index.html](https://training.plone.org/5/volto/index.html).


## Try it

1. Install [Docker](https://docs.docker.com/install/)
1. Install [Docker Compose](https://docs.docker.com/compose/install/)
1. Start:

        $ docker-compose pull
        $ docker-compose up -d

    optionally change `PORTS` via `.env`:

        $ FRONTEND=9000 BACKEND=9100 docker-compose up -d

1. Go to `http://localhost:8080` [Advanced](http://localhost:8080/@@plone-addsite?site_id=Plone&advanced=1):
   * Add `Plone` site with add-ons enabled (**user:** `admin`, **password:** `admin`):
     * `eea.restapi`
     * `kitconcept.voltodemo`

1. See application at http://localhost:8000


## Development

1. Install `nvm`

        $ touch ~/.bash_profile
        $ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash

        $ source ~/.bash_profile
        $ nvm version

1. Install latest `NodeJS 10.x`:

        $ nvm install 10
        $ nvm use 10
        $ node -v
        v10.19.0

1. Install `yarn`

        $ curl -o- -L https://yarnpkg.com/install.sh | bash
        $ yarn -v

1. Install and run `mrs-develop`

        $ npm -g i mrs-develop
        $ missdev

1. Activate `develop` add-ons

        $ make activate-all

1. Install

        $ npm install

1. Start backend

         $ docker-compose up -d

   * Go to `http://localhost:8080` [Advanced](http://localhost:8080/@@plone-addsite?site_id=Plone&advanced=1):
   * Add `Plone` site with add-ons enabled (**user:** `admin`, **password:** `admin`):
     * `eea.restapi`
     * `kitconcept.voltodemo`

1. Start frontend

        $ yarn start

1. See application at http://localhost:3000


## Boostrap new `EEA Volto Frontend` project

* **Github > eea/volto-starter-kit** click on [Use this template](https://github.com/eea/volto-starter-kit/generate)


## Synchronize your `EEA Volto Frontend` project

Synchronize git templates generated by GitHub as if they were forks.

In order to synchronize a child instance of Github [eea/volto-starter-kit template](https://github.com/eea/volto-starter-kit) template you can run:

        $ make sync


## Production

We use [Docker](https://www.docker.com/), [Rancher](https://rancher.com/) and [Jenkins](https://jenkins.io/) to deploy this application in production.

### Deploy

* Within `Rancher > Catalog > EEA` deploy [Volto](https://github.com/eea/eea.rancher.catalog/tree/master/templates/volto)

### Release

* Create a new release of this code via `git tag` command or [Draft new release](https://github.com/eea/ims-frontend/releases/new) on Github.
  * A new Docker image is built and released automatically on [DockerHub](https://hub.docker.com/r/eeacms/ims-frontend) based on this tag.
  * A new entry is automatically added to [Volto](https://github.com/eea/eea.rancher.catalog/tree/master/templates/volto) `EEA Rancher Catalog`

### Upgrade

* Within your Rancher environment click on the `Upgrade available` yellow button next to your stack.

* Confirm the upgrade

* Or roll-back if something went wrong and abort the upgrade procedure.
