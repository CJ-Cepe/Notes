Very generally speaking, values are the _entities_ existing in JavaScript.

There are two **categories** of values, each with various **types**:

- Category 1: **Primitive values**
    - String, for text → e.g. `"john"`
    - Number, for calculations → e.g. `7` and `3.14`
    - Boolean, for logical operations → only `true` and `false`
    - Null, for intentionally missing values → only `null`
    - Undefined, for unintentionally missing values → only `undefined`
- Category 2: **Special values**
    - Object, for key-value pair mappings, e.g. `{ name: "john", score: 20 }`
        - Array, e.g. `[1, 2, 3]`
        - Function, for bundles of functionality, e.g. `(x) => x * 2;`
        - Date, e.g. `Sat Jul 04 2020 19:15:32 GMT-0300`
        - Regex, e.g. `/\s+/`
        - etc.