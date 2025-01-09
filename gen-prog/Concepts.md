
# General Programming Terms
---
__Variable__
: A named storage location used to hold a value that can change during program execution.
__Expression__
: A combination of values, variables, and operators that evaluates to a single value.
__Equality__
: A comparison operator that checks if two values are equal.
__Statement__
: A single instruction that performs a specific action.
__Code Block__
: A group of statements enclosed within curly braces {}, often executed together.
And for the second set:

---
__Parameter__
: A variable defined in a function's signature to receive values passed to the function.
__Argument__
: A value passed to a function when it's called, corresponding to a parameter in the function's definition.

---

---
Instances
: 

___
String
:
String Concatenation
:
String Interpolation
:
Template Literal
:

---
Control Flow
Truthy Values
Falsy Values
return
scope
Type Coercion
Comparison of different types
Short Circuting



- Functions vs Methods
    - Functions that are part of objects are called methods.
- parameter vs argument
- Initialization, Definition, and Declaration
    - Declaration *(introducing identifier)*
        - Introduces a new identifier (name) into the program and specifies its type
        - Declaration does not allocate memory for the identifier
            - but only tells the compiler or interpreter that it exists and how to use it correctly
            
            ```java
            int x; //declares a variable named x of type int
            ```
            
    - Definition *(allocating memory)*
        - Definition of a previously declared name (or it can be both definition and declaration)
        - Is a statement that allocates memory for the identifier and assigns it a value
            
            ```java
            x = 10; //defines the variable x and gives it the value 10
            ```
            
        - Definition can be done separately from declaration, or at the same time
            
            ```java
            int x = 10; //is both a declaration and a definition
            ```
            
    - Initialization (*assigning of first value*)
        - Refers to the "assignment" of a value, at construction time
        - a special type of definition that assigns the first value to the identifier at the time of declaration
            
            ```java
            int x = 10; //is also an initialization, because it gives x its initial value of 10
            ```
            
        - Initialization is usually preferred over separate declaration and definition, because it ensures that the identifier has a valid value before it is used
    - Assigning
- parameter vs argument
    - default parameter
- expression
    - When a new piece of data is introduced into a JavaScript program, the program keeps track of it in an instance of that data type. An instance is an individual case of a data type.
    - instance - an example or single occurrence of something.
- statement
- code block
- instances
- **String Interpolation** (process)
    - interpolate - the insertion of something of a different nature into something else.
    - is the process of evaluating string literals containing one or more placeholders (expressions, variables, etc).
    - can be performed using template literal
        
        ```jsx
        let age = 7;
        
        // String concatenation
        'Tommy is ' + age + ' years old.';
        
        // String interpolation
        `Tommy is ${age} years old.`;
        ```
        
- Template Literal (type of string)
    - strings that allow embedded expressions, ${expression}. While regular strings use single ' or double " quotes, template literals use backticks instead.
- String Concatenation
    - multiple strings can be concatenated together using the + operator
    - concatenate - link (things) together in a chain or series.
- Control Flow
    - flow/order of statement execution
    - default - left to right, top to bottom
- Truthy values
    - evaluate to true when checked as a condition
    - Values that evaluate to true are known as truthy
- Falsy values
    - evaluate to false when checked as a condition
    - Values that evaluate to false are known as falsy
    - falsy values
        - false
        - 0
        - Empty strings like "" or ''
        - null which represent when there is no value at all
        - undefined which represent when a declared variable lacks a value
        - NaN, or Not a Number
- return
    - `return` ends function execution and returns the specified value to the location where it was called. A common mistake is to forget the `return` keyword, in which case the function will return `undefined` by default.
- scope
    - *Scope* is a concept that refers to where values and functions can be accessed.
    - Scope defines where variables can be accessed or referenced
    - where variables can be accessed throughout the program, and is determined by where and how they are declared
    - Global Scope
        - variables are declared outside of blocks.
        - accessible to every part of the program, including code in blocks.
        - These variables are called **global variables**
            - are variables that exist within global scope
    - Block Scope (Local Scope)
        - When a variable is defined inside a block, it is only accessible to the code within the curly braces {}
        - Refers to the context within which variables are accessible only within the block they are defined.
        - known as **local variables**
            - are variables that exist within block scope.
    - Scope Pollution
        - too many global variables that exist in the global namespace, or when we reuse variables across different scopes
            - difficult to keep track of our different variables and sets us up for potential accidents.
        - too many global variables can cause problems in a program. When you declare global variables, they go to the *global namespace*. These variables remain there until the program finishes which means our global namespace can fill up really quickly.
        - while it’s important to know what global scope is, it’s best practice to not define variables in the global scope.
        - **Global namespace**
            - is the space in our code that contains globally scoped information.
        - *Best Practice*
            - we should follow best practices for scoping our variables as tightly as possible using block scope.
                1. It will make your code more legible since the blocks will organize your code into discrete sections.
                2. It makes your code more understandable since it clarifies which variables are associated with different parts of the program rather than having to keep track of them line after line!
                3. It’s easier to maintain your code, since your code will be modular.
                4. It will save memory in your code because it will cease to exist after the block finishes running.
                - *If a variable does not need to exist outside a block— it shouldn’t!*
    - others
        - *Global* scope (a value/function in the global scope can be used anywhere in the entire program)
        - *File* or *module* scope (the value/function can only be accessed from within the file)
        - *Function* scope (only visible within the function),
        - *Code block* scope (only visible within a `{ ... }` codeblock)
