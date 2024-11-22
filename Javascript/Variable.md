# Variables
## Core
+ a _named container_ for a value. Variables label and store data in memory
+ variables are not values; they contain values and represent them with a name
+ after a binding has been defined, its name can be used as an expression
+ variables is also referred as bindings & Identifiers
+ variables can hold two types of data: _primitive_ & _reference_ values
+ few things you can do with variables:
	+ Create a variable with a descriptive name
	+ Store or update information stored in a variable
	+ Reference or “get” information stored in a variable


## Mental Model
+ Tentacles rather than boxes
	+ They do not _contain_ values; they _grasp_ them—two bindings can refer to the same value.

## Naming Convention
+ the name must contain only letters, digits, or the symbols `$`and `_`
+ variable names CANNOT start with numbers
+ variable names are case sensitive
+ variable names cannot be the same as keywords

## Declaration
### var (variable)
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
- A `var` variable will be available throughout the function body in which it is defined, no matter how deeply nested its definition
- “var” has no block scope
- “var” tolerates redeclarations
- “var” variables can be declared below their use - __HOISTING__
	- Declarations are hoisted, but assignments are not
### let
- The let keyword signals that the variable can be reassigned a different value.
- A `let` variable will only be available within the same block where it is defined
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
### const (constant)
- a const variable CANNOT be reassigned because it is constant. 
	- If you try to reassign a const variable, you’ll get a _TypeError_
- constant variables must be assigned a value when declared
	- If you try to declare a const variable without a value, you’ll get a _SyntaxError_


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





+ semicolon ;
+ Environment - The collection of bindings and their values that exist at a given time
	+ When a program starts up, this environment is not empty. It always contains bindings that are part of the language standard
	+ most of the time, it also has bindings that provide ways to interact with the surrounding system.
		+ For example, in a browser, there are functions to interact with the currently loaded website and to read mouse and keyboard input.
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