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

