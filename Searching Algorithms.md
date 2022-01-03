## Searching Algorithms
#### Linear Search
* Moving at a set interval.
* Looping through an array of values and checking if it matches (if so return the index else return -1 - Like `indexOf()` ).*



#### Binary Search (Divide and Conquer)
* Binary search is a much faster form of search
* Rather than eliminate one element at a time, you can eliminate half of the remaining elements at a time.
* Binary search works on sorted arrays!

##### Pseudocode
1. This function accepts a sorted array and a value
2. Create a left pointer at the start of the array, and a right pointer at the end of the array.
3. While the left pointer comes before the right pointer:
	1. Create a pointer in the middle.
	2. If you find the value you want, return the index.
	3. If the value is too small, move the left pointer up.
	4. If the value is too large, move the right pointer down.
4. If you never find the value, return -1.


```
function binarySearch(arr, val) {
	let start = 0;
	let end = arr.length - 1;
	let middle = Math.floor((start + end) / 2);	
	
	while (arr[middle] !== val && start <= end) {		
		if (val < arr[middle]) {
			start = middle - 1;
		} else {
			end = middle + 1;
		}
		
		middle = Math.floor((start + end) / 2);
	}
	
	if(arr[middle] == val ) {
		return middle;
	} else {
		return -1;
	}
}
```


### 'Naive' String Search
*	Suppose you want to count the number of times a smaller string appears in a longer string.
*	A straightforward approach involves checking pairs of characters individually.


##### Pseudocode
1. Define a function that takes two strings
2. Loop over the longer string
3. Loop over the shorter string
4. if the characters don't match, break out of the inner loop
5. if the characters do match, keep going
6. if you complete the inner loop and find a match, increment the count of matches.
7. return the count.


```
function naiveSearch(long, short) {
	let count = 0;
	for (let i = 0; i < long.length; i++) {
		for (let j = 0; j < short.length; j++) {
			if (short[j] !== long[i+j]) {
				break;
			}
			
			if (j === short.length - 1) {
				count++;
			}
		}
	}
	
	return count;
	
}

naiveSearch('lorie loled', 'lol');

```


