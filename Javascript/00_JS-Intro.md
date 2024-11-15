# JS-Introduction
---
## What is JS
+ a programming language.
> 	Single Treaded (one-at-a-time) event loop queue that drives all "events" (async function invocations). non-blocking in nature.
+ a core tech (alongside HTML and CSS), that makes web run.
+ a “safe” programming language. 
	+ It does not provide low-level access to memory or the CPU, because it was initially created for browsers which do not require it.
	+ limited to protect the user’s safety.
+ LiveScript - initial name
	+ changed to JavaScript to leverage Java’s popularity
	+ positioned as a “younger brother” to Java
	+ now it has no relation to Java at all
+ __Scripts__ - program in JS
	+ run automatically as page loads
	+ executed as plain text
	+ don't need special preparation/compilation to run
+ Engine - JS runs in any device with JS engine
	+ JavaScript virtual machine - browsers have an embedded engine


### ECMAScript
+ **ECMAScript** - is a standard. 
	+ **JavaScript** is the most popular _implementation_ of that standard. Other implementations include: [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey), [V8](https://en.wikipedia.org/wiki/Chrome_V8), and [ActionScript](https://en.wikipedia.org/wiki/ActionScript).
	+ [The ECMA-262 specification](https://www.ecma-international.org/publications/standards/Ecma-262.htm) contains the most in-depth, detailed and formalized information about JavaScript
+ Manual - 
	+ [MDN JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference) is the main manual with examples and other information.
+ Compatibility tables 
	+ https://caniuse.com – per-feature tables of support



### Why is it called JavaScript

## Mental Model


## Security/Limitation (to fill)
+ JavaScript’s abilities in the browser are limited to protect the user’s safety.
+ JavaScript’s capabilities greatly depend on the environment it’s running in.
+ Same Origin Policy

- **IDE (Integrated Development Environment)**: Full-featured software with tools like debugging, code suggestions, and project management, all-in-one.
- **Lightweight Editor**: Simple and fast code editor focused on editing text, with fewer built-in tools, but often customizable with extensions.


That had the benefit of never breaking existing code. But the downside was that any mistake or an imperfect decision made by JavaScript’s creators got stuck in the language forever.

This was the case until 2009 when ECMAScript 5 (ES5) appeared. It added new features to the language and modified some of the existing ones. To keep the old code working, most such modifications are off by default. You need to explicitly enable them with a special directive: `"use strict"`

- **Number**: Numeric values (e.g., `42`, `3.14`).
- **String**: Text data (e.g., `"Hello"`).
- **Boolean**: `true` or `false`.
- **Undefined**: Variable declared but not assigned a value.
- **Null**: Represents no value.
- **Object**: Collection of key-value pairs.
- **Symbol**: Unique and immutable identifier.
- **BigInt**: For numbers larger than `Number` can handle.

**JavaScript Variables - Objects and Primitives**

In JavaScript, variables can hold two main types of values: objects and primitives.

**Primitives**

Primitives are simple, immutable values. They are stored directly in memory as single units. Here are the primitive data types in JavaScript:

- **Numbers:** Represent numeric values (integers, floats).
    - Examples: `1`, `3.14`, `-10`
- **Strings:** Represent sequences of characters.
    - Examples: 'hello', 'JavaScript', 'true'
- **Booleans:** Represent true or false values.
    - Examples: `true`, `false`
- **Null:** Represents the absence of a value.
    - Example: `null`
- **Undefined:** Represents a variable that has not been assigned a value.
    - Example: `let x;`

**Objects**

Objects are complex data types that store properties (key-value pairs). They are stored as references to memory locations. Here are some key characteristics of objects:

- **Mutable:** Objects can be modified after they are created.
- **Properties:** Properties can be accessed using dot notation (`object.property`) or bracket notation (`object['property']`).
- **Methods:** Functions defined within an object are called methods.

**Examples of Objects**

- **Arrays:** Ordered collections of values.
    - Example: `let fruits = ['apple', 'banana', 'orange'];`
- **Functions:** Blocks of code that can be executed.
    - Example: `function sayHello() { console.log('Hello'); }`
- **Dates:** Represent points in time.
    - Example: `let today = new Date();`

**Important Considerations**

- **Primitive Equality:** Primitive values are compared by their value.
- **Object Equality:** Objects are compared by their reference. Two objects are only equal if they refer to the same object in memory.
- **Pass by Value:** Primitives are passed by value. When a primitive is passed to a function, a copy of the value is made.
- **Pass by Reference:** Objects are passed by reference. When an object is passed to a function, a reference to the object is passed.

**Common Pitfalls**

- **Confusing primitives and objects:** It's important to understand the difference between primitives and objects to avoid common errors.
- **Modifying objects passed as arguments:** Since objects are passed by reference, modifying an object passed to a function will affect the original object.
- **Using `==` instead of `===`:** The `==` operator performs type coercion, which can lead to unexpected results. It's recommended to always use the strict equality operator (`===`) to compare values.

> References
> - https://javascript.info/
> - https://www.theodinproject.com/
