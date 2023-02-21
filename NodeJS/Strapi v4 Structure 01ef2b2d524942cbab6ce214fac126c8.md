# Strapi v4 Structure

Category: NodeJS
First Source: Strapi%20v4%206f146e68c45f42a39ec13d4b2f6d3214.md
Tags: Concept, Medium

# `/.cache`

- Contains files used to build your admin panel

# `/build`

- build of the admin panel

# `/config`

## `api.js`

## `admin.js`

[Admin panel configuration - Strapi Developer Docs](https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/configurations/required/admin-panel.html)

## `cron-tasks.js`

## `database.js`

[Database configuration - Strapi Developer Docs](https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/configurations/required/databases.html)

## `middlewares.js`

[Middlewares configuration - Strapi Developer Docs](https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/configurations/required/middlewares.html#loading-order)

## `plugins.js`

## `server.js`

[Server configuration - Strapi Developer Docs](https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/configurations/required/server.html)

# `database`

## `migrations`

# `/public`

- files accessible to the outside world

## `uploads`

# `/src`

## **`/admin`**

- *(optional)*
- Contains your admin customization files.

### **`extensions`**

- Files to extend the admin panel

### `app.js`

### `webpack.config.js`

## `/api`

<aside>
💡 Contains the business logic of your project split into sub-folders per API.

</aside>

### `content-types`

<aside>
💡 Each `content-type` is a subfolders

</aside>

[Strapi Content-type](Strapi%20Content-type%206df2f7d8bd6a45218679e9c90d5177e2.md) 

- `lifecycles.js`
- `schema.json`

### `controllers`

[Strapi Controller](Strapi%20Controller%2075e8e18e575041fa95e9b7f4da7d45bc.md) 

### `middlewares`

### `policies`

### `routes`

[Strapi Route](Strapi%20Route%209ede7977abb447cfb4074b4a8616e573.md) 

### `services`

### `index.js`

## `components`

<aside>
💡 Each `category` is a subfolders

</aside>

- Each component is a JSON file

## `extensions`

- Files to extend installed plugins
- Lưu những plugin tải trên market

<aside>
💡 Each `extention` is a subfolders

</aside>

- `content-types`
    - (content-type-name)
        - `schema.json`
- `strapi-server.js`

## `middlewares`

- Global middleware
- `(middleware-name).j`

## `plugins`

- Local plugins files
- Mỗi plugins có thể là 1 project độc lập

`(plugin-name)`

- admin
    - src
        - index.js
- server
    - content-types
    - controllers
    - policies
- package.json
- strapi-admin.js
- strapi-server.js

# `.env`

# `package.json`