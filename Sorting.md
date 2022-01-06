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