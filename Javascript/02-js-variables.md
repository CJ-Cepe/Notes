# 🌌 Variables
## ☄️ Core
+ Variable/s is/are
	+ a _named container_ for a value 
	+ label and store data in memory
	+ also referred as _bindings_ & Identifiers
+ Variables can hold two types of data: _primitive_ & _reference_ values
+ Each variable points to a particular value
	+ We can change which value it points to by using the = assignment operator.

## ☄️ Syntax
```JS
	//Declaring variable
	let message;
		//Assigning value
		message = 'Hello';
	
	//Declaring & Assigning in 1 line
	let message = 'Hello!';
	
	//Declare multiple variables in one line
	let user = 'John', age = 25, message = 'Hello';
	
	//Multiline variant
		//style 1
		let user = 'John';
		let age = 25;
		let message = 'Hello';
	
		//style 2
		let user = 'John',
			age = 25,
			message = 'Hello';
			
		//style 3
		let user = 'John'
		  , age = 25
		  , message = 'Hello';
	
```
## ☄️ Mental Models
1. "Boxes with labels containing values"
	+ a “box” for data, with a uniquely-named sticker on it.
2. "Variables as tentacles"
	+ They do not _contain_ values; they _grasp_ them—two bindings can refer to the same value.
3. "Variables are wires"
	+ A variable is a wire that point to values
	+ It has two ends and a direction: it starts from a name in my _code_ and it ends pointing at some value in my universe
		+ The left side of an assignment must be a “wire”
		+ The right side of an assignment must be an expression
	+ "=" is the wire
	+ we can't pass variables to functions but instead pass the current value of a variable

## ☄️ Naming Convention
+ the name must contain only letters, digits, or the symbols `$`and `_
+ variable names CANNOT start with numbers
+ variable names CANNOT be the same as keywords/reserved words
+ variable names are case sensitive
```js
	//Valid
	let $ = 1; // declared a variable with the name "$"
	let _ = 2; // and now a variable with the name "_"
	
	//Not-valid
	let 1a; // cannot start with a digit
	let my-name; // hyphens '-' aren't allowed in the name
```

>[!TIP]
> - a variable name should have a clean, obvious meaning, describing the data that it stores.
> - make names maximally descriptive and concise
## ☄️ Declaration
+ a variable should be declared only once
+ after a binding has been defined, its name can be used as an expression
+ in old time, in non "use-strict" mode, it is technically possible to directly assign without declaration keywords. _bad practice_ -> see pragma notes
	```js
	//code 1 - no "use strict" in this example
	num = 5; // the variable "num" is created if it didn't exist
	alert(num); // 5
		
	//code 2 - with "use strict";
	num = 5; // error: num is not defined
	```
### 👾 var
- an old-school variable declaration
- declares a function-scoped variable, no block scope
	- available throughout the function body in which it is defined
	- no matter how deeply nested its definition
- allows reassignment
- tolerates redeclarations
- hoisted - can be declared below their use
	- declarations are hoisted, but assignments are not
```jsx
	function varScoping() {
	  var x = 1;
	
	  if (true) {
		var x = 2;
		console.log(x); // will print 2
	  }
	
	  console.log(x); // will print 2
	}
```
### 👾 let
+ declares a block-scoped variable
	+ only be available within the same block where it is defined
+ allows reassignment
```jsx
	function letScoping() {
	  let x = 1;
	
	  if (true) {
		let x = 2;
		console.log(x); // will print 2
	  }
	
	  console.log(x); // will print 1
	}
```
### 👾 const
- declares a constant variable
- cannot be reassigned
	- If you try to reassign a const variable, you’ll get a _TypeError_
- must be assigned a value when declared
	- If you try to declare a const variable without a value, you’ll get a _SyntaxError_
- when to use capitals for constant?
	- _capital-named_: for constant values known before execution
		- used as aliases for “hard-coded” values
	- _camelCase_: constant values that are calculated in run-time but do not change after initial assignment
```js
	const COLOR_RED = "#F00";
	const COLOR_GREEN = "#0F0";
	
	const myBirthday = '18.04.1982';
