Others (DYK)
```js

alert( 0.1 + 0.2 == 0.3 ); // false
alert( 0.1 + 0.2 ); // 0.30000000000000004

// 0.0001100110011001100110011001100110011001100110011001101
alert(0.1.toString(2));

//0.001100110011001100110011001100110011001100110011001101
alert(0.2.toString(2));

// 0.0100110011001100110011001100110011001100110011001101
alert((0.1 + 0.2).toString(2))

```
+ 0.1 and 0.2 in binary are actually unending fractions 
+ 0.3 === 1/3 an endless fraction 0.33333(3)
Solution
+ method [toFixed(n)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed)
	```js
	let sum = 0.1 + 0.2;
	alert( +sum.toFixed(2) ); // 0.3
	```
+ temporary multiply by 10+ -> turn them into integers
	```js
	alert( (0.1 * 10 + 0.2 * 10) / 10 ); // 0.3
	alert( (0.28 * 100 + 0.14 * 100) / 100); // 0.4200000000000001
	```

For `null` returns `"object"` – this is an error in the language, it’s not actually an object.

what is statement vs expression