# Data-Structures-Algorithms

---

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

---

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

---

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

---

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

### Sliding Window (Fixed Size)

#### Description
The fixed sliding window technique involves maintaining two pointers that are `k` elements apart. This technique is useful for problems that require examining subarrays or substrings of a fixed size. The goal is often to find some property within these fixed-size windows.

#### Operations

**Contains Duplicate II:**
Given an array, return true if there are two elements within a window of size `k` that are equal.

- **Brute Force Approach:**
    - **Complexity:** O(n^2)
    - **Code Example:**
    ```java
    public static boolean closeDuplicatesBruteForce(int[] nums, int k) {
        for (int L = 0; L < nums.length; L++) {
            for (int R = L + 1; R < Math.min(nums.length, L + k); R++) {
                if (nums[L] == nums[R]) {
                    return true;
                }
            }
        }
        return false;
    }
    ```

- **Optimized Approach Using Sliding Window:**
    - **Complexity:** O(n)
    - **Code Example:**
    ```java
    public static boolean closeDuplicates(int[] nums, int k) {
        HashSet<Integer> window = new HashSet<>(); // Current window of size <= k
        int L = 0;
        for (int R = 0; R < nums.length; R++) {
            if (R - L + 1 > k) {
                window.remove(nums[L]);
                L++;
            }
            if (window.contains(nums[R])) {
                return true;
            }
            window.add(nums[R]);
        }
        return false;
    }
    ```

#### Suggested Problems
1. [Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/) - Easy
2. [Number of Subarrays of Size K and Avg Greater than or Equal to Threshold](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/) - Medium

---

### Sliding Window (Variable Size)

#### Description
The variable sliding window technique involves expanding and contracting the window size dynamically to satisfy a given constraint. This technique is useful for problems where the subarray size is not fixed and can vary.

#### Operations

**Longest Substring Without Repeating Characters:**
Find the length of the longest subarray with unique values.

- **Code Example:**
    ```java
    public static int longestSubarray(int[] nums) {
        int length = 0;
        int L = 0;
        for (int R = 0; R < nums.length; R++) {
            if (nums[L] != nums[R]) {
                L = R;
            }
            length = Math.max(length, R - L + 1);
        }
        return length;
    }
    ```

**Minimum Size Subarray Sum:**
Find the minimum length subarray where the sum is greater than or equal to the target.

- **Code Example:**
    ```java
    public static int shortestSubarray(int[] nums, int target) {
        int L = 0, total = 0;
        int length = Integer.MAX_VALUE;
        for (int R = 0; R < nums.length; R++) {
            total += nums[R];
            while (total >= target) {
                length = Math.min(R - L + 1, length);
                total -= nums[L];
                L++;
            }
        }
        if (length ==  Integer.MAX_VALUE) {
            return 0;
        } 
        return length;
    }
    ```

#### Suggested Problems
1. [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) - Medium
2. [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/) - Medium
3. [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/) - Medium

---

### Two Pointers

#### Description
The two pointers technique involves using two pointers to iterate through an array or list. This technique is versatile and can solve various problems such as finding pairs with specific properties, reversing arrays, and detecting palindromes.

#### Operations

**Valid Palindrome:**
Check if a string is a palindrome.

- **Code Example:**
    ```java
    public static boolean isPalindrome(String word) {
        int L = 0, R = word.length() - 1;
        while (L < R) {
            if (word.charAt(L) != word.charAt(R)) {
                return false;
            }
            L++;
            R--;
        }
        return true;
    }
    ```

**Two Sum II:**
Given a sorted input array, return the two indices of two elements that sum up to the target value.

- **Code Example:**
    ```java
    public static int[] targetSum(int[] nums, int target) {
        int L = 0, R = nums.length - 1;
        while (L < R) {
            if (nums[L] + nums[R] > target) {
                R--;
            } else if (nums[L] + nums[R] < target) {
                L++;
            } else {
                return new int[] {L, R};
            }
        }
        return null;
    }
    ```

