# Strapi Controller

Category: NodeJS
First Source: Strapi%20v4%206f146e68c45f42a39ec13d4b2f6d3214.md
Tags: Concept, Medium

# Controller

<aside>
💡 Viết các hàm handler cho route
</aside>

- Controllers are JavaScript files that contain a set of methods, called actions, reached by the client according to the requested [Strapi Route](Strapi%20Route%209ede7977abb447cfb4074b4a8616e573.md)
- Các core route của model có sẵn controller mà không có file

```jsx
// path: ./src/api/restaurant/controllers/restaurant.js

const { createCoreController } = require('@strapi/strapi').factories;

module.exports = createCoreController('api::restaurant.restaurant', ({ strapi }) => ({
  // Method 1: Creating an entirely custom action
  async exampleAction(ctx) {
    try {
      ctx.body = 'ok';
    } catch (err) {
      ctx.body = err;
    }
  },

  // Method 2: Wrapping a core action (leaves core logic in place)
  async find(ctx) {
    // some custom logic here
    ctx.query = { ...ctx.query, local: 'en' };

    // Calling the default core action
    const { data, meta } = await super.find(ctx);

    // some more custom logic
    meta.date = Date.now();

    return { data, meta };
  },

  // Method 3: Replacing a core action
  async findOne(ctx) {
    const { id } = ctx.params;
    const { query } = ctx;

    const entity = await strapi.service('api::restaurant.restaurant').findOne(id, query);
    const sanitizedEntity = await this.sanitizeOutput(entity, ctx);

    return this.transformResponse(sanitizedEntity);
  },
}));
```

# Services

- Services are a set of reusable functions
- Code tương tự `controller`


```jsx
// path: ./src/api/restaurant/services/restaurant.js

const { createCoreService } = require('@strapi/strapi').factories;

module.exports = createCoreService('api::restaurant.restaurant', ({ strapi }) =>  ({
  // Method 1: Creating an entirely new custom service
  async exampleService(...args) {
    let response = { okay: true }

    if (response.okay === false) {
      return { response, error: true }
    }

    return response
  },

  // Method 2: Wrapping a core service (leaves core logic in place)
  async find(...args) {  
    // Calling the default core controller
    const { results, pagination } = await super.find(...args);

    // some custom logic
    results.forEach(result => {
      result.counter = 1;
    });

    return { results, pagination };
  },

  // Method 3: Replacing a core service
  async findOne(entityId, params = {}) {
    return strapi.entityService.findOne('api::restaurant.restaurant', entityId, this.getFetchParams(params));
  }
}));
```

---

[Backend customization - Controllers - Strapi Developer Docs](https://docs.strapi.io/developer-docs/latest/development/backend-customization/controllers.html)
[Backend customization - Services - Strapi Developer Docs](https://docs.strapi.io/developer-docs/latest/development/backend-customization/services.html)