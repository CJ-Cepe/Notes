# 🌌 Loops

> "Keep doing this until a specific condition is met."

+ Loops are a way to repeat a block of code multiple times
+  a loop exits when its condition becomes falsy.
+ __Key Concepts__
	1. Repeats Instructions Until _Stopping Condition_
		- Loops run a block of code repeatedly until a specified condition is met
		- _Iteration_: A single execution of the code block in the loop. "Iterate" means to repeat.
	2. Initialization
		- This is where the loop starts. It often sets up a variable (called the _iterator_) to keep track of the current state.
		+ `for (let i = 0; ...) { ... }`
			- Here, `let i = 0;` is the *inline variable declaration*
			- The iterator `i` is visible only inside the loop
	3. Stopping Condition
		- the condition that the iterator variable is evaluated against
		- if the condition evaluates to true the code block will run, and if it evaluates to false the code will stop.
	4. Iteration Statement
		+ Updates the iterator variable after each iteration, to the point that the condition becomes false
		+ this is always evaluated (or run) each time the loop has gone through a full iteration
+ **Looping in Reverse**
    - Iterator variable = highest desired value
    - Condition = less than the desired amount
    - Iteration statement = --

## ☄️ For loop
+ most commonly used loop
```js
for (begin; condition; step) {
// ... loop body ...
}

//Example 1
//This is called an “inline” variable declaration
for (let i = 0; i < 3; i++) {
  alert(i); // 0, 1, 2
}
alert(i); // error, no such variable

//Example 2
let i = 0;

for (i = 0; i < 3; i++) { // use an existing variable
  alert(i); // 0, 1, 2
}

alert(i); // 3, visible, because declared outside of the loop
```
+ begin - 	Executes once upon entering the loop.
	+ begin executes once
+ condition - Checked before every loop iteration. If false, the loop stops.
+ body - Runs again and again while the condition is truthy.
+ step - Executes after the body on each iteration.
+ Skipping Parts
	+ Any part of for can be skipped. 
	+ the two `for` semicolons `;` must be present
	```js
	//omit begin
	let i = 0; // we have i already declared and assigned
	
	for (; i < 3; i++) { // no need for "begin"
	  alert( i ); // 0, 1, 2
	}
	
	//omit step
	let i = 0;
	
	for (; i < 3;) { // identical to while (i < 3)
	  alert( i++ );
	}
	
	//omit condition - everything
	for (;;) {
	  // repeats without limits
	}
	```

## ☄️ While loop
+ ideal when we don’t know in advance how many times the loop should run
+ Any expression or variable can be a loop condition, not just comparisons: the condition is evaluated and converted to a boolean by while
	```js
	while (condition) {
	  // code
	  // so-called "loop body"
	}

	let i = 3;
	while (i) { // i != 0 | i
	  alert( i );
	  i--;
	}
	```

## ☄️ Do While loop
+ you want a piece of code to run at least once and then loop based on a specific condition after its initial run.
    - Note that the while and do...while loop are different! Unlike the while loop, do...while will run at least once whether or not the condition evaluates to true.

	```js
	do {
	  // loop body
	} while (condition);
	
	let i = 0;
	do {
	  alert( i );
	  i++;
	} while (i < 3);
	```

## ☄️ Break & Continue



- **For … in (objects)**
    
    ```jsx
    for (key in object) {
      // executes the body for each key among object properties
    }
    ```
    
    ```jsx
    let user = {
      name: "John",
      age: 30,
      isAdmin: true
    };
    
    for (let key in user) {
      // keys
      alert( key );  // name, age, isAdmin
      // values for the keys
      alert( user[key] ); // John, 30, true
    }
    ```
    + For ... in
    + For ... of
    
- Break & Continue
> [!CAUTION] _Please note that syntax constructs that are not expressions cannot be used with the ternary operator ?. In particular, directives such as break/continue aren’t allowed there._
> 
+ can you use break/conttinue inside if else? and ternary?
+ what is a directive


