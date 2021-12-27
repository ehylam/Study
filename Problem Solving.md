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

