# [Gatsby](https://www.gatsbyjs.org/) [Strapi](https://github.com/strapi/strapi) [Docker](https://www.docker.com/) 🐳 example 

## 🚀 Quick start

1.  Install Docker

1.  **Start developing.**

    Just startup all your environment with one of this commands

    `docker-compose -f docker-compose.yml -f docker-compose.dev.yml up` or `npm run docker:dev`
    
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
1. Since we edit gatsbe config - better to rebuild image `docker-compose build` and run project again `npm run docker:dev` or with full command as described in quick start.

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
