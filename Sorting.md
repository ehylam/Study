## Sorting
Sorting is the process of rearranging the items in a collection, so that the items are in some kind of order.


### Bubble Sort - Swapping
A sorting algorithm where the largest values bubble up to the top.

#### Pseudocode
* Start looping from the end of the array towards the beginning. ? //
* Start an inner loop with a variable called `j` from the beginning until i - 1
* if `arr[j]` is greater than `arr[j+1]`, swap those two values.
* Return the sorted array.


```
function bubbleSwap(arr) {
	let noSwaps;
	for (let i = arr.length; i > 0; i--) {
		noSwaps = true;
		for (let j = 0; j < i - 1; j++) {
			if(arr[j] > arr[j+1]) {
				let temp = arr[j];
				arr[j] = arr[j+1];
				arr[j+1] = temp;
				noSwaps = false;
			}
		}
		if (noSwaps) break;
		
	}
	
	return arr;
}

bubbleSwap([23,45,29,8]);
```


### Selection Sort - Swapping
Similar to bubble sort, but instead of first placing large values into sorted position, it places small values into sorted position.

#### Pseudocode
* Store the first element as the `min` value.
* Compare this variable to the next item in the array until you find a smaller number.
* If a smaller number is found designate that smaller number to be the new `min` value and continue until the end of the array.
* If the `min` value is not the value (index) you initially began with, swap the two values.
* Repeat this with the next element until the array is sorted.

```
function selectionSort(arr) {
	for( let i = 0; i < arr.length; i++) {
		let lowest = i;
		for(let j = i+1; j < arr.length; j++) {
			if(arr[j] < arr[lowest]) {
				lowest = j;
			}
		}
		
		if(lowest !== i) {
			var temp = arr[i];
			arr[i] = arr[lowest];
			arr[lowest] = temp;
		}
		
	}
	
	return arr;
} 

```


### Insertion Sort
Builds up the sort by gradually creating a larger left half which is always sorted.
* Good for continuous sorting. 

#### Pseudocode
* Start by picking the second element in the array
* Now compare the second element with the one before it and swap if necessary.
* Continue to the next element and if it is the incorrect order, iterate through the sorted portion (i.e. the left side) to place the element in the correct place.
* Repeat until the array is sorted.


```
function insertionSort(arr) {
	// comments refer to the second loop over.
	for(let i = 1; i < arr.length; i++) {
		let currentVal = arr[i]; // i = 2 // i = 3
		// 9 // 53

		for(var j = i - 1; j >= 0; j--) { // j = 1 // j = 2
			if (currentVal < arr[j]) { // if 9 is less than 2 // if 53 < 9
				arr[j+1] = arr[j];
			} else {
				break;

				// here.
			}
		}


		// j = 2
		arr[j+1] = currentVal;
	}
	return arr;
}



insertionSort([2,1,9,53,34]);

[1,2,9,53,34]

```


### Merge Sort
* A combination of two things - merging and sorting!
* Exports the fact that arrays of 0 or 1 element are always sorted.
* Works by decomposing an array into smaller arrays of 0 or 1 elements, then building up a newly sorted array.

* In order to implement merge sort, it's useful to first implement a function responsible for merging two sorted arrays.
* Given two arrays which are sorted, this helper function should create a new array which is also sorted, and consists of all of the elements in the two input arrays.
* This function should run in `O(n + m)` time and `O(n + m)` space and should not modify the parameters passed to it.

#### Merge - Pseudocode
* Create an empty array, take a look at the smallest values in each input array.
* While there are still values we haven't looked at...
	* If the value in the first array is smaller than the value in the second array, push the value in the first array into our results and move on to the net value into the first array.
	* If the value in the first array is larger than the value in the second array, push the value into the second array into our results and move on to the next value in the second array.
	* Once we exhaust one array, push in all remaining values from the other array.


```
// Split
[8, 3, 5, 4, 7, 6, 1, 2]

[8, 3, 5, 4] [7, 6, 1, 2]

[8, 3][5, 4] [7, 6][1, 2]

[8][3][5][4][7][6][1][2]

// Sort & Merge
[3, 8] [4, 5] [6, 7] [1, 2]

[3, 4, 5, 8] [1, 2, 6, 7]

[1, 2, 3, 4, 5, 6, 7, 8]

```


```
function merge(arr1, arr2) {
	let results = [];
	let i = 0;
	let j = 0;

	while(i < arr1.length && j < arr2.length) {
		if(arr2[j] > arr1[i]) {
			results.push(arr1[i]);
			i++;
			
		} else {
			results.push(arr2[j]);
			j++;
			
		}
	}

	while(i < arr1.length) {
		results.push(arr1[i]);
		i++;
	}

	while(j < arr2.length) {
		results.push(arr2[j]);
		i++;
	}

	return results;
}



merge([1,10,50],[2, 14, 99, 100]);
```


#### mergeSort Pseudocode
* Break up the array into halves until you have arrays that are empty or have one element
* Once you have the smaller sorted arrays merge those arrays with other sorted arrays until you are back at the full length of the array
* Once the array has been merged back together, return the merged (and sorted) array.

```
function mergeSort(arr) {
	if(arr.length <= 1) return arr;
	let mid = Math.floor(arr.length / 2);
	let left = mergeSort(arr.slice(0, mid));
	let right = mergeSort(arr.slice(mid));


	return merge(left, right);
	
}
```


### Quick sort
* Like merge sort, exploits the fact that arrays of 0 or 1 element are always sorted
* Works by selecting one element (called the "pivot")) and finding the index where the pivot should end up in the sorted array
* Once the pivot is positioned appropriately, quick sort can be applied on either side of the pivot


