---
# Data Structures and Design Algorithms
---

1. [Arrays](#arrays)
2. [Stacks](#stacks)
3. [Queues](#queues)
4. [Hash Maps](#hash-maps)
5. [Sliding Window](#sliding-window)
6. [Two Pointers](#two-pointers)
7. [Prefix Sum](#prefix-sum)
8. [Linked Lists](#linked-lists)
9. [Sorting](#sorting)
10. [Binary Search](#binary-search)
11. [Trees](#trees)
12. [Heaps](#heaps)
13. [Backtracking](#backtracking)
14. [Graphs](#graphs)
15. [Bit Manipulation](#bit-manipulation)
16. [Dynamic Programming (DP)](#dynamic-programming-dp)
---
## ARRAYS
---
1. [Remove Duplicates From Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) - Easy
2. [Remove Element](https://leetcode.com/problems/remove-element/) - Easy
3. [Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/) - Easy
4. [Reverse String](https://leetcode.com/problems/reverse-string/) - Easy
5. [Valid Anagram](https://leetcode.com/problems/valid-anagram/) - Easy
6. [Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/) - Easy
7. [Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/) - Medium
8. [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/) - Medium
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
**Time Complexity:**
- **Reading:** O(1)
  - **Explanation:** Accessing an element by index is a constant time operation.
- **Insert at End (Static Array):** O(1) if within capacity
  - **Explanation:** Inserting at the end is a constant time operation if there is space.
- **Remove from End:** O(1)
  - **Explanation:** Removing the last element is a constant time operation.
- **Insert at Index:** O(n)
  - **Explanation:** Inserting at a specific index requires shifting elements to the right.
- **Remove at Index:** O(n)
  - **Explanation:** Removing an element at a specific index requires shifting elements to the left.
- **Push Back (Dynamic Array):** Amortized O(1)
  - **Explanation:** Inserting an element at the end is generally O(1), but resizing can cause occasional O(n) operations.
- **Resize:** O(n)
  - **Explanation:** Resizing involves copying all elements to a new array, which takes linear time.

---
## STACKS
---
1. [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) - Easy
2. [Baseball Game](https://leetcode.com/problems/baseball-game/) - Easy
3. [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/) - Easy
4. [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/) - Medium
5. [Remove All Adjacent Duplicates in String II](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string-ii/) - Medium
6. [Min Stack](https://leetcode.com/problems/min-stack/) - Medium
---

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
**Time Complexity:**
- **Push, Pop, Peek:** O(1)
   - **Explanation:** These operations are performed at the top of the stack and do not require iteration through the elements, resulting in constant time complexity.

---
## QUEUES
---
1. [Number of Students Unable to Eat Lunch](https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/) - Easy
2. [Dota2 Senate](https://leetcode.com/problems/dota2-senate/) - Medium
---

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
**Time Complexity:**
- **Enqueue, Dequeue:** O(1)
   - **Explanation:** These operations involve adding or removing elements from the ends of the queue, which can be done in constant time without iterating through other elements.

---
## HASH MAPS
---
### Leetcode
1. [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) - Easy
2. [Two Sum](https://leetcode.com/problems/two-sum/) - Easy
3. [LRU Cache](https://leetcode.com/problems/lru-cache/) - Medium
4. [Group Anagrams](https://leetcode.com/problems/group-anagrams/) - Medium
5. [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/) - Medium
6. [Encode and Decode Strings](https://leetcode.com/problems/encode-and-decode-strings/) - Medium
7. [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) - Medium
---

### Hash Usage

#### Description
Hash maps and hash sets are fundamental data structures used for fast access and retrieval of data. They are based on hashing, which allows for nearly constant time complexity for search, insert, and delete operations. Hash maps store key-value pairs, while hash sets store unique elements.

---

### Command Cheat Sheet
1. [Creating a Map](#1-creating-a-map)
2. [Inserting Key-Value Pairs](#2-inserting-key-value-pairs)
3. [Accessing Values](#3-accessing-values)
4. [Checking Key Existence](#4-checking-key-existence)
5. [Checking Value Existence](#5-checking-value-existence)
6. [Removing Key-Value Pairs](#6-removing-key-value-pairs)
7. [Iterating Through a Map](#7-iterating-through-a-map)
8. [Getting Keys or Values](#8-getting-keys-or-values)
9. [Getting Map Size](#9-getting-map-size)
10. [Clearing the Map](#10-clearing-the-map)
11. [Checking if the Map is Empty](#11-checking-if-the-map-is-empty)
12. [Replacing a Value](#12-replacing-a-value)
13. [Merging Maps](#13-merging-maps)
14. [Computing a Value](#14-computing-a-value)
15. [Getting Default Values](#15-getting-default-values)
16. [Conditional Removal](#16-conditional-removal)

---

### 1. Creating a Map

```java
import java.util.*;

Map<Integer, String> map = new HashMap<>(); // Creates a HashMap
Map<Integer, String> treeMap = new TreeMap<>(); // Creates a TreeMap (sorted order)
Map<Integer, String> linkedMap = new LinkedHashMap<>(); // Maintains insertion order
```

---

### 2. Inserting Key-Value Pairs

```java
map.put(1, "Apple");
map.put(2, "Banana");
map.put(3, "Cherry");
```

---

### 3. Accessing Values

```java
String value = map.get(1); // Returns "Apple"
System.out.println(value); // Output: Apple
```

---

### 4. Checking Key Existence

```java
if (map.containsKey(2)) {
    System.out.println("Key 2 exists");
}
```

---

### 5. Checking Value Existence

```java
if (map.containsValue("Banana")) {
    System.out.println("Banana exists");
}
```

---

### 6. Removing Key-Value Pairs

```java
map.remove(2); // Removes the key 2 and its associated value
System.out.println(map); // Output: {1=Apple, 3=Cherry}
```

---

### 7. Iterating Through a Map

### Using `entrySet()`:
```java
for (Map.Entry<Integer, String> entry : map.entrySet()) {
    System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
}
```

### Using `keySet()`:
```java
for (Integer key : map.keySet()) {
    System.out.println("Key: " + key + ", Value: " + map.get(key));
}
```

### Using `forEach()` (Java 8+):
```java
map.forEach((key, value) -> {
    System.out.println("Key: " + key + ", Value: " + value);
});
```

---

### 8. Getting Keys or Values

```java
Set<Integer> keys = map.keySet(); // Get all keys
Collection<String> values = map.values(); // Get all values

System.out.println(keys); // Output: [1, 3]
System.out.println(values); // Output: [Apple, Cherry]
```

---

### 9. Getting Map Size

```java
System.out.println("Map size: " + map.size()); // Output: 2
```

---

### 10. Clearing the Map

```java
map.clear();
System.out.println(map); // Output: {}
```

---

### 11. Checking if the Map is Empty

```java
if (map.isEmpty()) {
    System.out.println("The map is empty");
}
```

---

### 12. Replacing a Value

```java
map.put(1, "Apple");
map.replace(1, "Apricot"); // Replaces "Apple" with "Apricot"
System.out.println(map); // Output: {1=Apricot}
```

---

### 13. Merging Maps

```java
Map<Integer, String> anotherMap = new HashMap<>();
anotherMap.put(4, "Date");
anotherMap.put(5, "Elderberry");

map.putAll(anotherMap);
System.out.println(map); // Output: {1=Apricot, 4=Date, 5=Elderberry}
```

---

### 14. Computing a Value

```java
map.compute(1, (key, val) -> val + " Pie"); // Appends " Pie" to the value
System.out.println(map); // Output: {1=Apricot Pie}
```

---

### 15. Getting Default Values

```java
String value = map.getOrDefault(6, "Not Found");
System.out.println(value); // Output: Not Found
```

---

### 16. Conditional Removal

```java
map.put(6, "Fig");
map.remove(6, "Fig"); // Removes the entry only if the value is "Fig"
```

---

## Practice Problems:

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

---

## Time Complexities

### **Insert**
- **Average Case:** \( O(1) \)
- **Worst Case:** \( O(n) \)

**Explanation:**
- **Average Case \( O(1) \):** The hash function maps the key to an index, and the value is stored at that index. With minimal collisions, this operation is constant time.
- **Worst Case \( O(n) \):** If many keys hash to the same index (collisions), a linear search through the bucket or multiple probes (open addressing) is required.

---

### **Delete**
- **Average Case:** \( O(1) \)
- **Worst Case:** \( O(n) \)

**Explanation:**
- **Average Case \( O(1) \):** The hash function calculates the index, and the key-value pair is removed directly from the table.
- **Worst Case \( O(n) \):** In case of collisions, finding the key may involve traversing a long list (separate chaining) or probing multiple slots (open addressing).

---

### **Search (Lookup)**
- **Average Case:** \( O(1) \)
- **Worst Case:** \( O(n) \)

**Explanation:**
- **Average Case \( O(1) \):** The hash function calculates the index, and the value is retrieved directly from the table.
- **Worst Case \( O(n) \):** When many keys collide, the search operation must traverse a long bucket or probe through slots, leading to linear time.

---

## Summary Table

| Operation | Average Time Complexity | Worst Time Complexity |
|-----------|--------------------------|------------------------|
| **Insert** | \( O(1) \)              | \( O(n) \)            |
| **Delete** | \( O(1) \)              | \( O(n) \)            |
| **Search** | \( O(1) \)              | \( O(n) \)            |

---
## SLIDING WINDOW
---
1. [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) - Easy
2. [Contains Duplicate II (Fixed Size)](https://leetcode.com/problems/contains-duplicate-ii/) - Easy
3. [Longest Substring Without Repeating Characters (Variable Size)](https://leetcode.com/problems/longest-substring-without-repeating-characters/) - Medium
4. [Longest Repeating Character Replacement (Variable Size)](https://leetcode.com/problems/longest-repeating-character-replacement/) - Medium
5. [Number of Sub Arrays of Size K and Avg Greater… (Fixed Size)](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/) - Medium
6. [Minimum Size Subarray Sum (Variable Size)](https://leetcode.com/problems/minimum-size-subarray-sum/) - Medium
---

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
**Time Complexity:**
- **Fixed Size Sliding Window Operations:** O(n)
  - **Explanation:** The algorithm maintains a window of fixed size and iterates through the array once, ensuring linear time complexity.

- **Variable Size Sliding Window Operations:** O(n)
  - **Explanation:** The algorithm adjusts the window size dynamically while iterating through the array once, resulting in linear time complexity.


---
## TWO POINTERS
---
1. [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/) - Easy
2. [Two Sum II Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) - Medium
3. [3Sum](https://leetcode.com/problems/3sum/) - Medium
4. [Container With Most Water](https://leetcode.com/problems/container-with-most-water/) - Medium
5. [Remove Duplicates From Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) - Easy
6. [Remove Duplicates From Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/) - Medium
---

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
**Time Complexity:**
- **Valid Palindrome:** O(n)
  - **Explanation:** The algorithm iterates through the string once, comparing characters from both ends.
  - 
- **Two Sum II:** O(n)
  - **Explanation:** The algorithm uses two pointers to iterate through the array, ensuring each element is checked once.

---
## PREFIX SUM
---
1. [Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/) - Easy
2. [Find Pivot Index](https://leetcode.com/problems/find-pivot-index/) - Easy
3. [Find the Highest Altitude](https://leetcode.com/problems/find-the-highest-altitude/) - Easy
4. [Range Sum Query 2D Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/) - Medium
5. [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) - Medium
6. [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) - Medium
---

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
**Time Complexity:**
- **Building the Prefix Sum Array:** O(n)
  - **Explanation:** The algorithm iterates through the array once to compute the cumulative sums.
- **Range Sum Query:** O(1)
  - **Explanation:** The range sum query uses the precomputed prefix sums to answer the query in constant time.

---
## LINKED LISTS
---
1. [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) - Easy
2. [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) - Easy
3. [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) - Easy
4. [Reorder List](https://leetcode.com/problems/reorder-list/) - Medium
5. [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) - Medium
6. [Design Linked List](https://leetcode.com/problems/design-linked-list/) - Medium
7. [Design Browser History](https://leetcode.com/problems/design-browser-history/) - Medium
---
### LINKED LISTS (DESIGN LEVEL)
---
#### Fast and Slow Pointers
1. [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) - Easy
2. [Maximum Twin Sum Of A Linked List](https://leetcode.com/problems/maximum-twin-sum-of-a-linked-list/) - Medium
3. [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) - Easy
4. [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/) - Medium
5. [Find The Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/) - Medium
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

---

### Fast and Slow Pointers (DESIGN)

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
**Time Complexity:**
- **Creating a Singly Linked List:** O(1)
  - **Explanation:** Creating each `ListNode` object is a constant time operation.
- **Traversal:** O(n)
  - **Explanation:** The algorithm iterates through each node in the list.
- **Appending:** O(n)
  - **Explanation:** The algorithm must traverse the list to find the last node.
- **Deletion:** O(1) for deleting a known node, O(n) for finding and deleting a node
  - **Explanation:** Updating pointers is a constant time operation, but finding the node to delete can take linear time.
- **Finding the Middle:** O(n)
  - **Explanation:** The algorithm iterates through the list with two pointers.
- **Cycle Detection:** O(n)
  - **Explanation:** The algorithm iterates through the list with two pointers.

---
## SORTING
---
#### Insertion Sort
1. [Sort an Array](https://leetcode.com/problems/sort-an-array/) - Medium

#### Merge Sort
1. [Sort an Array](https://leetcode.com/problems/sort-an-array/) - Medium
2. [Merge K Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) - Hard

#### Quick Sort
1. [Sort an Array](https://leetcode.com/problems/sort-an-array/) - Medium
2. [Kth Largest Element In An Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) - Medium

#### Bucket Sort
1. [Sort Colors](https://leetcode.com/problems/sort-colors/) - Medium
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
## BINARY SEARCH
---
1. [Binary Search](https://leetcode.com/problems/binary-search/) - Easy
2. [Guess Number Higher Or Lower](https://leetcode.com/problems/guess-number-higher-or-lower/) - Easy
3. [First Bad Version](https://leetcode.com/problems/first-bad-version/) - Easy
4. [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) - Medium
5. [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) - Medium
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
## TREES
---
#### Binary Search Tree
1. [Search In A Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/) - Easy
2. [Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree/) - Medium
3. [Delete Node in a BST](https://leetcode.com/problems/delete-node-in-a-bst/) - Medium

#### Depth-First Search
1. [Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/) - Easy
2. [Kth Smallest Element In a Bst](https://leetcode.com/problems/kth-smallest-element-in-a-bst/) - Medium
3. [Construct Binary Tree From Preorder And Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/) - Medium
4. [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/) (both DFS and BFS) - Easy
5. [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) (both DFS and BFS) - Easy
6. [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/) - Easy
7. [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/) (both DFS and BFS) - Easy
8. [Same Tree](https://leetcode.com/problems/same-tree/) - Easy

#### Breadth-First Search
1. [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/) - Medium
2. [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/) - Medium
---
### TREES (DESIGN LEVEL)
---
#### Trie
1. [Implement Trie Prefix Tree](https://leetcode.com/problems/implement-trie-prefix-tree/) - Medium
2. [Design Add And Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/) - Medium
3. [Word Search II](https://leetcode.com/problems/word-search-ii/) - Hard
4. [Prefix And Suffix Search](https://leetcode.com/problems/prefix-and-suffix-search/) - Hard

#### Union-Find
1. [Redundant Connection](https://leetcode.com/problems/redundant-connection/) - Medium
2. [Accounts Merge](https://leetcode.com/problems/accounts-merge/) - Medium
3. [Number of Connected Components In An Undirected Graph](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/) - Medium
4. [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) - Medium

#### Segment Tree
1. [Range Sum Query Mutable](https://leetcode.com/problems/range-sum-query-mutable/) - Medium
2. [Queue Reconstruction By Height](https://leetcode.com/problems/queue-reconstruction-by-height/) - Medium
3. [My Calendar I](https://leetcode.com/problems/my-calendar-i/) - Medium
4. [Longest Increasing Subsequence II](https://leetcode.com/problems/longest-increasing-subsequence-ii/) - Hard

#### Iterative DFS
1. [Binary Search Tree Iterator](https://leetcode.com/problems/binary-search-tree-iterator/) - Medium
2. [Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/) - Easy
3. [Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/) - Easy
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

### Trie (DESIGN)

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

### Union-Find (DESIGN)

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

### Segment Tree (DESIGN)

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

### Iterative DFS (DESIGN)

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
## HEAPS
---
1. [Kth Largest Element in a Stream](https://leetcode.com/problems/kth-largest-element-in-a-stream/) - Easy
2. [Last Stone Weight](https://leetcode.com/problems/last-stone-weight/) - Easy
3. [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) - Medium
4. [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/) - Medium
---
### HEAPS (DESIGN LEVEL)
---
#### Two Heaps
1. [Find Median From Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) - Hard
2. [Sliding Window Median](https://leetcode.com/problems/sliding-window-median/) - Hard
3. [IPO](https://leetcode.com/problems/ipo/) - Hard
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

### Two Heaps (DESIGN)

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
### BACKTRACKING
---
1. [Path Sum](https://leetcode.com/problems/path-sum/) - Easy
2. [Subsets](https://leetcode.com/problems/subsets/) - Medium
3. [Combination Sum](https://leetcode.com/problems/combination-sum/) - Medium
---
### BACKTRACKING (DESIGN LEVEL)
---
#### Subsets
1. [Subsets](https://leetcode.com/problems/subsets/) - Medium
2. [Subsets II](https://leetcode.com/problems/subsets-ii/) - Medium

#### Combinations
1. [Combinations](https://leetcode.com/problems/combinations/) - Medium
2. [Combination Sum](https://leetcode.com/problems/combination-sum/) - Medium
3. [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/) - Medium

#### Permutations
1. [Permutations](https://leetcode.com/problems/permutations/) - Medium
2. [Permutations II](https://leetcode.com/problems/permutations-ii/) - Medium
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

### Subsets (DESIGN)

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

### Combinations (DESIGN)

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

### Permutations (DESIGN)

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
## GRAPHS
---
#### Matrix DFS
1. [Number of Islands](https://leetcode.com/problems/number-of-islands/) - Medium
2. [Max Area of Island](https://leetcode.com/problems/max-area-of-island/) - Medium

#### Matrix BFS
1. [Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/) - Medium
2. [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) - Medium

#### Adjacency List
1. [Clone Graph](https://leetcode.com/problems/clone-graph/) - Medium
2. [Pacific Atlantic Water Flow](https://leetcode.com/problems/pacific-atlantic-water-flow/) - Medium
3. [Surrounded Regions](https://leetcode.com/problems/surrounded-regions/) - Medium
4. [Number of Connected Components In An Undirected Graph](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/) - Medium
---
### Greedy Algorithms (Graphs+)
---
#### Dijkstra’s Algorithm
1. [Network Delay Time](https://leetcode.com/problems/network-delay-time/) - Medium
2. [Swim In Rising Water](https://leetcode.com/problems/swim-in-rising-water/) - Hard
3. [Path with Maximum Probability](https://leetcode.com/problems/path-with-maximum-probability/) - Medium

#### Prim’s Algorithm
1. [Min Cost to Connect All Points](https://leetcode.com/problems/min-cost-to-connect-all-points/) - Medium
2. [Find Critical and Pseudo Critical Edges](https://leetcode.com/problems/find-critical-and-pseudo-critical-edges-in-minimum-spanning-tree/) - Hard

#### Kruskal’s Algorithm
1. [Min Cost to Connect All Points](https://leetcode.com/problems/min-cost-to-connect-all-points/) - Medium
2. [Find Critical and Pseudo Critical Edges](https://leetcode.com/problems/find-critical-and-pseudo-critical-edges-in-minimum-spanning-tree/) - Hard

#### Topological Sort
1. [Course Schedule](https://leetcode.com/problems/course-schedule/) - Medium
2. [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/) - Medium
3. [Course Schedule IV](https://leetcode.com/problems/course-schedule-iv/) - Medium
4. [Sort Items By Groups Respecting Dependencies](https://leetcode.com/problems/sort-items-by-groups-respecting-dependencies/) - Hard
5. [Alien Dictionary](https://leetcode.com/problems/alien-dictionary/) - Hard
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

### Dijkstra's Algorithm (DESIGN)

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

### Prim's Algorithm (DESIGN)

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

### Kruskal's Algorithm (DESIGN)

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

### Topological Sort (DESIGN)

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
## BIT MANIPULATION
---
1. [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/) - Easy
2. [Counting Bits](https://leetcode.com/problems/counting-bits/) - Easy
3. [Reverse Bits](https://leetcode.com/problems/reverse-bits/) - Easy
4. [Missing Number](https://leetcode.com/problems/missing-number/) - Easy
5. [Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/) - Medium
---

### Bit Operations

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
## DYNAMIC PROGRAMMING (DP)
---
#### 1-Dimension DP
1. [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) - Easy
2. [House Robber](https://leetcode.com/problems/house-robber/) - Medium

#### 2-Dimension DP
1. [Unique Paths](https://leetcode.com/problems/unique-paths/) - Medium
2. [Unique Paths II](https://leetcode.com/problems/unique-paths-ii/) - Medium
3. [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/) - Medium

#### 0 / 1 Knapsack
1. [Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/) - Medium
2. [Target Sum](https://leetcode.com/problems/target-sum/) - Medium
3. [Ones and Zeroes](https://leetcode.com/problems/ones-and-zeroes/) - Medium
4. [Last Stone Weight II](https://leetcode.com/problems/last-stone-weight-ii/) - Medium

#### Unbounded Knapsack
1. [Coin Change](https://leetcode.com/problems/coin-change/) - Medium
2. [Minimum Cost For Tickets](https://leetcode.com/problems/minimum-cost-for-tickets/) - Medium
3. [Coin Change II](https://leetcode.com/problems/coin-change-ii/) - Medium

#### Longest Common Subsequence (LCS)
1. [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/) - Medium
2. [Distinct Subsequences](https://leetcode.com/problems/distinct-subsequences/) - Hard
3. [Edit Distance](https://leetcode.com/problems/edit-distance/) - Medium
4. [Interleaving String](https://leetcode.com/problems/interleaving-string/) - Medium
5. [Shortest Common Supersequence](https://leetcode.com/problems/shortest-common-supersequence/) - Hard

#### Palindromes
1. [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/) - Medium
2. [Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/) - Medium
3. [Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/) - Medium
---

### 1-Dimension DP

#### Description
One-dimensional dynamic programming (1D DP) is a technique to solve problems by breaking them down into simpler subproblems, where the solutions are stored in a 1D array to avoid redundant calculations.

#### Common Problems

**Climbing Stairs:**
- **Problem:** Given `n` steps, each time you can climb 1 or 2 steps, find the number of distinct ways to reach the top.
- **Code Example:**
    ```java
    public int climbStairs(int n) {
        if (n == 1) return 1;
        int[] dp = new int[n + 1];
        dp[1] = 1;
        dp[2] = 2;
        for (int i = 3; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        return dp[n];
    }
    ```
- **Time Complexity: \(O(n)\)**
- **Space Complexity: \(O(n)\)**

**House Robber:**
- **Problem:** Given an array representing the amount of money of each house, determine the maximum amount you can rob tonight without alerting the police (you cannot rob two adjacent houses).
- **Code Example:**
    ```java
    public int rob(int[] nums) {
        if (nums.length == 0) return 0;
        if (nums.length == 1) return nums[0];
        int[] dp = new int[nums.length];
        dp[0] = nums[0];
        dp[1] = Math.max(nums[0], nums[1]);
        for (int i = 2; i < nums.length; i++) {
            dp[i] = Math.max(dp[i - 1], dp[i - 2] + nums[i]);
        }
        return dp[nums.length - 1];
    }
    ```
- **Time Complexity: \(O(n)\)**
- **Space Complexity: \(O(n)\)**

---

### 2-Dimension DP

#### Description
Two-dimensional dynamic programming (2D DP) extends 1D DP to solve problems that can be represented in a grid or table format. It involves creating a 2D array to store intermediate results.

#### Common Problems

**Unique Paths:**
- **Problem:** Given a `m x n` grid, find the number of unique paths from the top-left corner to the bottom-right corner, moving only down or right.
- **Code Example:**
    ```java
    public int uniquePaths(int m, int n) {
        int[][] dp = new int[m][n];
        for (int i = 0; i < m; i++) dp[i][0] = 1;
        for (int j = 0; j < n; j++) dp[0][j] = 1;
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
            }
        }
        return dp[m - 1][n - 1];
    }
    ```
- **Time Complexity: \(O(m \cdot n)\)**
- **Space Complexity: \(O(m \cdot n)\)**

**Longest Common Subsequence:**
- **Problem:** Given two strings, find the length of their longest common subsequence.
- **Code Example:**
    ```java
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length(), n = text2.length();
        int[][] dp = new int[m + 1][n + 1];
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        return dp[m][n];
    }
    ```
- **Time Complexity: \(O(m \cdot n)\)**
- **Space Complexity: \(O(m \cdot n)\)**

---

### 0/1 Knapsack (DESIGN)

#### Description
The 0/1 knapsack problem involves selecting items with given weights and values to maximize the total value without exceeding the weight limit. Each item can be included or excluded (0/1).

#### Operations

**Implementation:**
Use a 2D array to store the maximum value at each n-th item and capacity c.

- **Code Example:**
    ```java
    public int knapsack(int[] weights, int[] values, int W) {
        int n = weights.length;
        int[][] dp = new int[n + 1][W + 1];
        for (int i = 1; i <= n; i++) {
            for (int w = 0; w <= W; w++) {
                if (weights[i - 1] <= w) {
                    dp[i][w] = Math.max(dp[i - 1][w], dp[i - 1][w - weights[i - 1]] + values[i - 1]);
                } else {
                    dp[i][w] = dp[i - 1][w];
                }
            }
        }
        return dp[n][W];
    }
    ```
- **Time Complexity: \(O(n \cdot W)\)**
- **Space Complexity: \(O(n \cdot W)\)**

---

### Unbounded Knapsack (DESIGN)

#### Description
The unbounded knapsack problem allows for an unlimited number of each item. The goal is to maximize the total value without exceeding the weight limit.

#### Operations

**Implementation:**
Use a 1D array to store the maximum value at each capacity c, iterating through items and capacities.

- **Code Example:**
    ```java
    public int unboundedKnapsack(int[] weights, int[] values, int W) {
        int[] dp = new int[W + 1];
        for (int w = 0; w <= W; w++) {
            for (int i = 0; i < weights.length; i++) {
                if (weights[i] <= w) {
                    dp[w] = Math.max(dp[w], dp[w - weights[i]] + values[i]);
                }
            }
        }
        return dp[W];
    }
    ```
- **Time Complexity: \(O(n \cdot W)\)**
- **Space Complexity: \(O(W)\)**

---

### Longest Common Subsequence (LCS) (DESIGN)

#### Description
The longest common subsequence problem finds the longest subsequence present in both given sequences where order is preserved.

#### Operations

**Implementation:**
Use a 2D array to store the lengths of LCS for substrings.

- **Code Example:**
    ```java
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length(), n = text2.length();
        int[][] dp = new int[m + 1][n + 1];
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        return dp[m][n];
    }
    ```
- **Time Complexity: \(O(m \cdot n)\)**
- **Space Complexity: \(O(m \cdot n)\)**

---

### Palindromes (DESIGN)

#### Description
Dynamic programming can be used to solve problems related to palindromes, such as finding the longest palindromic substring or counting palindromic substrings.

#### Common Problems

**Longest Palindromic Substring:**
- **Problem:** Find the longest palindromic substring in a given string.
- **Code Example:**
    ```java
    public String longestPalindrome(String s) {
        if (s == null || s.length() < 1) return "";
        int start = 0, end = 0;
        for (int i = 0; i < s.length(); i++) {
            int len1 = expandAroundCenter(s, i, i);
            int len2 = expandAroundCenter(s, i, i + 1);
            int len = Math.max(len1, len2);
            if (len > end - start) {
                start = i - (len - 1) / 2;
                end = i + len / 2;
            }
        }
        return s.substring(start, end + 1);
    }

    private int expandAroundCenter(String s, int left, int right) {
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            left--;
            right++;
        }
        return right - left - 1;
    }
    ```
- **Time Complexity: \(O(n^2)\)**
- **Space Complexity: \(O(1)\)**

**Palindromic Substrings:**
- **Problem:** Count the

 number of palindromic substrings in a given string.
- **Code Example:**
    ```java
    public int countSubstrings(String s) {
        int n = s.length(), count = 0;
        boolean[][] dp = new boolean[n][n];
        for (int len = 1; len <= n; len++) {
            for (int i = 0; i <= n - len; i++) {
                int j = i + len - 1;
                if (s.charAt(i) == s.charAt(j) && (len <= 2 || dp[i + 1][j - 1])) {
                    dp[i][j] = true;
                    count++;
                }
            }
        }
        return count;
    }
    ```
- **Time Complexity: \(O(n^2)\)**
- **Space Complexity: \(O(n^2)\)**

---
