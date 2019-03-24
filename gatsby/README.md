# Gatsby Wordpress Docker 🐳 example 

## 🚀 Quick start

1.  Install Docker

1.  **Start developing.**

    Just startup all your environment with one of this commands

    `docker-compose -f docker-compose.yaml -f docker-compose.dev.yaml up` or `npm run docker:dev`
    
    Initially it will create image: download and setup layers for NodeJS, Wordpress, MySQL and Gatsby, and startup containers. Further runnings will only startup containers.

1.  To shut down environment just type `docker-compose down` or `npm run docker:down`
    
## 🧐 What's next?

Setup your local [Wordpress](https://localhost:8080/) :

1. Make an initial installation
1. Enable Wordpress plugins ( ACF to REST API, Advanced Custom Fields, Custom Post Type UI, WP REST API Menus )
1. Setup `pretty permalinks` **Settings** => **Permalinks** => choose '**Post name**' and save.
1. Setup Site Address (URL) to allow Gatsby properly fetch data inside of Docker: **Settings** => **Site Address (URL)** and change to `http://wordpress` (this is name of our wordpress docker container) and save.

Restart Gatsby container manually or stop/start everything to make Gatsby properly initialized

- Go to the [Grap*i*hQL](http://localhost:8000/__graphql) editor and try out queries:
```
{
  allWordpressPost {
    edges {
      node {
        id
        slug
        title
        content
        excerpt
        date
        modified
      }
    }
  }
}
```

- Try out [Gatsby Site](http://localhost:8000)

## Addtinional Info

After wordpress setup in `wordpress/engine` folder will be content that bind directly to wordpress container. You can easily modify it locally.

**!!!** Note that `wordpress/plugins_for_setup` used to copy initial plugins for setup. Don't use this folder after wordpress initialization.

## 🎓 Useful Links

Looking for more guidance? Full documentation for Gatsby lives [on the website](https://www.gatsbyjs.org/). Here are some places to start:

- **For most developers, we recommend starting with our [in-depth tutorial for creating a site with Gatsby](https://www.gatsbyjs.org/tutorial/).** It starts with zero assumptions about your level of ability and walks through every step of the process.

- **To dive straight into code samples, head [Gatsby documentation](https://www.gatsbyjs.org/docs/).** In particular, check out the _Guides_, _API Reference_, and _Advanced Tutorials_ sections in the sidebar.

- **Checkout [Gatsby Source Wordpress documentation](https://www.gatsbyjs.org/docs/sourcing-from-wordpress/)**
