# URL in Javascript

Category: Javascript
First Refrence: How%20do%20you%20decode%20or%20encode%20a%20URL%20in%20JavaScript%2022455304a77d41918fe6dbc501c9c12e.md
Tags: Concept, Low

## `encodeURI` & `decodeURI`

- `encodeURI()` function is used to encode an URL.
    - This function requires a URL string as a parameter and return that encoded string.
- `decodeURI()`function is used to decode an URL.
    - This function requires an encoded URL string as parameter and return that decoded string.

```jsx
let uri = "employeeDetails?name=john&occupation=manager";
let encoded_uri = encodeURI(uri);
let decoded_uri = decodeURI(encoded_uri);
```

---

# **URLSearchParams**

- The **`URLSearchParams`** interface defines utility methods to work with the query string of a URL.
- An object implementing `URLSearchParams` can directly be used in a `for...of` structure to iterate over key/value pairs.

```jsx
for (const [key, value] of mySearchParams) {}
for (const [key, value] of mySearchParams.entries()) {}
```

## Constructor

```jsx
const paramsString = 'q=URLUtils.searchParams&topic=api';
const searchParams = new URLSearchParams(paramsString);
```

- **`URLSearchParams`** chỉ nhận được `paramsString` mà không nhận cả URL

## Methods

### `URLSearchParams.append()`

- Appends a specified key/value pair as a new search parameter.

### `URLSearchParams.delete()`

- Deletes the given search parameter, and its associated value, from the list of all search parameters.

URLSearchParams.entries()
Returns an iterator allowing iteration through all key/value pairs contained in this object in the same order as they appear in the query string.

URLSearchParams.forEach()
Allows iteration through all values contained in this object via a callback function.

URLSearchParams.get()
Returns the first value associated with the given search parameter.

URLSearchParams.getAll()
Returns all the values associated with a given search parameter.

URLSearchParams.has()
Returns a boolean value indicating if such a given parameter exists.

URLSearchParams.keys()
Returns an iterator allowing iteration through all keys of the key/value pairs contained in this object.

URLSearchParams.set()
Sets the value associated with a given search parameter to the given value. If there are several values, the others are deleted.

URLSearchParams.sort()
Sorts all key/value pairs, if any, by their keys.

URLSearchParams.toString()
Returns a string containing a query string suitable for use in a URL.

URLSearchParams.values()
Returns an iterator allowing iteration through all values of the key/value pairs contained in this object.