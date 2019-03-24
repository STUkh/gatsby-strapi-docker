# [Gatsby](https://www.gatsbyjs.org/) [Strapi](https://github.com/strapi/strapi) [Docker](https://www.docker.com/) 🐳 example 

## 🚀 Quick start

1.  Install Docker

1.  **Start developing.**

    Just startup all your environment with one of this commands

    `docker-compose -f docker-compose.yaml -f docker-compose.dev.yaml up` or `npm run docker:dev`
    
    Initially it will create image: download and setup layers for NodeJS, Strapi, Mongo and Gatsby, and startup containers. Further runnings will only startup containers.

1.  To shut down environment just type `docker-compose down` or `npm run docker:down`
    
## 🧐 What's next?

Setup your local [Strapi](https://localhost:1337/admin) :

1. Make an initial Strapi installation
1. In **Content Type Builder** create entity with desirable schema
1. Create content for previously created entity in created **Content Type**
1. Go to the **Roles & Permissions** section and edit roles `Authenticated` and `Public` to grant access to CRUD operations. At least `find` and `findOne` for fetching. Instead you will always getting 403 Forbidden error.
1. Define entities in Gatsby `gatsby-config.js`. Add `contentTypes: ['pages'],` to allow gatsby prefetch needed data and describe GraphQL model.
1. Try out result in browser, ex.: `localhost:1337/pages` if you create Page content type.

- Go to the [Grap*i*hQL](http://localhost:8000/__graphql) editor and try out queries. Example:
```
{
  allStrapiPages {
    edges {
      node {
        id,
        route
      }
    }
  }
}
```

























# [Strapi](https://github.com/strapi/strapi) containerized


![Strapi](https://cldup.com/7umchwdUBh.png)

API creation made simple, secure and fast.
The most advanced open-source Content Management Framework to build powerful API with no effort.

***

[![Travis](https://img.shields.io/travis/strapi/strapi-docker.svg?style=for-the-badge)](https://travis-ci.org/strapi/strapi-docker)
[![GitHub release](https://img.shields.io/github/release/strapi/strapi-docker.svg?style=for-the-badge)](https://github.com/strapi/strapi-docker/releases)
[![Docker Pulls](https://img.shields.io/docker/pulls/strapi/strapi.svg?style=for-the-badge)](https://hub.docker.com/r/strapi/strapi)

## Quickstart (recommended)

> [Read the Medium post to have full explaination](https://medium.com/@lucaperret/strapi-quickstart-with-docker-d77ca7c86c1f)

1. `git clone https://github.com/strapi/strapi-docker && cd strapi-docker`
2. Run using `docker-compose up`

## Pull from Docker Hub

```bash
docker pull strapi/strapi
```

### Then run image

Start a database (e.g. MongoDB)

```bash
docker run -e MONGO_INITDB_DATABASE=strapi \
           -v `pwd`/db/:/data/db \
           --name strapi-mongo \
           -d mongo
```

Start strapi

```bash
docker run -e APP_NAME=strapi-project \
           -e DATABASE_CLIENT=mongo \
           -e DATABASE_HOST=strapi-mongo \
           -e DATABASE_PORT=27017 \
           -e DATABASE_NAME=strapi \
           -v `pwd`/strapi-project:/usr/src/api/strapi-project \
           --link strapi-mongo:mongo \
           -p 1337:1337 \
           --name strapi -d strapi/strapi
```

You should the be able to access your Strapi installation at [localhost:1337](http://localhost:1337).

## Use as base image

```Dockerfile
FROM strapi/strapi
```

## Environment variables

- `APP_NAME` to override the `strapi-project` generated folder name (you should also update the volumes paths).
- `DATABASE_CLIENT` a database providers supported by Strapi: MongoDB, Postgres, MySQL, Sqlite3 and Redis.
- `DATABASE_HOST` database service name.
- `DATABASE_PORT` depends on your database client.
- `DATABASE_NAME` initializes a database with specific name (default strapi). When using MongoDB, you should also update the `MONGO_INITDB_DATABASE` environment in the db service.
- `DATABASE_USERNAME` set the username of the database connection.
- `DATABASE_PASSWORD` set the password of the database connection.
- `DATABASE_SRV` boolean for SRV.
- `DATABASE_SSL` boolean for SSL.
- `DATABASE_AUTHENTICATION_DATABASE` set the authentification.
