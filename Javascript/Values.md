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
- In JavaScript they are written like this:
	- Greater/less than: `a > b`, `a < b`.
	- Greater/less than or equals: `a >= b`, `a <= b`.
	- Equals: `a == b`, please note the double equality sign `==` means the equality test, while a single one `a = b` means an assignment.
	- Not equals: In maths the notation is `≠`, but in JavaScript it’s written as `a != b`.
	
	In this article we’ll learn more about different types of comparisons, how JavaScript makes them, including important peculiarities.
	
	At the end you’ll find a good recipe to avoid “JavaScript quirks”-related issues.
	
	## [Boolean is the result](https://javascript.info/comparison#boolean-is-the-result)
	
	All comparison operators return a boolean value:
	
	- `true` – means “yes”, “correct” or “the truth”.
	- `false` – means “no”, “wrong” or “not the truth”.