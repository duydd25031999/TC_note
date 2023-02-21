# Strapi Route

Category: NodeJS
First Source: Strapi%20v4%206f146e68c45f42a39ec13d4b2f6d3214.md
Tags: Concept, Low

- Đăng kí Api Router với Controller function
- Mỗi content-type được đăng kí default các route theo chuẩn RESTful (find, findOne, create, update, delete)

# createCoreRouter

<aside>
💡 Setting core routers

</aside>

```jsx
// path: ./src/api/[apiName]/routes/[routerName].js (e.g './src/api/restaurant/routes/restaurant.js')

const { createCoreRouter } = require('@strapi/strapi').factories;

module.exports = createCoreRouter('api::apiName.contentType', {
  prefix: '',
  only: ['find', 'findOne'],
  except: [],
  config: {
    find: {
      auth: false,
      policies: [],
      middlewares: [],
    },
    findOne: {},
    create: {},
    update: {},
    delete: {},
  },
});
```

# Custom router

- Nên tạo 1 file custom router riêng

```jsx
module.exports = {
  routes: [
    { // Path defined with an URL parameter
      method: 'POST',
      path: '/restaurants/:id/review', 
      handler: 'restaurant.review',
    },
    { // Path defined with a regular expression
      method: 'GET',
      path: '/restaurants/:category([a-z]+)', // Only match when the URL parameter is composed of lowercase letters
      handler: 'restaurant.findByCategory',
    }
  ]
}
```

## method

- Method associated to the route (i.e. GET, POST, PUT, DELETE or PATCH)
- String

## path

- Path to reach, starting with a forward-leading slash (e.g. /articles)
- String

## handler

- Function to execute when the route is reached.
- Should follow this syntax: `<controllerName>.<actionName>`
- String

## config

- Optional
- Configuration to handle policies, middlewares and public availability for the route
- Object