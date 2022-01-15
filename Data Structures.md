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


	// * Push pseudocode
	- Accept a value
	- Crate a new node using the value passed to the method
	- If there is no head property on the list, set the head and tail to be the newly create node.
	- Otherwise set the next property on the tail to be the new node and set the tail property on the list to be the newly created node.
	- Increment the length by 1


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



	// * Pop pseudocode
	- If there are no nodes in the list, return undefined
	- Loop through the list until you reach the tail
	- Set the next property of the 2nd last node to be null
	- Set the tail to be the 2nd to last node
	- Decrement the length of the list by 1
	- Return the value of the node removed

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


	// * Shift pseudocode
	- If there are no nodes, return undefined
	- Store the current head property in a temp variable
	- Set the head property to be the current head's next property
	- Decrement the length by 1
	- Return the value of the node removed

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



	// * Unshift pseudocode
	- This function should accept a value
	- Create a new node using the value passed to the function
	- If there is no head propery on the list, set the head and tail to be the newly created node.
	- Otherwise set the newly created node's next property to be the current head property on the list.
	- Set the head property on the list to be that newly create node
	- Increment the length of the list by 1
	- Return the linked list.


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

	
}


let list = new SinglyLinkedList();

list.push("hallo");
list.push("Goodbye");


```