#### Suggested Problems
1. [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/) - Easy
2. [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) - Medium
3. [Remove Duplicates From Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) - Easy
4. [Remove Duplicates From Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/) - Medium
5. [Container With Most Water](https://leetcode.com/problems/container-with-most-water/) - Medium
6. [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) - Hard

---

### Prefix Sum

#### Description
Prefix sums are useful for quickly calculating the sum of elements in a subarray. By precomputing the cumulative sums of elements, you can answer range sum queries efficiently.

#### Operations

**Building the Prefix Sum Array:**
Given an array, build a prefix sum array where each element at index `i` is the sum of the elements from the start of the array to `i`.

- **Code Example:**
    ```java
    public class PrefixSum {
        List<Integer> prefix;
        public PrefixSum(int[] nums) {
            prefix = new ArrayList<>();
            int total = 0;
            for (int n : nums) {
                total += n;
                prefix.add(total);
            }
        }
        public int rangeSum(int left, int right) {
            int preRight = prefix.get(right);
            int preLeft = left > 0 ? prefix.get(left - 1) : 0;
            return (preRight - preLeft);
        }
    }
    ```

#### Suggested Problems
1. [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) - Medium
2. [Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/) - Easy
3. [Range Sum Query 2D - Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/) - Medium
4. [Find Pivot Index](https://leetcode.com/problems/find-pivot-index/) - Easy
5. [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) - Medium

---

### Singly Linked Lists

#### Description
A singly linked list is a linear data structure composed of nodes, where each node contains a value and a pointer to the next node in the sequence. This structure allows for efficient insertion and deletion operations.

#### Operations

**Creating a Singly Linked List:**
A linked list is created by chaining `ListNode` objects together. Each `ListNode` object has two attributes: `val` (value) and `next` (pointer to the next node).

- **Code Example:**
    ```java
    public class ListNode {
        int val;
        ListNode next;
        public ListNode(int val) {
            this.val = val;
            this.next = null;
        }
    }
    ```

**Traversal:**
Traversal involves iterating through the linked list from the head to the end using a while loop.

- **Code Example:**
    ```java
    ListNode cur = head;
    while (cur != null) {
        cur = cur.next;
    }
    ```

**Appending:**
Appending a node to the end of a singly linked list involves updating the `next` pointer of the last node to point to the new node.

- **Code Example:**
    ```java
    tail.next = newNode;
    tail = newNode;
    ```

**Deletion:**
Deleting a node involves updating the `next` pointer of the previous node to skip over the node to be deleted.

- **Code Example:**
    ```java
    head.next = head.next.next;
    ```

#### Suggested Problems
1. [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) - Easy
2. [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) - Easy

---

### Doubly Linked Lists

#### Description
A doubly linked list is a linear data structure similar to a singly linked list but with an additional pointer in each node that points to the previous node. This allows for more efficient bidirectional traversal.

#### Operations

**Insertion:**
Insertion involves updating the `next` and `prev` pointers of the adjacent nodes.

- **Code Example:**
    ```java
    tail.next = newNode;
    newNode.prev = tail;
    tail = newNode;
    ```

**Deletion:**
Deletion involves updating the `next` pointer of the previous node and the `prev` pointer of the next node.

- **Code Example:**
    ```java
    node.prev.next = node.next;
    if (node.next != null) {
        node.next.prev = node.prev;
    }
    ```

#### Suggested Problems
1. [Design Linked List](https://leetcode.com/problems/design-linked-list/) - Medium
2. [Design Browser History](https://leetcode.com/problems/design-browser-history/) - Medium

---

### Fast and Slow Pointers

#### Description
The fast and slow pointer technique involves using two pointers that move at different speeds to solve various problems in linked lists, such as finding the middle of a list or detecting cycles.

#### Operations

**Finding the Middle of a Linked List:**
Using fast and slow pointers, the slow pointer moves one step at a time while the fast pointer moves two steps at a time. When the fast pointer reaches the end, the slow pointer will be at the middle.

- **Code Example:**
    ```java
    public static ListNode middleOfList(ListNode head) {
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
    ```

**Cycle Detection:**
Using Floyd's Tortoise and Hare algorithm, the fast pointer moves twice as fast as the slow pointer. If there is a cycle, the fast pointer will eventually catch up to the slow pointer.

- **Code Example:**
    ```java
    public static boolean hasCycle(ListNode head) {
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                return true;
            }
        }
        return false;
    }
    ```

#### Suggested Problems
1. [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) - Easy
2. [Find The Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/) - Medium
3. [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) - Easy
4. [Maximum Twin Sum Of A Linked List](https://leetcode.com/problems/maximum-twin-sum-of-a-linked-list/) - Medium
5. [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/) - Medium

---

### Hash Usage

#### Description
Hash maps and hash sets are fundamental data structures used for fast access and retrieval of data. They are based on hashing, which allows for nearly constant time complexity for search, insert, and delete operations. Hash maps store key-value pairs, while hash sets store unique elements.

#### Operations

**Contains Duplicate:**
Given an array, return true if any value appears at least twice in the array, otherwise return false.

- **Code Example:**
    ```java
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            if (set.contains(num)) {
                return true;
            }
            set.add(num);
        }
        return false;
    }
    ```

**Two Sum:**
Given an array of integers and a target value, return the indices of the two numbers that add up to the target.

- **Code Example:**
    ```java
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }
        throw new IllegalArgumentException("No two sum solution");
    }
    ```

**LRU Cache:**
An LRU (Least Recently Used) Cache is a data structure that stores a limited number of items and evicts the least recently used item when the limit is exceeded.

- **Code Example:**
    ```java
    class LRUCache {
        private int capacity;
        private Map<Integer, Integer> map;
        private LinkedList<Integer> order;

        public LRUCache(int capacity) {
            this.capacity = capacity;
            this.map = new HashMap<>();
            this.order = new LinkedList<>();
        }

        public int get(int key) {
            if (!map.containsKey(key)) return -1;
            order.remove((Integer) key);
            order.addFirst(key);
            return map.get(key);
        }

        public void put(int key, int value) {
            if (map.containsKey(key)) {
                order.remove((Integer) key);
            } else if (map.size() == capacity) {
                int leastUsed = order.removeLast();
                map.remove(leastUsed);
            }
            order.addFirst(key);
            map.put(key, value);
        }
    }
    ```

**Time Complexity:**
- **Insert, Search, and Delete: \(O(1)\)**
    - **Explanation:** Hash maps and hash sets provide average-case constant time complexity for these operations due to efficient hashing and handling of collisions.

---

### Hash Implementation

#### Description
Hash maps are typically implemented using arrays under the hood, combined with a hash function to map keys to array indices. Collisions are handled using techniques like chaining or open addressing.

#### Operations

**Hash Function:**
A hash function converts a key into an integer index that maps to an array position. This is done by summing the ASCII values of the characters in the key and taking the modulo with the array size.

- **Code Example:**
    ```java
    public int hash(String key) {
        int index = 0;
        for (int i = 0; i < key.length(); i++) {
            index += (int) key.charAt(i);
        }
        return index % this.capacity;
    }
    ```

**Insert:**
To insert a key-value pair, compute the hash of the key to determine the array index. Handle collisions using chaining or open addressing.

- **Code Example:**
    ```java
    public void put(String key, String val) {
        int index = this.hash(key);

        while (true) {
            if (this.map[index] == null) {
                this.map[index] = new Pair(key, val);
                this.size += 1;
                if (this.size >= this.capacity / 2) {
                    this.rehash();
                }
                return;       
            } else if (this.map[index].key.equals(key)) {
                this.map[index].val = val;
                return;
            }
            index += 1;
            index = index % this.capacity;
        }    
    }
    ```

**Get:**
Retrieve a value by computing the hash of the key and checking the corresponding array index. Handle collisions by following the chain or probing for the key.

- **Code Example:**
    ```java
    public String get(String key) {
        int index = this.hash(key);
        while (this.map[index] != null) {
            if (this.map[index].key.equals(key)) {
                return this.map[index].val;
            }  
            index += 1;
            index = index % this.capacity;
        }    
        return null;
    }
    ```

**Remove:**
To remove a key-value pair, find the key and set the corresponding array index to null. Handle the hole created by rehashing subsequent entries.

- **Code Example:**
    ```java
    public void remove(String key) {
        if (this.get(key) == null) {
            return;
        }
        
        int index = this.hash(key);
        while (true) {
            if (this.map[index].key.equals(key)) {
                this.map[index] = null;
                this.size -= 1;
                return;
            }    
            index += 1;
            index = index % this.capacity;
        }
    }
    ```

**Rehashing:**
When the array becomes half full, double the array size and rehash all existing entries to the new array.

- **Code Example:**
    ```java
    public void rehash() {
        this.capacity = 2 * this.capacity;
        Pair[] newMap = new Pair[this.capacity];

        Pair[] oldMap = this.map;
        this.map = newMap;
        this.size = 0;
        for (Pair p : oldMap) {
            if (p != null) {
                this.put(p.key, p.val);
            }
        }
    }
    ```

**Time Complexity:**
- **Insert, Search, and Delete: \(O(1)\)**
    - **Explanation:** With efficient hashing and collision resolution, these operations can be performed in constant time on average.
- **Rehashing: \(O(n)\)**
    - **Explanation:** Rehashing requires re-inserting all elements into a new larger array, which takes linear time.

---
### Insertion Sort

#### Description
Insertion sort is a simple sorting algorithm that builds the final sorted array one item at a time. It is much like sorting playing cards in your hands. The array is virtually split into a sorted and an unsorted part. Values from the unsorted part are picked and placed at the correct position in the sorted part.

#### Concept

- **Algorithm:**
    1. Iterate from the second element to the end of the array.
    2. Compare the current element (key) to its predecessor.
    3. If the key element is smaller than its predecessor, compare it to the elements before. Move the greater elements one position up to make space for the swapped element.

- **Code Example:**
    ```java
    public static int[] insertionSort(int[] arr) {
        for (int i = 1; i < arr.length; i++) {
            int j = i - 1;
            while (j >= 0 && arr[j + 1] < arr[j]) {
                int tmp = arr[j + 1];
                arr[j + 1] = arr[j];
                arr[j] = tmp;
                j--;
            }
        }
        return arr;
    }
    ```

- **Stability:**
    Insertion sort is a stable sorting algorithm, meaning it maintains the relative order of equal elements.

- **Time Complexity:**
    - Best Case: \(O(n)\) (when the array is already sorted)
    - Average and Worst Case: \(O(n^2)\)

---

### Merge Sort

#### Description
Merge sort is a divide-and-conquer algorithm that divides the array into two halves, recursively sorts them, and then merges the sorted halves to produce the sorted array.

#### Concept

- **Algorithm:**
    1. Divide the array into two halves.
    2. Recursively sort each half.
    3. Merge the two halves to form a sorted array.

- **Code Example:**
    ```java
    public static int[] mergeSort(int[] arr, int l, int r) {
        if (l < r) {
            int m = (l + r) / 2;
            mergeSort(arr, l, m);
            mergeSort(arr, m + 1, r);
            merge(arr, l, m, r);
        }
        return arr;
    }

    public static void merge(int[] arr, int l, int m, int r) {
        int length1 = m - l + 1;
        int length2 = r - m;

        int[] L = new int[length1];
        int[] R = new int[length2];

        for (int i = 0; i < length1; i++) {
            L[i] = arr[l + i];
        }
        for (int j = 0; j < length2; j++) {
            R[j] = arr[m + 1 + j];
        }

        int i = 0, j = 0, k = l;
        while (i < length1 && j < length2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        while (i < length1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        while (j < length2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }
    ```

- **Stability:**
    Merge sort is a stable sorting algorithm.

- **Time Complexity:**
    - Best, Average, and Worst Case: \(O(n \log n)\)

---

### Quick Sort

#### Description
Quick sort is a divide-and-conquer algorithm that picks an element as a pivot and partitions the array around the pivot. The key process in quicksort is the partition process, which ensures that the pivot is in its correct position.

#### Concept

- **Algorithm:**
    1. Pick a pivot element.
    2. Partition the array around the pivot such that elements less than the pivot are on the left and elements greater than the pivot are on the right.
    3. Recursively apply the above steps to the sub-arrays.

- **Code Example:**
    ```java
    public static int[] quickSort(int[] arr, int s, int e) {
        if (e - s + 1 <= 1) {
            return arr;
        }

        int pivot = arr[e];
        int left = s;

        for (int i = s; i < e; i++) {
            if (arr[i] < pivot) {
                int tmp = arr[left];
                arr[left] = arr[i];
                arr[i] = tmp;
                left++;
            }
        }

        arr[e] = arr[left];
        arr[left] = pivot;

        quickSort(arr, s, left - 1);
        quickSort(arr, left + 1, e);

        return arr;
    }
    ```

- **Stability:**
    Quick sort is not a stable sorting algorithm.

- **Time Complexity:**
    - Best and Average Case: \(O(n \log n)\)
    - Worst Case: \(O(n^2)\)

---

### Bucket Sort

#### Description
Bucket sort is a distribution sort that works by distributing the elements of an array into a number of buckets. Each bucket is then sorted individually, either using a different sorting algorithm or recursively applying the bucket sort.

#### Concept

- **Algorithm:**
    1. Create an empty array of buckets.
    2. Scatter the elements from the input array into the appropriate buckets.
    3. Sort each non-empty bucket.
    4. Gather the sorted elements from each bucket.

- **Code Example:**
    ```java
    public static int[] bucketSort(int[] arr) {
        int[] counts = {0, 0, 0}; // Assuming arr contains only 0, 1, or 2

        for (int num: arr) {
            counts[num] += 1;
        }

        int i = 0;
        for (int n = 0; n < counts.length; n++) {
            for (int j = 0; j < counts[n]; j++) {
                arr[i] = n;
                i++;
            }
        }

        return arr;
    }
    ```

- **Stability:**
    Bucket sort is not stable as it overwrites the original array.

- **Time Complexity:**
    - Best, Average, and Worst Case: \(O(n)\) (assuming uniform distribution)

---

### Binary Search Array

#### Description
Binary search is an efficient way of searching for elements within a sorted array. Given a sorted array and a target value, binary search divides the array into halves to eliminate half of the elements from the search at each step, making the search process faster.

#### Operations

**Binary Search:**
Binary search involves finding the middle element of the current subarray and comparing it to the target value. Depending on the comparison, the search continues in the left or right half of the subarray.

- **Code Example:**
    ```java
    public static int binarySearch(int[] arr, int target) {
        int L = 0, R = arr.length - 1;
        int mid;

        while (L <= R) {
            mid = L + (R - L) / 2;
            if (target > arr[mid]) {
                L = mid + 1;
            } else if (target < arr[mid]) {
                R = mid - 1;
            } else {
                return mid;
            }
        }
        return -1;
    }
    ```

**Time Complexity:**
- **Best, Average, and Worst Case: \(O(\log n)\)**
    - **Explanation:** Each step in binary search reduces the search space by half, leading to a logarithmic time complexity.

---

### Binary Search Range

#### Description
Binary search range involves finding a target value within a given range using the binary search algorithm. This variation is useful when the search range is provided instead of a specific target.

#### Operations

**Binary Search Range:**
This involves using a binary search algorithm to guess the target within the provided range.

- **Code Example:**
    ```java
    public static int isCorrect(int n) {
        if (n > 10) {
            return 1;
        } else if (n < 10) {
            return -1;
        } else {
            return 0;
        }
    }

    public static int binarySearch(int low, int high) {
        int mid;

        while (low <= high) {
            mid = (low + high) / 2;

            if (isCorrect(mid) > 0) {
                high = mid - 1;
            } else if (isCorrect(mid) < 0) {
                low = mid + 1;
            } else {
                return mid;
            }
        }
        return -1;
    }
    ```

**Time Complexity:**
- **Best, Average, and Worst Case: \(O(\log n)\)**
    - **Explanation:** Similar to standard binary search, each step reduces the search space by half.

---

### Binary Tree

#### Description
A binary tree is a data structure where each node has at most two children, referred to as the left child and the right child. It starts with a root node, and each node in the tree has zero, one, or two child nodes.

#### Operations

**Node Definition:**
A binary tree node contains a value and pointers to its left and right children.

- **Code Example:**
    ```java
    public class TreeNode {
        int val;
        TreeNode left;
        TreeNode right;

        public TreeNode(int val) {
            this.val = val;
            left = null;
            right = null;
        }
    }
    ```

**Properties:**
- **Root Node:** The topmost node in the tree.
- **Leaf Node:** A node with no children.
- **Height:** The length of the longest path from the root to a leaf.
- **Depth:** The length of the path from a node to the root.

**Time Complexity:**
- **Traversal: \(O(n)\)**
    - **Explanation:** Each node is visited exactly once.

---

### Binary Search Tree (BST)

#### Description
A binary search tree (BST) is a binary tree with the additional property that for any node, the left subtree contains values less than the node, and the right subtree contains values greater than the node. This property makes BSTs useful for efficient searching, insertion, and deletion operations.

#### Operations

**BST Search:**
To search for a value, compare it with the root. If the value is smaller, search the left subtree; if larger, search the right subtree.

- **Code Example:**
    ```java
    public boolean search(TreeNode root, int target) {
        if (root == null) {
            return false;
        }
        if (target > root.val) {
            return search(root.right, target);
        } else if (target < root.val) {
            return search(root.left, target);
        } else {
            return true;
        }
    }
    ```

**Time Complexity:**
- **Best, Average Case: \(O(\log n)\)**
    - **Explanation:** In a balanced BST, each comparison halves the search space.
- **Worst Case: \(O(n)\)**
    - **Explanation:** In a skewed BST, the tree behaves like a linked list.

---

### BST Insert and Remove

#### Description
Inserting and removing nodes in a BST involves maintaining the BST property after the operation.

#### Operations

**Insertion:**
To insert a new node, traverse the tree to find the appropriate position and insert the node.

- **Code Example:**
    ```java
    public TreeNode insert(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }
        if (val > root.val) {
            root.right = insert(root.right, val);
        } else {
            root.left = insert(root.left, val);
        }
        return root;
    }
    ```

**Removal:**
To remove a node, consider three cases: node has no children, node has one child, or node has two children.

- **Code Example:**
    ```java
    public TreeNode remove(TreeNode root, int val) {
        if (root == null) {
            return null;
        }
        if (val > root.val) {
            root.right = remove(root.right, val);
        } else if (val < root.val) {
            root.left = remove(root.left, val);
        } else {
            if (root.left == null) {
                return root.right;
            } else if (root.right == null) {
                return root.left;
            } else {
                TreeNode minNode = minValueNode(root.right);
                root.val = minNode.val;
                root.right = remove(root.right, minNode.val);
            }
        }
        return root;
    }

    public TreeNode minValueNode(TreeNode root) {
        TreeNode curr = root;
        while (curr.left != null) {
            curr = curr.left;
        }
        return curr;
    }
    ```

**Time Complexity:**
- **Best, Average Case: \(O(\log n)\)**
    - **Explanation:** In a balanced BST, operations halve the search space.
- **Worst Case: \(O(n)\)**
    - **Explanation:** In a skewed BST, the tree behaves like a linked list.

---

### Depth-First Search (DFS)

#### Description
Depth-First Search (DFS) is a tree traversal algorithm that explores as far as possible along each branch before backtracking. It is typically implemented using recursion.

#### Operations

**Inorder Traversal:**
Visit the left subtree, the root node, and then the right subtree.

- **Code Example:**
    ```java
    public void inorder(TreeNode root) {
        if (root == null) {
            return;
        }
        inorder(root.left);
        System.out.println(root.val);
        inorder(root.right);
    }
    ```

**Preorder Traversal:**
Visit the root node, the left subtree, and then the right subtree.

- **Code Example:**
    ```java
    public void preorder(TreeNode root) {
        if (root == null) {
            return;
        }
        System.out.println(root.val);
        preorder(root.left);
        preorder(root.right);
    }
    ```

**Postorder Traversal:**
Visit the left subtree, the right subtree, and then the root node.

- **Code Example:**
    ```java
    public void postorder(TreeNode root) {
        if (root == null) {
            return;
        }
        postorder(root.left);
        postorder(root.right);
        System.out.println(root.val);
    }
    ```

**Time Complexity:**
- **Traversal: \(O(n)\)**
    - **Explanation:** Each node is visited exactly once.

---

### Breadth-First Search (BFS)

#### Description
Breadth-First Search (BFS) is a tree traversal algorithm that explores all nodes at the present depth level before moving on to nodes at the next depth level. It is typically implemented using a queue.

#### Operations

**BFS Traversal:**
Visit all nodes level by level using a queue to keep track of the nodes at the current level.

- **Code Example:**
    ```java
    public void bfs(TreeNode root) {
        Deque<TreeNode> queue = new ArrayDeque<TreeNode>();
        if (root != null) {
            queue.add(root);
        }
        int level = 0;
        while (!queue.isEmpty()) {
            System.out.print("level " + level + ": ");
            int levelLength = queue.size();
            for (int i = 0; i < levelLength; i++) {
                TreeNode curr = queue.removeFirst();
                System.out.print(curr.val + " ");
                if (curr.left != null) {
                    queue.add(curr.left);
                }
                if (curr.right != null) {
                    queue.add(curr.right);
                }
            }
            level++;
            System.out.println();
        }
    }
    ```

**Time Complexity:**
- **Traversal: \(O(n)\)**
    - **Explanation:** Each node is visited exactly once.

---

### BST Sets and Maps

#### Description
Sets and Maps are interfaces that can be implemented using trees, providing efficient \(O(\log n)\) operations.

#### Operations

**Set:**
A set ensures that all values are unique and sorted.

- **Code Example:**
    ```java
    TreeSet<Integer> set = new TreeSet<>();
    set.add(1);
    set.add(2);
    set.add(3);
    ```

**Map:**
A map stores key-value pairs and is sorted by the key.

- **Code Example:**
    ```java
    TreeMap<String, Integer> map = new TreeMap<>();
    map.put("Alice", 123);
    map.put("Brad", 345);
    map.put("Collin", 678);
    ```

**Time Complexity:**
- **Insertion and Lookup: \(O(\log n)\)**
    - **Explanation:** Tree-based sets and maps maintain balance, ensuring logarithmic operations for insertion and lookup.

---

### Trie

#### Description
A trie, also known as a prefix tree, is a tree data structure used for storing a dynamic set or associative array where the keys are usually strings. Each node in the trie represents a single character of the key, and the path from the root to a node represents a prefix of the keys.

#### Operations

**Insert:**
To insert a word, iterate through each character of the word. If the character does not exist, insert it into the trie. Mark the end of the word in the last node.

- **Code Example:**
    ```java
    class TrieNode {
        boolean word;
        Map<Character, TrieNode> children = new HashMap<>();
    }

    public class Trie {
        TrieNode root;

        public Trie() {
            root = new TrieNode();
        }

        public void insert(String word) {
            TrieNode curr = root;
            for (char c : word.toCharArray()) {
                curr.children.putIfAbsent(c, new TrieNode());
                curr = curr.children.get(c);
            }
            curr.word = true;
        }
    }
    ```

**Search:**
To search for a word, iterate through each character of the word. If a character does not exist, return false. If all characters exist and the last node is marked as a word, return true.

- **Code Example:**
    ```java
    public boolean search(String word) {
        TrieNode curr = root;
        for (char c : word.toCharArray()) {
            if (!curr.children.containsKey(c)) {
                return false;
            }
            curr = curr.children.get(c);
        }
        return curr.word;
    }
    ```

**Starts With:**
To check if there is any word that starts with a given prefix, iterate through each character of the prefix. If a character does not exist, return false. If all characters exist, return true.

- **Code Example:**
    ```java
    public boolean startsWith(String prefix) {
        TrieNode curr = root;
        for (char c : prefix.toCharArray()) {
            if (!curr.children.containsKey(c)) {
                return false;
            }
            curr = curr.children.get(c);
        }
        return true;
    }
    ```

**Time Complexity:**
- **Insert, Search, and Starts With: \(O(m)\)**
    - **Explanation:** Where \(m\) is the length of the word or prefix.

---

### Union-Find

#### Description
Union-Find, also known as Disjoint Set Union (DSU), is a data structure that keeps track of a set of elements partitioned into disjoint (non-overlapping) subsets. It supports two primary operations: union and find.

#### Operations

**Find:**
Finds the root of the set containing the element. Uses path compression to make subsequent searches faster.

- **Code Example:**
    ```java
    public int find(int n) {
        int p = par.get(n);
        while (p != par.get(p)) {
            par.put(p, par.get(par.get(p)));
            p = par.get(p);
        }
        return p;
    }
    ```

**Union:**
Joins two subsets into a single subset. Uses union by rank to keep the tree flat.

- **Code Example:**
    ```java
    public boolean union(int n1, int n2) {
        int p1 = find(n1), p2 = find(n2);
        if (p1 == p2) {
            return false;
        }
        if (rank.get(p1) > rank.get(p2)) {
            par.put(p2, p1);
        } else if (rank.get(p1) < rank.get(p2)) {
            par.put(p1, p2);
        } else {
            par.put(p1, p2);
            rank.put(p2, rank.get(p2) + 1);
        }
        return true;
    }
    ```

**Time Complexity:**
- **Find and Union: \(O(\alpha(n))\)**
    - **Explanation:** \(\alpha(n)\) is the inverse Ackermann function, which is very slow-growing and practically constant for all reasonable \(n\).

---

### Segment Tree

#### Description
A segment tree is a data structure that allows for efficient range queries and updates. It is particularly useful for scenarios where there are multiple range queries and updates on an array.

#### Operations

**Build:**
Constructs the segment tree from an array.

- **Code Example:**
    ```java
    public static SegmentTree build(int[] nums, int L, int R) {
        if (L == R) {
            return new SegmentTree(nums[L], L, R);
        }

        int M = (L + R) / 2;
        SegmentTree root = new SegmentTree(0, L, R);
        root.left = build(nums, L, M);
        root.right = build(nums, M + 1, R);
        root.sum = root.left.sum + root.right.sum;
        return root;
    }
    ```

**Update:**
Updates a value at a specific index and adjusts the tree accordingly.

- **Code Example:**
    ```java
    public void update(int index, int val) {
        if (this.L == this.R) {
            this.sum = val;
            return;
        }

        int M = (this.L + this.R) / 2;
        if (index > M) {
            this.right.update(index, val);
        } else {
            this.left.update(index, val);
        }
        this.sum = this.left.sum + this.right.sum;
    }
    ```

**Range Query:**
Returns the sum of a range.

- **Code Example:**
    ```java
    public int rangeQuery(int L, int R) {
        if (L == this.L && R == this.R) {
            return this.sum;
        }

        int M = (this.L + this.R) / 2;
        if (L > M) {
            return this.right.rangeQuery(L, R);
        } else if (R <= M) {
            return this.left.rangeQuery(L, R);
        } else {
            return this.left.rangeQuery(L, M) + this.right.rangeQuery(M + 1, R);
        }
    }
    ```

**Time Complexity:**
- **Build: \(O(n)\)**
    - **Explanation:** Constructs the tree in linear time.
- **Update and Range Query: \(O(\log n)\)**
    - **Explanation:** Updates and queries take logarithmic time due to the tree height.

---

### Iterative DFS

#### Description
Depth-First Search (DFS) is a tree traversal algorithm that explores as far as possible along each branch before backtracking. Iterative DFS uses a stack instead of recursion to traverse the tree.

#### Operations

**Inorder Traversal:**
Visit the left subtree, the root node, and then the right subtree using a stack.

- **Code Example:**
    ```java
    public static void inorder(TreeNode root) {
        Stack<TreeNode> stack = new Stack<>();
        TreeNode curr = root;

        while (curr != null || !stack.isEmpty()) {
            if (curr != null) {
                stack.push(curr);
                curr = curr.left;
            } else {
                curr = stack.pop();
                System.out.println(curr.val);
                curr = curr.right;
            }
        }
    }
    ```

**Preorder Traversal:**
Visit the root node, the left subtree, and then the right subtree using a stack.

- **Code Example:**
    ```java
    public static void preorder(TreeNode root) {
        Stack<TreeNode> stack = new Stack<>();
        TreeNode curr = root;

        while (curr != null || !stack.isEmpty()) {
            if (curr != null) {
                System.out.println(curr.val);
                if (curr.right != null) {
                    stack.push(curr.right);
                }
                curr = curr.left;
            } else {
                curr = stack.pop();
            }
        }
    }
    ```

**Postorder Traversal:**
Visit the left subtree, the right subtree, and then the root node using two stacks.

- **Code Example:**
    ```java
    public static void postorder(TreeNode root) {
        Stack<TreeNode> stack = new Stack<>();
        stack.push(root);

        Stack<Boolean> visit = new Stack<>();
        visit.push(false);

        while (!stack.isEmpty()) {
            TreeNode curr = stack.pop();
            boolean visited = visit.pop();
            if (curr != null) {
                if (visited) {
                    System.out.println(curr.val);
                } else {
                    stack.push(curr);
                    visit.push(true);
                    stack.push(curr.right);
                    visit.push(false);
                    stack.push(curr.left);
                    visit.push(false);
                }
            }
        }
    }
    ```

**Time Complexity:**
- **Traversal: \(O(n)\)**
    - **Explanation:** Each node is visited exactly once.
 
---

### Heap Properties

#### Description
A heap is a specialized, tree-based data structure that is a complete binary tree. It implements the priority queue abstract data type, where elements are added and removed based on their priority.

#### Types of Heaps
1. **Min Heap:** The smallest value is at the root, and each parent node is smaller than or equal to its child nodes.
2. **Max Heap:** The largest value is at the root, and each parent node is larger than or equal to its child nodes.

#### Properties

**Structure Property:**
A binary heap is a complete binary tree, meaning every level of the tree is fully filled except possibly for the last level, which is filled from left to right.

**Order Property:**
- **Min Heap:** Every node's value is less than or equal to the values of its children.
- **Max Heap:** Every node's value is greater than or equal to the values of its children.

**Array Representation:**
Heaps are typically implemented using arrays. The left child of a node at index `i` is at index `2*i`, the right child is at index `2*i + 1`, and the parent is at index `i/2`.

- **Code Example:**
    ```java
    public class Heap {
        List<Integer> heap;

        public Heap() {
            heap = new ArrayList<>();
            heap.add(0); // Initialize heap with a dummy value at index 0
        }
    }
    ```

**Time Complexity:**
- **Insert, Delete: \(O(\log n)\)**
    - **Explanation:** Operations involve percolating up or down the tree, taking logarithmic time.

---

### Push and Pop

#### Description
Push and pop operations in a heap maintain the heap properties by ensuring that the structure and order properties are intact after each operation.

#### Operations

**Push:**
To insert an element into the heap, add the element at the end of the array and percolate it up to restore the heap order property.

- **Code Example:**
    ```java
    public void push(int val) {
        heap.add(val);
        int i = heap.size() - 1;

        // Percolate up
        while (i > 1 && heap.get(i) < heap.get(i / 2)) {
            int tmp = heap.get(i);
            heap.set(i, heap.get(i / 2));
            heap.set(i / 2, tmp);
            i = i / 2;
        }
    }
    ```

**Pop:**
To remove the root element (minimum in a min-heap or maximum in a max-heap), replace it with the last element in the array and percolate it down to restore the heap order property.

- **Code Example:**
    ```java
    public int pop() {
        if (heap.size() == 1) {
            // Handle empty heap case
            throw new NoSuchElementException("Heap is empty");
        }

        int res = heap.get(1); // Root element
        heap.set(1, heap.remove(heap.size() - 1)); // Move last element to root
        int i = 1;

        // Percolate down
        while (2 * i < heap.size()) {
            int child = 2 * i; // Left child
            if (child + 1 < heap.size() && heap.get(child + 1) < heap.get(child)) {
                child = child + 1; // Right child
            }
            if (heap.get(i) <= heap.get(child)) {
                break;
            }
            int tmp = heap.get(i);
            heap.set(i, heap.get(child));
            heap.set(child, tmp);
            i = child;
        }
        return res;
    }
    ```

**Time Complexity:**
- **Push, Pop: \(O(\log n)\)**
    - **Explanation:** Both operations involve percolating up or down the tree, taking logarithmic time.

---

### Heapify

#### Description
Heapify is a process used to build a heap from an arbitrary array. It ensures that the array satisfies the heap properties.

#### Operations

**Heapify:**
To build a heap, start from the last non-leaf node and percolate down each node to ensure the heap property is maintained.

- **Code Example:**
    ```java
    public void heapify(ArrayList<Integer> arr) {
        arr.add(arr.get(0)); // Move 0-th position to the end
        heap = arr;
        int cur = (heap.size() - 1) / 2;
        while (cur > 0) {
            int i = cur;
            while (2 * i < heap.size()) {
                if (2 * i + 1 < heap.size() && heap.get(2 * i + 1) < heap.get(2 * i) && heap.get(i) > heap.get(2 * i + 1)) {
                    int tmp = heap.get(i);
                    heap.set(i, heap.get(2 * i + 1));
                    heap.set(2 * i + 1, tmp);
                    i = 2 * i + 1;
                } else if (heap.get(i) > heap.get(2 * i)) {
                    int tmp = heap.get(i);
                    heap.set(i, heap.get(2 * i));
                    heap.set(2 * i, tmp);
                    i = 2 * i;
                } else {
                    break;
                }
            }
            cur--;
        }
    }
    ```

**Time Complexity:**
- **Heapify: \(O(n)\)**
    - **Explanation:** Although each percolate down operation takes \(O(\log n)\), the number of operations decreases exponentially, leading to a linear overall time complexity.

---

### Two Heaps

#### Description
Using two heaps (a min-heap and a max-heap) is a technique to efficiently solve problems like finding the median of a data stream. The max-heap stores the smaller half of the data, and the min-heap stores the larger half.

#### Operations

**Median Finder:**
Maintain two heaps such that the max-heap contains the smaller half of the numbers, and the min-heap contains the larger half. The median is either the root of one of the heaps or the average of the roots.

- **Code Example:**
    ```java
    import java.util.PriorityQueue;
    import java.util.Collections;

    public class MedianFinder {
        PriorityQueue<Integer> small; // Max-heap
        PriorityQueue<Integer> large; // Min-heap

        public MedianFinder() {
            small = new PriorityQueue<>(Collections.reverseOrder());
            large = new PriorityQueue<>();
        }

        public void insert(int num) {
            small.add(num);
            if (!small.isEmpty() && !large.isEmpty() && small.peek() > large.peek()) {
                large.add(small.poll());
            }
            if (small.size() > large.size() + 1) {
                large.add(small.poll());
            }
            if (large.size() > small.size() + 1) {
                small.add(large.poll());
            }
        }

        public double getMedian() {
            if (small.size() > large.size()) {
                return small.peek();
            } else if (large.size() > small.size()) {
                return large.peek();
            }
            return (small.peek() + large.peek()) / 2.0;
        }
    }
    ```

**Time Complexity:**
- **Insert: \(O(\log n)\)**
    - **Explanation:** Insertion involves adding the element to one of the heaps and possibly rebalancing, taking logarithmic time.
- **Get Median: \(O(1)\)**
    - **Explanation:** Retrieving the median is a constant time operation since it involves accessing the root of the heaps.

---

### Tree Maze

#### Description
The tree maze problem involves finding a path from the root of a binary tree to a leaf node without encountering any nodes with a value of zero. This problem is typically solved using depth-first search (DFS).

#### Operations

**DFS Approach:**
Perform a depth-first search from the root node. If you encounter a node with a value of zero, backtrack. If you reach a leaf node without encountering any zeros, return true.

- **Code Example:**
    ```java
    public boolean canReachLeaf(TreeNode root) {
        if (root == null || root.val == 0) {
            return false;
        }
        if (root.left == null && root.right == null) {
            return true;
        }
        if (canReachLeaf(root.left)) {
            return true;
        }
        return canReachLeaf(root.right);
    }
    ```

**Path Retrieval:**
To retrieve the path, use a list to store the nodes in the current path. Backtrack by removing nodes from the list if the path is invalid.

- **Code Example:**
    ```java
    public boolean leafPath(TreeNode root, ArrayList<Integer> path) {
        if (root == null || root.val == 0) {
            return false;
        }
        path.add(root.val);
        if (root.left == null && root.right == null) {
            return true;
        }
        if (leafPath(root.left, path)) {
            return true;
        }
        if (leafPath(root.right, path)) {
            return true;
        }
        path.remove(path.size() - 1);
        return false;
    }
    ```

**Time Complexity:**
- **DFS and Path Retrieval: \(O(n)\)**
    - **Explanation:** The algorithm visits each node exactly once.

---

### Subsets

#### Description
Subsets are all possible combinations of elements from a set where the order does not matter. The elements must be distinct.

#### Operations

**Generating Subsets:**
Use backtracking to explore all possible subsets by deciding whether to include each element.

- **Code Example:**
    ```java
    public static List<List<Integer>> subsetsWithoutDuplicates(int[] nums) {
        List<List<Integer>> subsets = new ArrayList<>();
        List<Integer> curSet = new ArrayList<>();
        helper(0, nums, curSet, subsets);
        return subsets;
    }

    public static void helper(int i, int[] nums, List<Integer> curSet, List<List<Integer>> subsets) {
        if (i >= nums.length) {
            subsets.add(new ArrayList<>(curSet));
            return;
        }
        // decision to include nums[i]
        curSet.add(nums[i]);
        helper(i + 1, nums, curSet, subsets);
        curSet.remove(curSet.size() - 1);
        // decision NOT to include nums[i]
        helper(i + 1, nums, curSet, subsets);
    }
    ```

**Time Complexity:**
- **Subsets: \(O(n \cdot 2^n)\)**
    - **Explanation:** Each element can be included or not included, resulting in \(2^n\) subsets. Each subset takes \(O(n)\) time to build.

---

### Combinations

#### Description
Combinations involve selecting elements from a set where the order does not matter, but the elements must be distinct. Typically, combinations have a fixed size \(k\).

#### Operations

**Generating Combinations:**
Use backtracking to explore all possible combinations of a given size \(k\) from a range of numbers.

- **Code Example:**
    ```java
    public static List<List<Integer>> combinations(int n, int k) {
        List<List<Integer>> combs = new ArrayList<>();
        helper(1, new ArrayList<>(), combs, n, k);
        return combs;
    }

    public static void helper(int i, List<Integer> curComb, List<List<Integer>> combs, int n, int k) {
        if (curComb.size() == k) {
            combs.add(new ArrayList<>(curComb));
            return;
        }
        if (i > n) {
            return;
        }
        // decision to include i
        curComb.add(i);
        helper(i + 1, curComb, combs, n, k);
        curComb.remove(curComb.size() - 1);
        // decision to NOT include i
        helper(i + 1, curComb, combs, n, k);
    }
    ```

**Time Complexity:**
- **Combinations: \(O(k \cdot C(n, k))\)**
    - **Explanation:** Generating each combination takes \(O(k)\) time, and there are \(C(n, k)\) combinations.

---

### Permutations

#### Description
Permutations are all possible arrangements of a set of distinct elements where the order matters. The number of permutations of \(n\) elements is \(n!\).

#### Operations

**Generating Permutations:**
Use backtracking to explore all possible permutations by swapping elements.

- **Code Example:**
    ```java
    public static List<List<Integer>> permutations(int[] nums) {
        List<List<Integer>> perms = new ArrayList<>();
        helper(0, nums, perms);
        return perms;
    }

    public static void helper(int i, int[] nums, List<List<Integer>> perms) {
        if (i == nums.length) {
            List<Integer> perm = new ArrayList<>();
            for (int num : nums) {
                perm.add(num);
            }
            perms.add(perm);
            return;
        }
        for (int j = i; j < nums.length; j++) {
            swap(nums, i, j);
            helper(i + 1, nums, perms);
            swap(nums, i, j);
        }
    }

    public static void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
    ```

**Time Complexity:**
- **Permutations: \(O(n \cdot n!)\)**
    - **Explanation:** There are \(n!\) permutations, and generating each permutation takes \(O(n)\) time.

---

### Introduction to Graphs

#### Description
A graph is a data structure consisting of nodes (vertices) connected by edges. Graphs are versatile structures used to represent various real-world problems, such as networks, social connections, and paths. 

#### Graph Terminology
- **Vertex (Node):** A fundamental part of a graph that can store data.
- **Edge:** A connection between two vertices. It can be directed or undirected.
- **Directed Graph:** Graph where edges have a direction, indicating the relationship flows from one vertex to another.
- **Undirected Graph:** Graph where edges have no direction, indicating a bidirectional relationship.
- **Adjacency Matrix:** A 2D array representation where each cell `(i, j)` indicates the presence of an edge between vertex `i` and vertex `j`.
- **Adjacency List:** A collection of lists or arrays, where each list represents a vertex and contains the vertices adjacent to it.

#### Formats of Graphs
1. **Matrix (2D Grid):**
   - **Code Example:**
     ```java
     int[][] grid = {
         {0, 0, 0, 0},
         {1, 1, 0, 0},
         {0, 0, 0, 1},
         {0, 1, 0, 0}
     };
     ```

2. **Adjacency Matrix:**
   - **Code Example:**
     ```java
     int[][] adjMatrix = {
         {0, 1, 0, 0},
         {1, 0, 1, 0},
         {0, 1, 0, 1},
         {0, 0, 1, 0}
     };
     ```

3. **Adjacency List:**
   - **Code Example:**
     ```java
     public class GraphNode {
         int val;
         List<GraphNode> neighbors;
         public GraphNode(int val) {
             this.val = val;
             this.neighbors = new ArrayList<GraphNode>();
         }
     }
     HashMap<Integer, List<Integer>> adjList = new HashMap<>();
     adjList.put(1, Arrays.asList(2, 3));
     adjList.put(2, Arrays.asList(1, 4));
     adjList.put(3, Arrays.asList(1, 4));
     adjList.put(4, Arrays.asList(2, 3));
     ```

**Time Complexity:**
- **Adjacency Matrix: \(O(V^2)\)**
  - **Explanation:** A square matrix of size \(V \times V\) is used, where \(V\) is the number of vertices.
- **Adjacency List: \(O(V + E)\)**
  - **Explanation:** Space depends on the number of vertices \(V\) and edges \(E\).

---

### Matrix DFS

#### Description
Depth-First Search (DFS) on a matrix is used to traverse and explore all nodes of a graph represented as a 2D grid. DFS explores as far as possible along each branch before backtracking.

#### Operations

**DFS Implementation:**
To implement DFS, start from a given cell and recursively visit all four possible directions (up, down, left, right) while marking visited cells to avoid re-visitation.

- **Code Example:**
    ```java
    public int dfs(int[][] grid, int r, int c, int[][] visit) {
        int ROWS = grid.length, COLS = grid[0].length;
        if (Math.min(r, c) < 0 || r >= ROWS || c >= COLS || visit[r][c] == 1 || grid[r][c] == 1) {
            return 0;
        }
        if (r == ROWS - 1 && c == COLS - 1) {
            return 1;
        }
        visit[r][c] = 1;
        int count = 0;
        count += dfs(grid, r + 1, c, visit);
        count += dfs(grid, r - 1, c, visit);
        count += dfs(grid, r, c + 1, visit);
        count += dfs(grid, r, c - 1, visit);
        visit[r][c] = 0;
        return count;
    }
    ```

**Time Complexity:**
- **DFS: \(O(n \cdot m)\)**
  - **Explanation:** In the worst case, DFS visits each cell in the \(n \times m\) grid exactly once.

---

### Matrix BFS

#### Description
Breadth-First Search (BFS) on a matrix is used to find the shortest path from a starting cell to a target cell in a grid. BFS explores all neighbors at the present depth level before moving on to nodes at the next depth level.

#### Operations

**BFS Implementation:**
To implement BFS, use a queue to traverse the grid level by level, starting from the source cell. Mark visited cells to avoid re-visitation.

- **Code Example:**
    ```java
    public int bfs(int[][] grid) {
        int ROWS = grid.length;
        int COLS = grid[0].length;
        int[][] visit = new int[ROWS][COLS];
        Deque<int[]> queue = new ArrayDeque<>();
        queue.add(new int[] {0, 0});
        visit[0][0] = 1;
        int length = 0;

        while (!queue.isEmpty()) {
            int queueLength = queue.size();
            for (int i = 0; i < queueLength; i++) {
                int[] pair = queue.poll();
                int r = pair[0], c = pair[1];
                if (r == ROWS - 1 && c == COLS - 1) {
                    return length;
                }
                int[][] neighbors = {{r, c + 1}, {r, c - 1}, {r + 1, c}, {r - 1, c}};
                for (int[] neighbor : neighbors) {
                    int newR = neighbor[0], newC = neighbor[1];
                    if (Math.min(newR, newC) < 0 || newR >= ROWS || newC >= COLS || visit[newR][newC] == 1 || grid[newR][newC] == 1) {
                        continue;
                    }
                    queue.add(neighbor);
                    visit[newR][newC] = 1;
                }
            }
            length++;
        }
        return -1; // Path not found
    }
    ```

**Time Complexity:**
- **BFS: \(O(n \cdot m)\)**
  - **Explanation:** Each cell in the \(n \times m\) grid is visited at most once.

---

### Adjacency List

#### Description
An adjacency list is a way of representing a graph using a list of lists or arrays. Each vertex in the graph has a list of adjacent vertices, making it a space-efficient way to represent sparse graphs.

#### Operations

**Building an Adjacency List:**
Given a list of edges, construct the adjacency list by mapping each vertex to its neighbors.

- **Code Example:**
    ```java
    public class GraphNode {
        int val;
        List<GraphNode> neighbors;
        public GraphNode(int val) {
            this.val = val;
            this.neighbors = new ArrayList<GraphNode>();
        }
    }
    HashMap<Integer, List<Integer>> adjList = new HashMap<>();
    String[][] edges = {{"A", "B"}, {"B", "C"}, {"B", "E"}, {"C", "E"}, {"E", "D"}};
    for (String[] edge : edges) {
        String src = edge[0], dst = edge[1];
        adjList.putIfAbsent(src, new ArrayList<>());
        adjList.putIfAbsent(dst, new ArrayList<>());
        adjList.get(src).add(dst);
    }
    ```

**DFS on Adjacency List:**
Perform DFS to explore all paths from a source to a destination.

- **Code Example:**
    ```java
    public int dfs(String node, String target, HashMap<String, ArrayList<String>> adjList, HashSet<String> visit) {
        if (visit.contains(node)) {
            return 0;
        }
        if (node.equals(target)) {
            return 1;
        }
        visit.add(node);
        int count = 0;
        for (String neighbor : adjList.get(node)) {
            count += dfs(neighbor, target, adjList, visit);
        }
        visit.remove(node);
        return count;
    }
    ```

**BFS on Adjacency List:**
Perform BFS to find the shortest path from a source to a destination.

- **Code Example:**
    ```java
    public int bfs(String node, String target, HashMap<String, ArrayList<String>> adjList) {
        int length = 0;
        HashSet<String> visit = new HashSet<>();
        Queue<String> queue = new LinkedList<>();
        visit.add(node);
        queue.add(node);

        while (!queue.isEmpty()) {
            int queueLength = queue.size();
            for (int i = 0; i < queueLength; i++) {
                String curr = queue.poll();
                if (curr.equals(target)) {
                    return length;
                }
                for (String neighbor : adjList.get(curr)) {
                    if (!visit.contains(neighbor)) {
                        visit.add(neighbor);
                        queue.add(neighbor);
                    }
                }
            }
            length++;
        }
        return length; // Path not found
    }
    ```

**Time Complexity:**
- **DFS and BFS: \(O(V + E)\)**
  - **Explanation:** The algorithms visit all vertices \(V\) and edges \(E\) in the graph.

---

### Dijkstra's Algorithm

#### Description
Dijkstra's algorithm is used to find the shortest paths from a source vertex to all other vertices in a weighted graph. Unlike BFS, which works only for unweighted graphs, Dijkstra's algorithm can handle graphs with varying edge weights. It prioritizes finding the "lightest" path, i.e., the path with the smallest total weight.

#### Operations

**Implementation:**
Dijkstra's algorithm uses a min-heap to keep track of the next vertex to visit based on the smallest known distance from the source.

- **Code Example:**
    ```java
    import java.util.*;

    public class Dijkstra {
        public static Map<Integer, Integer> shortestPath(int[][] edges, int n, int src) {
            Map<Integer, ArrayList<Integer[]>> adj = new HashMap<>();
            for (int i = 1; i <= n; i++) {
                adj.put(i, new ArrayList<>());
            }
            for (int[] edge : edges) {
                int s = edge[0], d = edge[1], w = edge[2];
                adj.get(s).add(new Integer[] {d, w});
            }

            HashMap<Integer, Integer> shortest = new HashMap<>();
            Queue<int[]> minHeap = new PriorityQueue<>((a, b) -> a[0] - b[0]);
            minHeap.add(new int[]{0, src});

            while (!minHeap.isEmpty()) {
                int[] cur = minHeap.poll();
                int weight = cur[0], node = cur[1];

                if (shortest.containsKey(node)) continue;
                shortest.put(node, weight);

                for (Integer[] neighbor : adj.get(node)) {
                    int nextNode = neighbor[0], nextWeight = neighbor[1];
                    if (!shortest.containsKey(nextNode)) {
                        minHeap.add(new int[]{weight + nextWeight, nextNode});
                    }
                }
            }
            return shortest;
        }
    }
    ```

**Time Complexity:**
- **Time Complexity: \(O(E \log V)\)**
  - **Explanation:** Each edge is processed at most once, and each operation on the min-heap (insert/remove) takes \(O(\log V)\).

---

### Prim's Algorithm

#### Description
Prim's algorithm is used to find the minimum spanning tree (MST) of a weighted undirected graph. It starts from an arbitrary node and grows the MST by adding the smallest edge that connects a vertex in the MST to a vertex outside the MST.

#### Operations

**Implementation:**
Prim's algorithm uses a min-heap to select the edge with the smallest weight that connects the growing MST to a new vertex.

- **Code Example:**
    ```java
    import java.util.*;

    public class Prim {
        public static List<int[]> mst(int[][] edges, int n) {
            Map<Integer, List<int[]>> adj = new HashMap<>();
            for (int i = 1; i <= n; i++) {
                adj.put(i, new ArrayList<>());
            }
            for (int[] edge : edges) {
                int u = edge[0], v = edge[1], w = edge[2];
                adj.get(u).add(new int[]{v, w});
                adj.get(v).add(new int[]{u, w});
            }

            Queue<int[]> minHeap = new PriorityQueue<>((a, b) -> a[0] - b[0]);
            List<int[]> mst = new ArrayList<>();
            Set<Integer> visited = new HashSet<>();
            visited.add(1);

            for (int[] neighbor : adj.get(1)) {
                minHeap.add(new int[]{neighbor[1], 1, neighbor[0]});
            }

            while (visited.size() < n) {
                int[] edge = minHeap.poll();
                int weight = edge[0], u = edge[1], v = edge[2];
                if (visited.contains(v)) continue;
                visited.add(v);
                mst.add(new int[]{u, v});

                for (int[] neighbor : adj.get(v)) {
                    if (!visited.contains(neighbor[0])) {
                        minHeap.add(new int[]{neighbor[1], v, neighbor[0]});
                    }
                }
            }
            return mst;
        }
    }
    ```

**Time Complexity:**
- **Time Complexity: \(O(E \log V)\)**
  - **Explanation:** Each edge is processed, and each operation on the min-heap takes \(O(\log V)\).

---

### Kruskal's Algorithm

#### Description
Kruskal's algorithm is another method for finding the minimum spanning tree (MST) of a graph. It sorts all edges by weight and adds them one by one to the MST, skipping edges that would form a cycle, until the MST includes all vertices.

#### Operations

**Implementation:**
Kruskal's algorithm uses a union-find data structure to detect cycles and manage the growing MST.

- **Code Example:**
    ```java
    import java.util.*;

    public class Kruskal {
        public static List<int[]> mst(int[][] edges, int n) {
            Arrays.sort(edges, Comparator.comparingInt(a -> a[2]));
            UnionFind uf = new UnionFind(n);
            List<int[]> mst = new ArrayList<>();

            for (int[] edge : edges) {
                int u = edge[0], v = edge[1], weight = edge[2];
                if (uf.union(u, v)) {
                    mst.add(new int[]{u, v});
                    if (mst.size() == n - 1) break;
                }
            }
            return mst;
        }
    }

    class UnionFind {
        int[] parent, rank;

        UnionFind(int size) {
            parent = new int[size + 1];
            rank = new int[size + 1];
            for (int i = 0; i <= size; i++) parent[i] = i;
        }

        boolean union(int u, int v) {
            int pu = find(u), pv = find(v);
            if (pu == pv) return false;
            if (rank[pu] > rank[pv]) {
                parent[pv] = pu;
            } else if (rank[pu] < rank[pv]) {
                parent[pu] = pv;
            } else {
                parent[pv] = pu;
                rank[pu]++;
            }
            return true;
        }

        int find(int u) {
            if (parent[u] != u) parent[u] = find(parent[u]);
            return parent[u];
        }
    }
    ```

**Time Complexity:**
- **Time Complexity: \(O(E \log E)\)**
  - **Explanation:** Sorting the edges takes \(O(E \log E)\), and the union-find operations take \(O(\log V)\) each.

---

### Topological Sort

#### Description
Topological sort is a linear ordering of vertices in a directed acyclic graph (DAG) such that for every directed edge \(u \rightarrow v\), vertex \(u\) comes before \(v\). It is used in scenarios where dependencies need to be resolved, such as task scheduling.

#### Operations

**Implementation:**
Topological sort can be implemented using DFS. Visit all nodes, and for each node, recursively visit all its neighbors before adding the node to the result.

- **Code Example:**
    ```java
    import java.util.*;

    public class TopologicalSort {
        public static List<Integer> topologicalSort(int[][] edges, int n) {
            Map<Integer, List<Integer>> adj = new HashMap<>();
            for (int i = 1; i <= n; i++) adj.put(i, new ArrayList<>());
            for (int[] edge : edges) adj.get(edge[0]).add(edge[1]);

            List<Integer> topSort = new ArrayList<>();
            Set<Integer> visited = new HashSet<>();

            for (int i = 1; i <= n; i++) {
                if (!visited.contains(i)) dfs(i, adj, visited, topSort);
            }

            Collections.reverse(topSort);
            return topSort;
        }

        private static void dfs(int node, Map<Integer, List<Integer>> adj, Set<Integer> visited, List<Integer> topSort) {
            if (visited.contains(node)) return;
            visited.add(node);
            for (int neighbor : adj.get(node)) dfs(neighbor, adj, visited, topSort);
            topSort.add(node);
        }
    }
    ```

**Time Complexity:**
- **Time Complexity: \(O(V + E)\)**
  - **Explanation:** Each vertex and each edge is processed exactly once.

---

### Bit Manipulation

#### Description
Bit manipulation is a technique used in computer science to directly operate on the binary representation of integers. It involves using bitwise operators to perform operations at the bit level. Bit manipulation is often used to optimize algorithms and solve problems more efficiently.

#### Common Bitwise Operations

1. **AND (`&`):**
   - **Operation:** `1 & 1 = 1`, `1 & 0 = 0`, `0 & 1 = 0`, `0 & 0 = 0`
   - **Use:** To check if a bit is set or to clear specific bits.

2. **OR (`|`):**
   - **Operation:** `1 | 1 = 1`, `1 | 0 = 1`, `0 | 1 = 1`, `0 | 0 = 0`
   - **Use:** To set specific bits.

3. **XOR (`^`):**
   - **Operation:** `1 ^ 1 = 0`, `1 ^ 0 = 1`, `0 ^ 1 = 1`, `0 ^ 0 = 0`
   - **Use:** To toggle specific bits or detect changes.

4. **NOT (`~`):**
   - **Operation:** `~1 = 0`, `~0 = 1`
   - **Use:** To invert all bits in a binary representation.

5. **Left Shift (`<<`):**
   - **Operation:** Shifts bits to the left, filling with zeros on the right. Equivalent to multiplying by 2.
   - **Example:** `001 << 1 = 010`

6. **Right Shift (`>>`):**
   - **Operation:** Shifts bits to the right, filling with zeros on the left. Equivalent to dividing by 2.
   - **Example:** `010 >> 1 = 001`

#### Demonstration

**Example Problem: Count the Number of 1 Bits**

To count the number of 1 bits in the binary representation of an integer, use a loop to check each bit and shift the integer to the right until all bits are processed.

- **Code Example:**
    ```java
    public static int countBits(int n) {
        int count = 0;
        while (n > 0) {
            if ((n & 1) == 1) {
                count++;
            }
            n = n >> 1; // same as n / 2
        }
        return count;
    }
    ```

**Example:**
For the integer `23` (binary representation `10111`):
- First bit (`1`): Increment count, shift right (`01011`)
- Second bit (`1`): Increment count, shift right (`00101`)
- Third bit (`1`): Increment count, shift right (`00010`)
- Fourth bit (`0`): Shift right (`00001`)
- Fifth bit (`1`): Increment count, shift right (`00000`)

Final count is `4`.

**Time Complexity:**
- **Bit Manipulation: \(O(\log n)\)**
  - **Explanation:** The operations involve iterating over each bit, leading to logarithmic time complexity based on the number of bits in the integer.

---

### Truth Tables and Bit Operations

**AND Operation:**
- **Example:**
    ```java
    int n = 1 & 1; // Result: 1
    ```

**OR Operation:**
- **Example:**
    ```java
    int n = 1 | 0; // Result: 1
    ```

**XOR Operation:**
- **Example:**
    ```java
    int n = 0 ^ 1; // Result: 1
    ```

**NOT Operation:**
- **Example:**
    ```java
    int n = ~n; // Inverts all bits in n
    ```

**Bit Shifting:**
- **Left Shift:**
    ```java
    int n = 1;
    n = n << 1; // Result: 2 (binary 10)
    ```
- **Right Shift:**
    ```java
    int n = 2;
    n = n >> 1; // Result: 1 (binary 1)
    ```

**Time Complexity:**
- **Bitwise AND, OR, XOR, NOT, Shifts: \(O(1)\)**
  - **Explanation:** Each operation works directly on the binary representation and takes constant time.

---

### Applications

**Number of 1 Bits (Hamming Weight):**
- **Problem:** Count the number of 1 bits in an integer.
- **Code Example:**
    ```java
    public static int hammingWeight(int n) {
        int count = 0;
        while (n != 0) {
            n &= (n - 1); // Clear the least significant bit set
            count++;
        }
        return count;
    }
    ```

**Counting Bits:**
- **Problem:** Count the number of 1 bits in all numbers from `0` to `n`.
- **Code Example:**
    ```java
    public static int[] countBits(int num) {
        int[] res = new int[num + 1];
        for (int i = 1; i <= num; i++) {
            res[i] = res[i >> 1] + (i & 1);
        }
        return res;
    }
    ```

**Reverse Bits:**
- **Problem:** Reverse the bits of a given 32-bit unsigned integer.
- **Code Example:**
    ```java
    public static int reverseBits(int n) {
        int result = 0;
        for (int i = 0; i < 32; i++) {
            result <<= 1;
            if ((n & 1) == 1) {
                result++;
            }
            n >>= 1;
        }
        return result;
    }
    ```

**Time Complexity:**
- **Number of 1 Bits (Hamming Weight), Counting Bits, Reverse Bits: \(O(\log n)\)**
  - **Explanation:** Each operation iterates over the bits of the integer, resulting in logarithmic time complexity based on the number of bits.

---