+ A _**label**_ is an identifier with a colon before a loop
	+ It's not a goto, it's just a way for break and continue to say which loop they're referring to.
	+ we need to break out from multiple nested loops at once
	+ The continue directive can also be used with a label. In this case, code execution jumps to the next iteration of the labeled loop
	+ Labels do not allow to “jump” anywhere
	+ A break directive must be inside a code block. Technically, any labelled code block will do. Although, 99.9% of the time `break` is used inside loops
	+ A `continue` is only possible from inside a loop
		+ If you used continue without 'outer' label, it would go to the next iteration of inner loop. 
	+ Labelled loops or blocks are very uncommon. Usually, function calls can be used instead of loop jumps.
	```jsx
	labelName: for (...) {
	  ...
	}

	//EXAMPLE
	outer: for (let i = 0; i < 3; i++) {
	  for (let j = 0; j < 3; j++) {
	    let input = prompt(`Value at coords (${i},${j})`, '');
	    // if an empty string or canceled, then break out of both loops
	    if (!input) break outer; // (*)
	
	    // do something with the value...
	  }
	}
	
	alert('Done!');

	//We can also move the label onto a separate line:
	outer:
	for (let i = 0; i < 3; i++) { ... }

	```

Using a labeled block with break
+ You can label statements other than loops, such as simple blocks, but only break statements can reference non-loop labels.
+ Labels in JavaScript are not limited to loops; they can be used with any block of code. However, they are primarily associated with loops because they are most commonly used to control the flow of nested loops. That said, they can also be applied outside of loops in certain scenarios.
1. With Loops (Primary Use Case)
	+ Labels are often used with break or continue to control the flow of nested loops.
2. With Non-Loop Blocks
	+ Labels can also be applied to any code block and used with break to exit the block early.
	+ When to Use Labels Without Loops?
		+ Labels can be used without loops in rare cases where you have complex blocks of code and want a way to exit them early. However, this is not common and can often be replaced with simpler constructs like if conditions or function returns for better readability
	
```js
label: {
    console.log("Start block");
    if (true) {
        break label; // Exits the labeled block
    }
    console.log("This won't run");
}
console.log("After block");

Start block
After block


```
+ Labeled function declarations
	+ Labels can only be applied to statements, not declarations. There is a legacy grammar that allows function declarations to be labeled in non-strict code
	+ Non-plain functions, such as generator functions and async functions can neither be labeled in strict code, nor in non-strict code
	+ The labeled function declaration syntax is [deprecated](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Deprecated_and_obsolete_features) and you should not use it, even in non-strict code. You cannot actually jump to this label within the function body
	```js
	L: function F() {}

"use strict";
L: function F() {}
// SyntaxError: functions cannot be labelled

L: function* F() {}
// SyntaxError: generator functions cannot be labelled

	```


        
- Break directive
	- “break” out of the loop from within the loop’s block.
	- great for situations when a loop’s condition must be checked not in the beginning or end of the loop, but in the middle or even in several places of its body
    - the break statement is used to immediately exit a loop when a certain condition is met. When working with nested loops, the break statement can be used to break out of both the inner and outer loops.
    - If a break statement is encountered in the inner loop, only the inner loop will be exited and the outer loop will continue to iterate. However, if the break statement is included in the outer loop, both the outer and inner loops will be exited and the program will continue executing after the loop.
    - Break is a loop control statement along with continue and pass.
    - You can use break to exit for loops and while loops.
    - Break only exits the innermost loop in a nested loop.
    - You can’t use break to exit an if statement unless the if statement is inside of a loop.
    - You can also use the break statement to terminate a switch statement or a labeled statement.
- Continue directive
	- a “lighter version” of break
	- It doesn’t stop the whole loop. Instead, it stops the current iteration and forces the loop to start a new one (if the condition allows).
	- do the rest gets executed when continued?
    - used when you want to restart a new iteration of a loop.
    - This statement can be used in a while loop, for loop or for-in loop.
    - When JavaScript executes the continue statement, any remaining code left in the current iteration of the loop body is skipped. The code will resume execution at the start of the loop (as a new iteration of the loop).