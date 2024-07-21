# Data-Structures-Algorithms

### Static Arrays

#### Description
Static arrays have a fixed size upon initialization, meaning their size cannot change after being set. These arrays are common in strictly typed languages like Java, C++, and C#. Arrays are fundamental data structures and form the basis of many other data structures and algorithms.

#### Operations

**Reading:** Accesses an element by its index.
- **Complexity:** O(1)
- **Code Example:**
```java
int[] myArray = {1, 3, 5};
int value = myArray[i];
```

**Insert at End:** Adds an element to the end of the array.
- **Complexity:** O(1)
- **Code Example:**
```java
public void insertEnd(int[] arr, int n, int length, int capacity) {
    if (length < capacity) {
        arr[length] = n;
    }
}
```

**Remove from End:** Removes the last element of the array.
- **Complexity:** O(1)
- **Code Example:**
```java
public void removeEnd(int[] arr, int length) {
    if (length > 0) {
        arr[length - 1] = 0;
        length--;
    }
}
```

**Insert at Index:** Inserts an element at a specific index, shifting elements to the right.
- **Complexity:** O(n)
- **Code Example:**
```java
public void insertMiddle(int[] arr, int i, int n, int length) {
    // Shift starting from the end to i.
    for (int index = length - 1; index > i - 1; index--) {
        arr[index + 1] = arr[index];
    }
    arr[i] = n;
}
```

**Remove at Index:** Removes an element from a specific index, shifting elements to the left.
- **Complexity:** O(n)
- **Code Example:**
```java
public void removeMiddle(int[] arr, int i, int length) {
    // Shift starting from i + 1 to end.
    for (int index = i + 1; index < length; index++) {
        arr[index - 1] = arr[index];
    }
}
```

#### Suggested Problems
1. [Remove Duplicates From Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) - Easy
2. [Remove Element](https://leetcode.com/problems/remove-element/) - Easy

### Dynamic Arrays

#### Description
Dynamic arrays are more common and useful because they can be resized. Unlike static arrays, dynamic arrays do not require specifying a size upon initialization. In different languages, dynamic arrays may be assigned a default size—Java assigns 10 and C# assigns 4 by default. These arrays resize at runtime as needed.

#### Mechanics

When inserting into a dynamic array, the operating system finds the next empty space and pushes the element into it. When the capacity is reached, the array is resized by copying the elements to a new array that is double the original size.

**Push Back:** Adds an element to the end of the array.
- **Complexity:** Amortized O(1)
- **Code Example:**
```java
public void pushback(int n) {
    if (length == capacity) {
        this.resize();
    }
    arr[length] = n;
    length++;
}
```

**Resize:** Resizes the array to double its current capacity.
- **Complexity:** O(n)
- **Code Example:**
```java
public void resize() {
   // Create new array of double capacity
   capacity = 2 * capacity;
   int[] newArr = new int[capacity]; 
   
   // Copy elements to newArr
   for (int i = 0; i < length; i++) {
       newArr[i] = arr[i];
   }
   arr = newArr;
}  
```

#### Suggested Problems
1. [Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/) - Easy

### Stacks

#### Description
A stack is a data structure that follows the Last In, First Out (LIFO) principle. The last element placed inside the stack is the first element that comes out. Stacks are dynamic data structures that support three primary operations: push, pop, and peek.

In the physical world, a stack can be conceptualized by thinking of plates at a dinner party buffet. When you go to take a plate, you can only remove from the top, and similarly, when you finish your meal, the stack of plates can only be built by adding them on top of each other. This is exactly what a stack in the software world does.

#### Operations

**Push:** Adds an element to the top of the stack.
- **Complexity:** O(1)
- **Code Example:**
```java
public void push(int n) {
    stack.add(n);
}
```

**Pop:** Removes the element from the top of the stack.
- **Complexity:** O(1)
- **Code Example:**
```java
public int pop() {
    return stack.remove(stack.size() - 1);
}
```

**Peek:** Returns the top element without removing it.
- **Complexity:** O(1)
- **Code Example:**
```java
public int peek() {
    return stack.get(stack.size() - 1);
}
```

#### Suggested Problems
1. [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) - Easy
2. [Min Stack](https://leetcode.com/problems/min-stack/) - Medium
3. [Baseball Game](https://leetcode.com/problems/baseball-game/) - Easy

### Queues

#### Description
A queue is a data structure that follows the First In, First Out (FIFO) principle. The first person to enter the queue is the first person to be served. Examples of queues in the real world include lines at the bank and print jobs where multiple documents are handled on a first-come, first-served basis.

#### Operations

**Enqueue:** Adds an element to the end of the queue.
- **Complexity:** O(1)
- **Code Example:**
```java
public void enqueue(int val) {
    ListNode newNode = new ListNode(val);
    if (this.right != null) {  
        this.right.next = newNode;
        this.right = this.right.next;
    } else {       
        this.left = newNode;
        this.right = newNode;
    }
}
```

**Dequeue:** Removes an element from the front of the queue.
- **Complexity:** O(1)
- **Code Example:**
```java
public int dequeue() {
    if (this.left == null) {
        // Queue is empty 
        System.exit(0);
    }
    int val = this.left.val;
    this.left = this.left.next;
    if (this.left == null) {
        this.right = null;
    }
    return val;
}   
```

#### Suggested Problems
1. [Number of Students Unable to Eat Lunch](https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/) - Easy
2. [Implement Stack Using Queues](https://leetcode.com/problems/implement-stack-using-queues/) - Easy
