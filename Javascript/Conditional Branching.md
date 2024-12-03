## `If` statement
+ The `if(...)` statement evaluates a condition in parentheses and, if the result is true, executes a block of code. `else` block executes when the condition is falsy.
+ evaluates the expression in its parentheses and converts the result to a Boolean

```js
let year = prompt('In which year was the ECMAScript-2015 specification published?', '');

if (year < 2015) {
  alert( 'Too early...' );
} else if (year > 2015) {
  alert( 'Too late' );
} else {
  alert( 'Exactly!' );
}
```

## Ternary Operator
+ The question mark operator has a low precedence
```js
// syntax
let result = condition ? value1 : value2;

// sample
let accessAllowed = age > 18 ? true : false;

// multiple condition
```
	
Non-traditional use of ‘?’
+ Sometimes the question mark ? is used as a replacement for if
+ It’s not recommended to use the question mark operator in this way. less readable
```js
let company = prompt('Which company created JavaScript?', '');

(company == 'Netscape') ?
   alert('Right!') : alert('Wrong.');
```

>[!NOTE]
>The purpose of the question mark operator ? is to return one value or another depending on its condition. Please use it for exactly that. Use if when you need to execute different branches of code



## Switch statement
+ __Syntax__
	+ one or more _cases_, _optional_ default
	+ checked for a _strict equality_ against cases
		+ values must be of the same type to match
	+  common convention to place the _default_ case at the end
		+ placement of default is not strictly enforced by the language
	```js 
	switch(x) {  //strict equality
	  case 'value1':  // if (x === 'value1')
	    ...
	    [break]
	
	  case 'value2':  // if (x === 'value2')
	    ...
	    [break]
	
	  default:
	    ...
	    [break]
	}
	```

+ __Behavior__
	+ Direct Matching: The switch statement evaluates the expression (e.g., value) and jumps directly to the matching case or default. It does not sequentially check all cases.
	+ No Match? Default! If no matching case is found, JavaScript executes the default case (if provided).
	+ Fall-through Behavior: Once a match is found, JavaScript executes all subsequent cases until a break is encountered, regardless of whether those cases match.
	+ The _break_ acts like a `goto` command
	+ If a match is found for an earlier case, the later cases won't be checked, even if they also match the expression value.
	+  if you think about it as a series of checks, it looks like sequential evaluation
		+ conceptually it jumps directly to the first matching case or default

+ __Fall-through__
	+ If there is no break then the execution continues with the next case _without any checks_
	+ If break is omitted, execution will proceed to the next case clause, even to the default clause, regardless of whether the value of that clause's expression matches. This behavior is called "_fall-through_"
	```js
	let a = 2 + 2;
	
	switch (a) {
	  case 3:
	    alert( 'Too small' );
	  case 4:
	    alert( 'Exactly!' );
	  case 5:
	    alert( 'Too big' );
	  default:
	    alert( "I don't know such values" );
	}
	
	alert( 'Exactly!' );
	alert( 'Too big' );
	alert( "I don't know such values" );
	```

+ __Grouping Cases__
	+ The ability to “group” cases is a side effect of how `switch/case` works without `break`
	```js
	let a = 3;

	switch (a) {
	  case 4:
	    alert('Right!');
	    break;
	
	  case 3: // (*) grouped two cases
	  case 5:
	    alert('Wrong!');
	    alert("Why don't you take a math class?");
	    break;
	
	  default:
	    alert('The result is strange. Really.');
	}
	```

+ **Reasons to use a `default`**
	1. To 'catch' an unexpected value or when another case gets added at the end (defensive programming)
	2. To handle 'default' actions, where the cases are for special behavior
	3. Good practice

+ __Other Sample__
	+ switch is not compiled into a sequence of if-then-elses, it's a jump table that works fast for two as well as for two hundred items.
	```js
	let value = 5;

	switch (value) {
	    case 1:
	        console.log("Case 1");
	        break;
	    default:
	        console.log("Default case");
	    case 6:
	        console.log("Case 6");
	}

	// Output
	// Default case
	// Case 6
	```



Here, if `value === 2`, you might imagine it first checking `case 1`, then `case 2`, then executing the matching block. This is how many tutorials explain `switch`, but **this is not how modern engines implement it under the hood**.