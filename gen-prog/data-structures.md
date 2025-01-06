# Data Structures & Algorithms
Data Structures
+ The best data structure is -> it depends
	+ based on application specific needs
Algorithms
+ there can be more algorithms to solve 
+ has assumptions
+ not an implementation
+ describes the steps to perform only
+ implementation is the code to perform those steps
+ many implementation of an algorithm
+ there can be many algorithms that accomplish the same task
+ there can be many implementations of the same algorithm
Arrays
+ contiguous block in memory
	+ all elements are stored in 1 contiguous block - allocated
	+ static length can't be resized ? 
	+ every element occupies the same amount of space in memory ?
	+ if objects are stored, reference are only stored. always same size
	+ if an array starts at starts at memory address x, and the size of each element in the array is y, we can calculate the memory address of the ith element by using the following expression: x + i * y
	+ if we know the index of an element the time to retrieve the element will be the same no matter where it is in the array
	+ good at retrieving elements if index is known
		+ to retrieve element from an array
			+ multiply the size of the element by the index
			+ get the start address of the array
			+ add the start address to the result of the multiplication
		+ consistent steps to retrieve O(1)
	+ memory efficient
	+ 
	+ bogus
+ 

Big-O > O of "1"
+ compare algorithm performance
+ more objective measure
+ look at the number of steps to execute an algorithm
+ time and space complexity
	+ amount of time - were more concern
	+ amount of space - memory is cheap today
+ look at the worst case
	+ best - rare
	+ average - doesn't give worst
+ give us an idea how an algorithm performs as the number of items it has to deal with grows
	+ tells us how an algorithm will scale
+ constants don't factor
	+ the n influence
+ linear time complexity
+ input x steps
+ comparing time complexity of different algorithms in an objective manner, in a hardware independent manner