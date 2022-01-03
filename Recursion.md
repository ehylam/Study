## Recursion
* Needs a base case to end the recursion.


Helper method recursion
```
function outer(input) {
	let outerScopedVariable = [];
	
	function helper(helperInput) {
		// Modify the outerScopedVariable
		helper(helperInput--);
	}
	
	helper(input);
	
	return outerScopedVariable;
}

function collectOddValues(arr) {
	let result = [];
	
	function helper(helperInput) {
		if(helperInput.length === 0) {
			return;
		}
		
		if(helper[input[0] % 2 !== 0) {
			result.push(helperInput[0]);
		}
		
		
		helper(helperInput.slice(1)) // O(N) - Remove the first item and reshuffle the array
	}
	
	helper(arr);
	
	return result;
}



```


#### Pure recursion
```
function. collectOddVaues(arr) {
	let newArr = [];
	
	if(arr.length === 0) {
		return newArr;
	}
	
	if(arr[0] % 2 !== 0) {
		newArr.push(arr[0]);
	}
	
	newArr = newArr.concat(collectOddValues(arr.slice(1)));
	
	return newArr;
}

```

* For arrays, use methods like **slice**, **spread operator,** and **concat** that make copies of arrays so you do not mutate them.
* Remember that strings are immutable so you will need to use methods like slice, or substring to make copies of strings.
* To make copies of objects, use Object.assign, or the spread operator.

