# Strapi Content-type

<!--- TODO: UPDATE -->

Category: NodeJS
First Source: Strapi%20Model%2056ad99ff2d67414daa39fb0664c08606.md
Tags: Concept, Low

# Types

## Collection-type

- Lưu thành 1 bảng

# Single-type

- Có 1 giá trị duy nhất

# FIles

## `schema.json`

- Định nghĩa model: fields, datatype, …
```json
{
  "kind": "collectionType",
  "collectionName": "actors", // name of content type
  "info": {
    "singularName": "actor",
    "pluralName": "actors",
    "displayName": "Actor"
  },
  "options": {
    "draftAndPublish": true
  },
  "pluginOptions": {},
  "attributes": { // fields of content type
    "first_name": {
      "type": "string"
    },
    "last_name": {
      "type": "string"
    },
    "movies": {
      "type": "relation",
      "relation": "manyToMany",
      "target": "api::movie.movie",
      "mappedBy": "actors"
    }
  }
}

```

## `lifecycles.js`

- Vòng đời của 1 model
- Để khi 1 entry có vấn đề thì sẽ call những thằng khác
- File này phải tự tạo = code