- Type Coercion
    - *Type Coercion* means that two values are compared only after attempting to convert them into a common type.
- Comparison of different types
    - Comparison operators return a boolean value.
    - When values of different types are compared, they get converted to numbers (with the exclusion of a strict equality check).
        
        ```jsx
        alert( '2' > 1 ); // true, string '2' becomes a number 2
        alert( '01' == 1 ); // true, string '01' becomes a number 1
        ```
        
- Nesting
- Truty and Falsy
    - Any value that is not false, undefined, null, 0, NaN, or an empty string ('') actually returns true when tested as a conditional statement, therefore you can use a variable name on its own to test whether it is true, or even that it exists
- mutable
- delete
    - Once an object is created in JavaScript, it is possible to remove properties from the object using the `delete` operator. The `delete` keyword deletes both the value of the property and the property itself from the object. The `delete` operator only works on properties, not on variables or functions.
- Hoisting
    - allows access to function declarations before they’re defined.
    - hoisting isn’t considered good practice, we simply want you to be aware of this feature.
- Call Stack
    - A call stack is a way for the JavaScript engine to keep track of its place in code that calls multiple functions. It has the information on what function is currently being run and what functions are invoked from within that function
    - Also, the JavaScript engine uses a call stack to manage execution contexts:
        - Global execution context
        - function execution contexts
    - based on the LIFO principle i.e., last-in-first-out.
    1. When you execute a script, the JavaScript engine creates a global execution context and pushes it on top of the call stack.
    2. Whenever a function is called, the JavaScript engine creates a function execution context for the function, pushes it on top of the call stack, and starts executing the function.
    3. If a function calls another function, the JavaScript engine creates a new function execution context for the function being called and pushes it on top of the call stack.
    4. When the current function completes, the JavaScript engine pops it off the call stack and resumes the execution where it left off.
    5. The script will stop when the call stack is empty
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f1ef83b9-d771-4525-89e6-b9204fc2af55/Untitled.png)
    
- Stack overflow
    - The call stack has a fixed size, depending on the implementation of the host environment, either the web browser or Node.js.
    - If the number of execution contexts exceeds the size of the stack, a stack overflow error will occur.
    - For example, when you execute a recursive function that has no exit condition, the JavaScript engine will issue a stack overflow error
- **Asynchronous JavaScript**
    - JavaScript is a single-threaded programming language. This means that the JavaScript engine has only one call stack. Therefore, it only can do one thing at a time.
    - When executing a script, the JavaScript engine executes code from top to bottom, line by line. In other words, it is **synchronous**.
    - Asynchronous means the JavaScript engine can execute other tasks while waiting for another task to be completed.
        - To do this, the JavaScript engine uses an **event loop**
- Refactor
    - Refactoring is the process of restructuring code, while not changing its original functionality.
    - The goal of refactoring is to improve internal code by making many small changes without altering the code's external behavior.
- Parse
- Test Driven Development (TDD)
    - refers to the practice of writing automated tests that describe how your code should work before you actually write the code.
- Integer properties
    - The “integer property” term here means a string that can be converted to-and-from an integer without a change.
    - So, "49" is an integer property name, because when it’s transformed to an integer number and back, it’s still the same.
        
        ```jsx
        // Number(...) explicitly converts to a number
        // Math.trunc is a built-in function that removes the decimal part
        alert( String(Math.trunc(Number("49"))) ); // "49", same, integer property
        alert( String(Math.trunc(Number("+49"))) ); // "49", not same "+49" ⇒ not integer property
        alert( String(Math.trunc(Number("1.2"))) ); // "1", not same "1.2" ⇒ not integer property
        ```
        
- static vs dynamic websites
    - static
        - not generated dynamically
- short-circuiting
    - ||
    - &&
- Invoke
