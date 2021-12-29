## Problem Solving
1. Can you restate the problem in your own words? (Make sure you understand the question)
2. What are the inputs that go into the problem?
3. What are the output that should come from the solution to the problem?
4. Can the outputs be determined from the inputs? In other words, do I have enough information to solve the problems? (You may not be able to answer this question until you set about solving the problem. That's okay; it's still worth considering the question at this early stage.)
5. How should I label the important pieces of data that are a part of the problem?


#### Practice Question
```
Write a function which takes two numbers and returns their sum.
1. Implement addition for the two values
2. int, float, string
3. int, float, string?
4. ??
5. ??



10000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000 + 10000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000

= infinity

```


### Explore examples
* Coming up with examples can help you understand the problem better.
* Examples also provided sanity checks that your eventual solutions works how it should.

*"Write a function which takes in a string and returns counts of each character in the string."*


* Start with a simple example
	* `charCount("aaaa") // returns {a:4}`
* Progress to more complex examples
	 ```
	 charCount("my phone number is 184937") // spaces?
	 charCount("hello Hi") // uppercase h
	 charCount("") // {}
	 charCount() // return error?
	 ```
* Explore examples with empty inputs
* Explore examples with invalid inputs


### Break it down
*"Write a function which takes in a string and returns counts of each character in the string."*

```
function charCount(str) {
	// do something
	// Make an object to turn
	const result = {};
	let string = str;
	// Lowercase the entire string
	string = string.toLowerCase();
	
	// Loop through the string
	for (let i = 0; i < string.length; i++) {
		let char = string[i];
		// If the character is an empty space/period, skip/continue loop.
		if(char === ' ' || char === ',') {
		} else if ( char in result ) { 		// else if character is not in object, add character and 1 to object
            result[char] = result[char]+1;
		} else { 		// else find character in object and increment the number value	
			result[char] = 1;
		}


	}

	// Return object at the end
	// returns an object that contains the characters and their count - charCount("aa"){a: 2}

    return result;
}
```


### Solve/Simplify
#### Simplify
* Find the core difficulty in what you're trying to do
* Temporarily ignore that difficulty
* Write a simplified solution
* Then incorporate that difficulty back



### Look back & refactor
#### Refactoring
* Can you check the result?
* Can you derive the result differently?
* Can you understand it at a glance?
* Can you use the result or method for some other problem?
* Can you improve the performance of your solution
* Can you think of other ways to refactor?
* How have other people solved this problem?

```
function charCount(str) {
	const result = {};
	let string = str.toLowerCase();
	
	for (var char of string) {
		if(/[a-z0-9]/.test(char)) {
			if(result[char] > 0) {
				result[char]++;
			} else {
				result[char] = 1;
			}
		}
	}
    return result;
}
```

```
function charCount(str) {
	const result = {};
	for (var char of str) {
		if(isAlphaNumeric(char)) {
			char = char.toLowerCase();
			// result[char] == ++result[char] || 1;
			if(char in result) {
			 	result[char] = result[char]+1;
			} else {
				result[char] = 1;
			}		
		}
	}
    return result;
}



function isAlphaNumeric(char) {
	const code = char.charCodeAt(0);
	if(!(code > 47 && code < 58) &&
	   !(code > 64 && code < 91) &&
	   !(code > 96 && code < 123)) {
			return false;
	}
	
	return true;
}
```

### Problem solving patterns
#### Frequency Counters
This pattern uses object or sets to collect values/frequencies of values.
This can often avoid the need for nested loops or `O(n^2)` operations with arrays / strings.


Example:
Write a function called **same**, which accpets two arrays. The function should return true if every value in the array has it's corresponding value squared in the second array. The frequency of values must be the same.

```
same([1,2,3], [4,1,9]) // true
same([1,2,3], [1,9]) // false
same([1,2,1], [4,4,1]) // false
```

A naive solution:
```
function same(arr1, arr2) {
	if(arr1.length !== arr2.length) {
		return false;
	}
	
	for(let i = 0; i < arr1.length; i++) {
		let correctIndex  arr2.indexOf(arr1[i] ** 2);
		if(correctIndex == -1) {
			return false;
		}
		
		arr2.splice(correctIndex,1);
	}
	
	return true;
}


```

A refactored solution:
```
function same(arr1, arr2){
    if(arr1.length !== arr2.length){
        return false;
    }
    let frequencyCounter1 = {}
    let frequencyCounter2 = {}
    for(let val of arr1){
        frequencyCounter1[val] = (frequencyCounter1[val] || 0) + 1
    }
    for(let val of arr2){
        frequencyCounter2[val] = (frequencyCounter2[val] || 0) + 1        
    }
    console.log(frequencyCounter1);
    console.log(frequencyCounter2);
    for(let key in frequencyCounter1){
        if(!(key ** 2 in frequencyCounter2)){
            return false
        }
        if(frequencyCounter2[key ** 2] !== frequencyCounter1[key]){
            return false
        }
    }
    return true
}

same([1,2,3,2,5], [9,1,4,4,11])
```

#### Multiple pointers
Creating **pointers** or values that correspond to an index or position and move towards the beginning, end or middle based on a certain condition.

**Very** efficient for solving problems with minimal space complexity as well.

Example:
Write a function called sumZero which accepts a sorted array of integers. The function should find the first pair where the sum is 0. Return an array that includes bth values that sum to zero or undefined if a pair doesn't exist.

A naive solution:
```
sumZero([-3,-2,-1,0,1,2,3]) // [-3, 3]
sumZero([-2,0,1,3]) // undefined
sumZero([1,2,3]) // undefined



function sumZero(arr) {
	for(let i = 0; i < arr.length; i++) {
		for(let j = i+1; j < arr.length; j++) {
			if(arr[i] + arr[j] === 0) {
				return [arr[i],arr[j]];
			}
		}
	}
}
```

A refactored solution:
```
function sumZero(arr) {
	let left = 0;
	let right = arr.length - 1;
	
	while(left < right) {
		let sum = arr[left] + arr[right];
		if(sum === 0) {
			return [arr[left], arr[right]];
		} else if(sum > 0) {
			right--;
		} else {
			left++;
		}
	}
}
```


Example 2:
Implement a function called countUniqueValues, which accepts a sorted array, and counts the unqiue values in the array. There can be negative numbers in the array but it will always be sorted.


A refactored solution:
```
function countUniqueValues(arr) {
	if(arr.length === 0) {
		return 0;
	}
	var i = 0;
	
	for var j = 1; j < arr.length; j++) {
		if(arr[i] !== arr[j]) {
			i++;
			arr[i] = arr[j];
		}
	}
	
	return i;
}

```

### Sliding window
This pattern involves creating a window which can either be an array or number from one condition to another. Depending on a certain condition, the window either increases or closes (and a new window is created). Very useful for keep track of a subset of data in an array/string etc.

a refactored solution:
```
function maxSubarrySum(arr, num) {
	let maxSum = 0;
	let tempSum = 0;
	
	
	if(arr.length < num) return null;
	
	for(let i = 0; i < num; i++) {
		maxSum += arr[i];
	}
	
	
	tempSum = maxSum;
	
	for (let i = num; i < arr.length; i++) {
		tempSum = tempSum - arr[i - num] + arr[i];
		maxSUm = Math.max(maxSum, tempSum);
	}
	
	return maxSum;
}

```