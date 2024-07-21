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