```

## ☄️ Where are Variables are stored?
+ Where variables are stored depends on the type of data they hold
	+ __Primitives__ -> stack
		+ The value of primitive types is stored directly in the stack if the variable is a local variable.
		+ For global or closure variables, the storage might vary depending on the JavaScript engine.
	+ __Non-Primitives__ (Objects, Arrays, Functions) -> heaps
		+ The _reference_ to the object is stored in the _stack_.
		- The actual _data_ (the object itself) is stored in the _heap_.

## ☄️ Garbage Collection
+ JavaScript’s garbage collector periodically clears unreferenced objects in the heap to free up memory. This process, known as garbage collection, helps maintain efficient memory usage.
## ☄️ Environment
+ Environment - The collection of bindings and their values that exist at a given time
	+ When a program starts up, this environment is not empty. It always contains bindings that are part of the language standard
	+ most of the time, it also has bindings that provide ways to interact with the surrounding system.
		+ For example, in a browser, there are functions to interact with the currently loaded website and to read mouse and keyboard input.
## ☄️ Under the Hood

> If multiple variables `a, b, c` have the same primitive value, `10`, is there only one shared instance of `10` in memory that all three variables point to, or if there are three separate instances of `10` in memory? if the latter, is it inefficient?

```js
let a = 10
let b = 10
let c = 10
```

_ANSWER_ - depends on **how JavaScript engines optimize memory usage**, which can vary between implementations.
+ some engines _may_ optimize memory by using *interning or value sharing* for common primitives, meaning multiple variables with the same value (like `10`) could point to the same underlying memory representation. This avoids unnecessary duplication.
+ this behavior is abstracted away, and JavaScript gives you no direct control or visibility into whether primitives are de-duplicated at the memory level
+ For practical purposes, you can assume that each variable holds its own copy unless you're specifically concerned with low-level optimizations.
+ Also, primitive values like 10 are immutable and often small

+ logically, each variable `a`, `b`, and `c` holds its _own copy_ of the value `10` from a language perspective.
- whether these copies share the same physical memory is an _implementation detail_ and does not affect how your code behaves.








## Scoping ?
+ Bindings and scopes
	+ Each binding has a scope, which is the part of the program in which the binding is visible.
	+ global
	+ local binding
		+ Bindings created for function parameters or declared inside a function can be referenced only in that function
		+ Every time the function is called, new instances of these bindings are created. This provides some isolation between functions—each function call acts in its own little world (its local environment) and can often be understood without knowing a lot about what’s going on in the global environment.
		+ Each scope can “look out” into the scope around it, so `x` is visible inside the block in the example. The exception is when multiple bindings have the same name—in that case, code can see only the innermost one.
	+ _lexical scoping_
		+ The set of bindings visible inside a block is determined by the place of that block in the program text. Each local scope can also see all the local scopes that contain it, and all scopes can see the global scope. This approach to binding visibility is called _lexical scoping_.
	+ Each block creates a new scope

- scope
    - _Scope_ is a concept that refers to where values and functions can be accessed.
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
        - too many global variables can cause problems in a program. When you declare global variables, they go to the _global namespace_. These variables remain there until the program finishes which means our global namespace can fill up really quickly.
        - while it’s important to know what global scope is, it’s best practice to not define variables in the global scope.
        - **Global namespace**
            - is the space in our code that contains globally scoped information.
        - _Best Practice_
            - we should follow best practices for scoping our variables as tightly as possible using block scope.
                
                1. It will make your code more legible since the blocks will organize your code into discrete sections.
                2. It makes your code more understandable since it clarifies which variables are associated with different parts of the program rather than having to keep track of them line after line!
                3. It’s easier to maintain your code, since your code will be modular.
                4. It will save memory in your code because it will cease to exist after the block finishes running.
                
                - _If a variable does not need to exist outside a block— it shouldn’t!_
    - others
        - _Global_ scope (a value/function in the global scope can be used anywhere in the entire program)
        - _File_ or _module_ scope (the value/function can only be accessed from within the file)
        - _Function_ scope (only visible within the function),
        - _Code block_ scope (only visible within a `{ ... }` codeblock)



+ semicolon ;
+ 
+ Functions
	+ A lot of the values provided in the default environment have the type _function_.
+ Expression
	+ Anything that produces a value is an expression in JavaScript
+ Console.log
	+ console.log("the value of x is", x);
+ A `return` statement determines the value the function returns. When control comes across such a statement, it immediately jumps out of the current function and gives the returned value to the code that called the function. A `return` keyword without an expression after it will cause the function to return `undefined`. Functions that don’t have a `return` statement at all, such as `makeNoise`, similarly return `undefined`.
	+ (https://eloquentjavascript.net/03_functions.html#p-tSSGXmQE8/)Parameters to a function behave like regular bindings, but their initial values are given by the _caller_ of the function, not the code in the function itself.

+ Function declarations are not part of the regular top-to-bottom flow of control. They are conceptually moved to the top of their scope and can be used by all the code in that scope. This is sometimes useful because it offers the freedom to order code in a way that seems the clearest, without worrying about having to define all functions before they are used.
+ Call Stack
	+  a function has to jump back to the place that called it when it returns, the computer must remember the context from which the call happened.
	+ The place where the computer stores this context is the _call stack_. Every time a function is called, the current context is stored on top of this stack. When a function returns, it removes the top context from the stack and uses that context to continue execution.
	+ Storing this stack requires space in the computer’s memory. When the stack grows too big, the computer will fail with a message like “out of stack space” or “too much recursion”.
+ Optional Arguments
	+ It ignores the extra arguments and computes the square of the first one.
	+ JavaScript is extremely broad-minded about the number of arguments you can pass to a function. If you pass too many, the extra ones are ignored. If you pass too few, the missing parameters are assigned the value `undefined`.
	+ The downside of this is that it is possible—likely, even—that you’ll accidentally pass the wrong number of arguments to functions. And no one will tell you about it. The upside is that you can use this behavior to allow a function to be called with different numbers of arguments
	+ If you write an `=` operator after a parameter, followed by an expression, the value of that expression will replace the argument when it is not given.
+ Closure
	+ The ability to treat functions as values, combined with the fact that local bindings are re-created every time a function is called, brings up an interesting question: What happens to local bindings when the function call that created them is no longer active?
		+  local bindings are created anew for every call, and different calls don’t affect each other’s local bindings.
	+ This feature—being able to reference a specific instance of a local binding in an enclosing scope—is called _closure_. A function that references bindings from local scopes around it is called _a_ closure. This behavior not only frees you from having to worry about the lifetimes of bindings but also makes it possible to use function values in some creative ways.
	+ A good mental model is to think of function values as containing both the code in their body and the environment in which they are created. When called, the function body sees the environment in which it was created, not the environment in which it is called.
+ Recursion
	+ A function that calls itself is called _recursive_.
	+ in typical JavaScript implementations, it’s about three times slower than a version using a `for` loop. Running through a simple loop is generally cheaper than calling a function multiple times.
	+ Recursion is not always just an inefficient alternative to looping. Some problems really are easier to solve with recursion than with loops. Most often these are problems that require exploring or processing several “branches”, each of which might branch out again into even more branches.
+ Functions and side effects
	+ . Functions that create values are easier to combine in new ways than functions that directly perform side effects.
	+ A _pure_ function is a specific kind of value-producing function that not only has no side effects but also doesn’t rely on side effects from other code—for
	+ A pure function has the pleasant property that, when called with the same arguments, it always produces the same value (and doesn’t do anything else).
	+ When you are not sure that a pure function is working correctly, you can test it by simply calling it and know that if it works in that context, it will work in any context. Nonpure functions tend to require more scaffolding to test.
+ The two main ways to access properties in JavaScript are with a dot and with square brackets. Both value.x and value[x] access a property on value—but not necessarily the same property. The difference is in how x is interpreted. When using a dot, the word after the dot is the literal name of the property. When using square brackets, the expression between the brackets is evaluated to get the property name. Whereas value.x fetches the property of value named “x”, value[x] takes the value of the variable named x and uses that, converted to a string, as the property name.