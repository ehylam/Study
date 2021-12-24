## Big O Notation
A way to describe the growth of an algorithm as the input grows.
"We say that an algorithm is `O(f(n))` if the number of simple operations the computer has to do is eventually less than a constant times `f(n)`, as `n` increases."

Some examples.
* `f(n)` could be linear `(f(n) = n)`
* `f(n)` could be quadratic `(f(n) = n2)`
* `f(n)` could be constant `(f(n) = 1)`

Examples:
```
// Example 1
function addUpTo(n) {
  let total = 0;
  for (let i = 1; i <= n; i++) {
  	total += i;
  }
  
  return total;
}


// Example 2
function addUpTo(n) {
  return n * (n + 1) / 2;
}

// Example 3
function countUpAndDown(n) {
  for (let i = 0; i < n; i++) {
  	console.log(i);
  }
  
  for (let j = n - 1; j >= 0; j--) {
    console.log(j);
  }
}

// Example 4
function printAllPairs(n) {
  for (let i = 0; i < n; i++) {
  	for(let j = 0; j < n; j++) {
	  console.log(i,j);
	}
  }
}

// Example 5
function logALeast5(n) {
  for (let i = 1; i <= Math.max(5, n); i++) {
  	console.log(i)
  }
}

// Example 6
function logAMost5(n) {
  for (let i = 1; i <= Math.min(5, n); i++) {
  	console.log(i)
  }
}
```

**Example 1**
`O(n)` - Linear growth.

**Example 2**
`O(1)` - Constant.

**Example 3**
`O(n)` - Linear growth (Think about the big picture - not `O(2n)`).

**Example 4**
`O(n2)` - Quadratic growth, An nested `O(n)` operation.

**Example 5**
`O(n)` - as `n` grows `O` grows.

**Example 6**
`O(1)` - Is constant after `n` is > 5



##### Constants doesn't matter
`O(2n)` => `O(n)`
`O(500)` => `O(1)`


##### Smaller terms don't matter
`O(n + 10)` => `O(n)`
`O(1000n + 50)` => `O(n)`
`O(n2 + 5n + 8)` => `O(n2)`

### Big O shorthands
* Analyzing complexity with big O can get complicated
* There are several rules of thumb that can help
* These rules won't **ALWAYS** work, but are helpful starting point.


#### Rule of thumb
* Arithmetic operations are constant
* Variable assignment is a constant
* Accessing elements in an array (by index) or by object (key) is constant
* In a loop, the complexity is the length of the loop times the complexity of whatever happens inside of the loop. (`~n2`)




### Space Complexity in JS
* Most primitives (boolean, numbers, characters(?), undefined, null) are constant space)
* Strings require `O(n)` space (where n is the string length)
* Reference types are generally `O(n)`, where `n` is the length (for arrays) or the number of keys (for objects)


## Logarithm
* The logarithm of a number roughly measures the number of times you can divide that number by 2 **before you get a value that's less than or equal to one**

```
8 (%2)
4 (%2)
2 (%2)
1

log(8) = 3


25 (%2)
12.5 (%2)
6.25 (%2)
3.125 (%2)
1.5625 (%2)
0.78125

log(25) = 4.64
```

### Objects
##### When to use them
* When you don't need order
* When you need fast access / insertion and removal.

- Insertion - `O(1)`
- Removal - `O(1)`
- Searching - `O(N)`
- Access - `I(1)`

- Object.keys(obj) - `O(N)`
- Object.values(obj) - `O(N)`
-  Object.entries(obj) - `O(N)`
-  {obj}.hasOwnProperty(obj.key) - `O(1)`


```
let instructor = {
	firstName: "Kelly",
	isInstructor: true,
	favouriteNumbers: [1,2,3,4]
}
```

### Arrays
* When you need order
* When you need fast access / insertion and removal (sort of...)
* 