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