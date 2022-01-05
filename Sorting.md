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