```
[5, 2, 1, 8, 4, 7, 6, 3]

[3, 2, 1, 4, 5, 7, 6, 8]

[1, 2, 3, 4, 5, 7, 6, 8]


// Right Side

[1, 2, 3, 4, 5, 6, 7, 8]

```

#### Pivot / Partion Helper
* In order to implement quick sort, it's useful to first implement a function responsible arranging elements in an array on either side of a pivot
* Given an array, this helper function should designate an element as the pivot
* It should then rearrange elements in the array so that all values less than the pivot are moved to the left of the pivot and all values greater than the pivot are moved to the right of the pivot
* The order of elements on either side of the pivot doesn't matter
* The helper should do this in place, that is, it should not create a new array
* When complete, the helper should return the index of the pivot


##### Picking a pivot
* The runtime of quick sort depends in part on how one selects the pivot
* Ideally, the pivot should be chosen so that it's roughy the median value in the data set you're sorting

#### Pivot pseudocode
* It will help to accept three arguments: an array, a start index, and an end index (these can default to 0 and the array length minus 1, respectively)
* Grab the pivot from the start of the array.
* Store the current pivot index in a variable (this will keep track of where the pivot should end up)
* Loop through the array from the start until the end
	* If the pivot is greater than the current element, increment the pivot index variable and then swap the current element with the element at the pivot index
* Swap the starting element (i.e. the pivot) with the pivot index
* Return the pivot index


```
function pivot(arr, start = 0, end = arr.length + 1) {
  let pivot = arr[start]; // 4
  let swapIndex = start;

  const swap = (array, i, j) {
	let temp = array[i];
	array[i] = array[j];
	array[j] = temp;
  }

  for(let i = start + 1; i < arr.length; i++) {
	  if(pivot > arr[i]) {
		  swapIndex++;
		  swap(arr, swapIndex, i);
	  }
  }

  swap(arr, start, swapIndex);
  return swapIndex;
}

pivot([4,8,2,1,5,7,6,3]);
```


#### Quick sort Pseudocode
* Call the pivot helper on the array
* When the helper returns to yo the updated pivot index, recursively calls the pivot helper on the subarray to the left of that index, and the subarray to the right of that index

```
function quickSort(arr, left = 0, right = arr.length - 1) {
	if(left < right) {
		let pivotIndex = pivot(arr, left, right);
	
		// Left
		quickSort(arr, left, pivotIndex - 1);
	
		// Right
		quickSort(arr, pinvotIndex + 1, right);

	}

	return arr;
}
```


#### Alternative code
```
function quickSort(arr) {
	// if the array capp
	ontains only 1 item.
	if(arr.length <= 1) return arr; // returns 2


	let pivot = arr[0]; // 23 // 5 // 42 // 6
	let left = []; // 5, 2, 6, 10 // 2 // 
	let right = []; // 42, 100 // 6, 10, 42, 100 // 100

	for(let i = 1; i < arr.length; i++) {
		if(arr[i] <= pivot) left.push(arr[i]) // 42 <= 23 // 5 <= 23 push
		else if(arr[i] > pivot) right.push(arr[i]); // push
		
	}

	left = quickSort(left); // 2 // 2, 5, 6, 10
	right = quickSort(right); // 6, 10 // 42, 100

	result = left.concat(pivot).concat(right); // 2, 5, 6 ...

	return result;
}


quickSort([23,42,5,2,6,10,100]);

```


### Radix Sort
* A special sorting algorithm that works on lists of numbers.
* It never makes comparisons between elements.
* It exploits the fact that information about sizing of a number is encoded in the number of digits.


#### Radix sort helpers
```
const getDigit = (num, i) => Math.floor(Math.abs(num) / Math.pow(10, i)) % 10;


const digitCount = (num) => {
	if(num === 0) return 1;
	return Math.floor(Math.log10(Math.abs(num))) + 1;
}

const mostDigits = (nums) => {
	let maxDigits = 0;
	
	for(let i = 0; i < nums.length; i++) {
		maxDigits = Math.max(maxDigits, digitCount(nums[i]));
	}

	return maxDigits;
}
```


#### Radix Sort Pseudocode
* Define a function that accepts list of numbers
* Figure out how many digits the largest number has
* Loop from k = 0 up to this largest number of digits
* For each iteration of the loop:
	* Create buckets for each digit (0 to 9)
	* place each number in the corresponding bucket based on it's `k`th digit
* Replace our existing array with values in our buckets, starting with 0 and going up to 9
* return list at the end

```
function radixSort(nums) {
	const getDigit = (num, i) => Math.floor(Math.abs(num) / Math.pow(10, i)) % 10;
	
	const digitCount = (num) => {
		if(num === 0) return 1;
		return Math.floor(Math.log10(Math.abs(num))) + 1;
	}
	
	const mostDigits = (nums) => {
		let maxDigits = 0;
		
		for(let i = 0; i < nums.length; i++) {
			maxDigits = Math.max(maxDigits, digitCount(nums[i]));
		}
	
		return maxDigits;
	}

	let numArr = nums;
	let maxDigitCount = mostDigits(numArr);

	for(let k = 0; k < maxDigitCount; k++) {
		let digitBuckets = Array.from({length: 10}, () => []);

		for(let i = 0; i < numArr.length; i++) {
			let digit = getDigit(numArr[i], k);
			digitBuckets[digit].push(numArr[i]);
		}

		numArr = [].concat(...digitBuckets);
		
	}

	return numArr;
}

radixSort([23,524,63454,643,23,12,7,2343]);
```