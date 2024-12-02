# `If` statement
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
+ The value of x is checked for a strict equality to the value from the first case (that is, value1) then to the second (value2) and so on.
+ If the equality is found, switch starts to execute the code starting from the corresponding case, until the nearest break (or until the end of switch).
+ If no case is matched then the default code is executed (if it exists).


the execution starts from case 4 until the nearest break.
If there is no break then the execution continues with the next case without any checks
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

If break is omitted, execution will proceed to the next case clause, even to the default clause, regardless of whether the value of that clause's expression matches. This behavior is called "fall-through".


Should we use a break; in the last default case?

As a matter of good form, put a break after the last case (the default here) even though it's logically unnecessary. Some day when another case gets added at the end, this bit of defensive programming will save you.



A switch statement first evaluates its expression. It then looks for the first case clause whose expression evaluates to the same value as the result of the input expression [...]

If no matching case clause is found, the program looks for the optional default clause [...] By convention, the default clause is the last clause, but it does not need to be so.


**Reasons to use a `default`**

_1.To 'catch' an unexpected value_
_To handle 'default' actions, where the cases are for special behavior._