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
+ **ECMAScript** - is a standard.
	+ **JavaScript** is the most popular _implementation_ of that standard. Other implementations include: [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey), [V8](https://en.wikipedia.org/wiki/Chrome_V8), and [ActionScript](https://en.wikipedia.org/wiki/ActionScript).
	+ [The ECMA-262 specification](https://www.ecma-international.org/publications/standards/Ecma-262.htm) contains the most in-depth, detailed and formalized information about JavaScript
+ Manual
	+ [MDN JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference) is the main manual with examples and other information.
+ Compatibility tables
	+ https://caniuse.com – per-feature tables of support



### Why is it called JavaScript

## Mental Model

## Security/Limitation (to fill)
+ JavaScript’s abilities in the browser are limited to protect the user’s safety.
+ JavaScript’s capabilities greatly depend on the environment it’s running in.
+ Same Origin Policy



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
**JavaScript Functions: A Comprehensive Guide**

**What is a Function?** A function is a block of reusable code designed to perform a specific task. It takes input values, processes them, and returns an output value.

**Syntax:**

JavaScript

```
function functionName(parameter1, parameter2, ...) {
  // Function body
  return value; // Optional return statement
}
```

Use code [with caution.](/faq#coding)

**Key Components:**

1. **Function Name:** A unique identifier to call the function.
2. **Parameters:** Variables defined within the parentheses to receive input values.
3. **Function Body:** The code block that executes when the function is called.
4. **Return Statement:** Optionally returns a value from the function.

**Calling a Function:** To execute a function, you use its name followed by parentheses:

JavaScript

```
functionName(argument1, argument2, ...);
```

Use code [with caution.](/faq#coding)

- **Arguments:** The values passed to the function when it's called.

**Example:**

JavaScript

```
function greet(name) {
  console.log("Hello, " + name + "!");
}

greet("Alice"); // Output: Hello, Alice!
```

Use code [with caution.](/faq#coding)

**Types of Functions:**

1. **Named Functions:**
    - Defined with a specific name.
    - Can be called from anywhere within the script.
2. **Anonymous Functions:**
    - Defined without a name.
    - Often used as arguments to other functions or assigned to variables.
3. **Arrow Functions:**
    - A concise syntax for defining anonymous functions.
    - Useful for short, simple functions.

**Example:**

JavaScript

```
// Named Function
function square(x) {
  return x * x;
}

// Anonymous Function
let cube = function(x) {
  return x * x * x;
};

// Arrow Function
let multiply = (x, y) => x * y;
```

Use code [with caution.](/faq#coding)

**Function Scope:**

- Variables declared within a function are local to that function.
- Variables declared outside a function are global.

**Return Statement:**

- The `return` statement exits a function and optionally returns a value.
- If no `return` statement is present, the function implicitly returns `undefined`.

**Function Expressions:**

- Functions can be assigned to variables:

JavaScript

```
let add = function(x, y) {
  return x + y;
};
```

Use code [with caution.](/faq#coding)

**IIFE (Immediately Invoked Function Expression):**

- An anonymous function that is executed immediately after being defined:

JavaScript

```
(function() {
  console.log("This function runs immediately.");
})();
```

Use code [with caution.](/faq#coding)

**Recursive Functions:**

- Functions that call themselves directly or indirectly.
- Used to solve problems that can be broken down into smaller, similar subproblems.

**Key Points to Remember:**

- Functions promote code reusability.
- They help organize code into smaller, manageable parts.
- Functions can take input parameters and return output values.
- Understand function scope and variable accessibility.
- Use arrow functions for concise syntax.
- Explore recursive functions for solving specific problems.

**Object-Oriented Programming (OOP)**

**Core Concepts:**

1. **Objects:**
    
    - Instances of classes that represent real-world entities.
    - Composed of properties (data) and methods (functions).
    - Example:
        
        JavaScript
        
        ```
        const person = {
            firstName: "Alice",
            lastName: "Johnson",
            age: 30,
            greet: function() {
                console.log("Hello, my name is " + this.firstName + " " + this.lastName);
            }
        };
        ```
        
        Use code [with caution.](/faq#coding)
        
2. **Classes:**
    
    - Blueprints for creating objects.
    - Define the properties and methods that objects of that class will have.
    - Example:
        
        JavaScript
        
        ```
        class Person {
            constructor(firstName, lastName, age) {
                this.firstName = firstName;
                this.lastName = lastName;
                this.age = age;
            }
        
            greet() {
                console.log("Hello, my name is " + this.firstName + " " + this.lastName);      
            }
        }
        
        const person1 = new Person("Bob", "Smith", 25);
        ```
        
        Use code [with caution.](/faq#coding)
        
3. **Inheritance:**
    
    - The ability to create new classes based on existing ones.
    - Child classes inherit properties and methods from parent classes.
    - Example:
        
        JavaScript
        
        ```
        class Student extends Person {
            constructor(firstName, lastName, age, grade) {
                super(firstName, lastName, age);
                this.grade = grade;
            }
        
            study() {
                console.log("Studying    hard!");
            }
        }
        ```
        
        Use code [with caution.](/faq#coding)
        
4. **Polymorphism:**
    
    - The ability of objects of different types to be treated as if they were of the same type.
    - Achieved through method overriding and interfaces.
5. **Encapsulation:**
    
    - The practice of bundling data and methods that operate on that data within a single unit (an object or a class).
    - Protects data integrity by controlling access to it.

**Key Points:**

- JavaScript is a prototype-based language, not a class-based language.
- Classes are syntactic sugar introduced in ES6 to make OOP concepts easier to understand and implement.
- `this` keyword refers to the current object.
- Constructors are special methods used to initialize objects.
- Use `super()` to call the parent class's constructor.
- Inheritance allows code reuse and creates hierarchical relationships between classes.
- Polymorphism enables flexible and extensible code.
- Encapsulation promotes modularity and data security.

**Best Practices:**

- Use clear and concise naming conventions.
- Keep classes and methods focused on specific tasks.
- Favor composition over inheritance when possible.
- Use object-oriented principles to structure your code effectively.
- Test your code thoroughly to ensure correctness and reliability.

> References
> - https://javascript.info/
> - https://www.theodinproject.com/
