### Singly Linked Lists
A data structure that contains a head, tail, and length property.

Linked Lists consist of nodes, and each node has a value and a pointer to another node or null.

```
// Store a piece of data - val
// Reference to next node - next


class Node {
	constructor(val) {
		this.val = val;
		this.next = null;
	}
}

// Bad but this shows how linked lists work.
let first = new Node("Hi");
first.next == new Node("there")
first.next.next = new Node("how");
first.next.next.next = new Node("are");
first.next.next.next.next = new Node("you");



class SinglyLinkedList {
	constructor() {
		this.head = null;
		this.tail = null;
		this.length = 0;
	}


	/* Push pseudocode
	- Accept a value
	- Crate a new node using the value passed to the method
	- If there is no head property on the list, set the head and tail to be the newly create node.
	- Otherwise set the next property on the tail to be the new node and set the tail property on the list to be the newly created node.
	- Increment the length by 1
	*/


	push(val) {
		let newNode = new Node(val);
		
		if(!this.head) {
			this.head = newNode;
			this.tail = this.head;
		} else {
			this.tail.next = newNode;
			this.tail = newNode;
		}

		this.length++;

		return this;
	}



	/* Pop pseudocode
	- If there are no nodes in the list, return undefined
	- Loop through the list until you reach the tail
	- Set the next property of the 2nd last node to be null
	- Set the tail to be the 2nd to last node
	- Decrement the length of the list by 1
	- Return the value of the node removed
	*/


	pop() {
		if(!this.head) return undefined;

		let current = this.head;
		let newTail = current;

		while(current.next) {
			newTail = current;
			current = current.next;
		}

		this.tail = newTail;
		this.tail.next = null;
		this.length--;

		if(this.length === 0) {
			this.head = null;
			this.tail = null;
		}
		
		return current;
	}


	/* Shift pseudocode
	- If there are no nodes, return undefined
	- Store the current head property in a temp variable
	- Set the head property to be the current head's next property
	- Decrement the length by 1
	- Return the value of the node removed
	*/

	shift() {
		if(!this.head) return undefined;

		let currentHead = this.head;
		let newHead = this.head.next;
		
		this.length--;

		if(this.length === 0) {
			this.tail == null;
		}
		return currentHead;
	}



	/* Unshift pseudocode
	- This function should accept a value
	- Create a new node using the value passed to the function
	- If there is no head propery on the list, set the head and tail to be the newly created node.
	- Otherwise set the newly created node's next property to be the current head property on the list.
	- Set the head property on the list to be that newly create node
	- Increment the length of the list by 1
	- Return the linked list.
	*/

	unshift(val) {
		let newNode = new Node(val);
		if(this.length === 0) {
			this.head = newNode;
			this.tail = this.head;
		} else {
			newNode.next = this.head;
			this.head = newNode;
		}

		this.length++;

		return this;
	}



	/* Get pseudocode
	- This function should accept a index
	- If the index is less than zero or greater than or equal to the length of the list, return null
	- Loop throguh the list until you reach the index and return the node at that specific index

	*/
	

	get(index) {
		if(index < 0 || index > this.length) return null;
		let counter = 0;
		let current = this.head;

		while(counter !== index) {
			counter = current.next;
			counter++;
		}

		return current;
		
	}


	/* Set pseudocode
	- This function should accept a value and an index
	- Use your get function to find the specific node
	- If the node is found, set the value of that node to be the value passed to the function and return true
	- 
	*/


	set(index, val) {
		let foundNode = this.get(index);

		if(foundNode) {
			foundNode.val = val;
			return true;
		}

		return false;
	}
	

	/* Insert pseudocode
	- If the index is less than zero or greater than the length, return false
	- If the index is 0, unshift a new node to the start of the list
	- Otherwise, using the get method, access the node at the index - 1
	- Set the next property on that node to be the new node
	- Set the prev property on that new node to be the previous next
	- Increment the length
	- return true
	*/


	insert(index, val) {
		if(index < 0 || index > this.length) return false;
		if(index === this.length) return !!this.push(val);
		if(index === 0) return !!this.unshift(val);
		let newNode = new Node(val);
		let previous = this.get(index - 1);
		let temp = prev.next;
		prev.next = newNode;
		newNode.next = temp;
		this.length++;

		return true;
	}



	/* Remove pseudocode
	- If the index is less than zero or greater than the length, return undefined
	- If the index is the same as the length - 1, pop
	- If the index is 0, shift
	- Otherwise, using the get method, access the node at the index - 1
	- Set the next property on that node to be the next of the next node
	- Decrement the length
	- Return the value of the node removed
	- 

	*/


	remove(index) {
		if(index < 0 || index >= this.length) return undefined;
		if(index === 0) return !!this.shift();
		if(index === this.length - 1) return !!this.pop();
		let previousNode = this.get(index - 1);
		let removed = previousNode.next;
		previousNode.next = removed.next;
		this.length--;

		return removed;

	}


	/* Reverse pseudocode
	- Swap the head and tail
	- Create a variable called next, previous, node and initialize it to the head property
	- Loop through the list
	- Set next to be the next property on whatever node is
	- Set previous to be the vale of the node variable
	- Set the node variable to be the value of the next variable

	reverse() {
		let node = this.head; // 13 // 27
		this.head = this.tail;
		this.tail = node;
		
		let previous = null;
		let next;

		for(let i = 0; i < this.length; i++) {
			next = node.next; // 27 // 32
			node.next = previous; // null // 13
			previous = node; // 13 // 27
			node = next; // 27 // 32
		}

		return this;
	}

	
}


let list = new SinglyLinkedList();

list.push("hallo");
list.push("Goodbye");


```



### Doubly Linked Lists
Like singly linked list, but can be linked two ways (prev/next).
```
class Node() {
	constructor() {
		this.val = val;
		this.next = null;
		this.prev = null;
	}
}


class DoublyLinkedList {
	constructor() {
		this.head = null
		this.tail = null;
		this.length = 0;
	}

	/* Push
	- Create a new node with the value passed to the function
	- If the head property is null set the head and tail to be the newly created node
	- If not, set the next property on the tail to be that node
	- Set the previous property on the newly created node to be the tail.
	- Set the tail to be the newly created node.
	- Increment the length
	- Return the Doubly Linked List
	*/


	push(val) {
		let newNode = new Node(val); // 99

		if(this.length === 0) {
			this.head = newNode; // 99
			this.tail = newNode; // 99
		} else {
			// Update the tail's (99) next value to hold newNode
			this.tail.next = newNode; // 99.tail.next = 100
			// Set new node's previous to the current tail of the list
			newNode.prev = this.tail; // 100.prev = 99
			// Set the tail of the list to be the newNode
			this.tail = newNode; // 99.tail = newNode
		}

		this.length++;
		return this;
	}

	/* Push
	- If there is no head, return undefined
	- Store the current tail in a variable to return later
	- If the length is 1, set the head and tail to be null
	- Update the tail to be the previous Node.
	- Set the new tail's next to null
	- Decrement the length
	- Return the value removed
	*/
	
	pop() {
		if(this.length === 0) return undefined;
		let poppedNode = this.tail;

		if(this.length === 1) {
			this.head = null;
			this.tail = null;
		} else {
			// set the current tail to be the previous node
			this.tail = poppedNode.prev;
			// set the new tail's next to be null
			this.tail.next = null;
			// Remove the linkage between the tail and the popped node
			poppedNode.prev = null;
		}

		this.length--;
		return this;
		
	}

	
}

const list = new DoublyLinkedList();

list.push(99); // -> 99
list.push(100); // -> 99, 100
list.push(232); // -> 99, 100, 232

```

