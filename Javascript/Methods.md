DataType
+ typeof x || typeof(x)
## Numbers
+ Number System
	+ toString(base)
+ Rounding
	+ Math.floor
	+ Math.ceil
	+ Math.round
	+ Math.trunc
	+ num.toFixed(base)
+ Check
	+ isNaN() Number.isNaN()
	+ isFinite() Number.isFinite()
+ Extract numeric value
	+ parseInt 
	+ parseFloat
+ Others - Math
	+ Math.random()
	+ Math.max()
	+ Math.min()
	+ Math.pow()
	+ Number.MAX_SAFE_INTEGER
	+ Number.MIN_SAFE_INTEGER
+ Object.is()
	+ When an internal algorithm needs to compare two values for being exactly the same
+ String
	+ .length
	+ .at()
	+ for..of
	+ .toLowerCase()
	+ .toUpperCase()
	+ search for substring
		+ .indexOf(substr, pos).
		+ .lastIndexOf(substr, pos)
		+ .includes(substr, pos)
		+ .startsWidth()
		+ .endsWidth()
	+ get a substring
		+ .slice(start, [, end]) excludes end
		+ .substring(start [, end]) excludes end
			+ allows start to be greater than end (in this case it simply swaps start and end values).
			+ Negative arguments are (unlike slice) not supported, they are treated as 0
		+ str.substr(start [, length])
	+ get UTF code
		+ str.codePointAt(pos)
		+ String.fromCodePoint(code)
	+ compare
		+ str.localeCompare(str2)
		+ str.trim()
		+ str.repeat(n)