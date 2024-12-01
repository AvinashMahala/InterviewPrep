
---

### **1. Reverse a String**
**Question:** Write a function to reverse a string.

**Answer (Python):**
```python
def reverse_string(s):
    return s[::-1]

# Test
print(reverse_string("coderpad"))  # Output: "dapredoc"
```

---

### **2. FizzBuzz**
**Question:** Write a program that prints numbers from 1 to 100. For multiples of 3, print "Fizz"; for multiples of 5, print "Buzz"; for multiples of both, print "FizzBuzz".

**Answer (Python):**
```python
def fizz_buzz(n):
    for i in range(1, n + 1):
        if i % 3 == 0 and i % 5 == 0:
            print("FizzBuzz")
        elif i % 3 == 0:
            print("Fizz")
        elif i % 5 == 0:
            print("Buzz")
        else:
            print(i)

fizz_buzz(100)
```

---

### **3. Check for Palindrome**
**Question:** Write a function to check if a given string is a palindrome.

**Answer (Python):**
```python
def is_palindrome(s):
    return s == s[::-1]

# Test
print(is_palindrome("racecar"))  # Output: True
print(is_palindrome("coderpad"))  # Output: False
```

---

### **4. Two Sum Problem**
**Question:** Given an array of integers, return indices of the two numbers that add up to a target.

**Answer (Python):**
```python
def two_sum(nums, target):
    num_map = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in num_map:
            return [num_map[complement], i]
        num_map[num] = i
    return []

# Test
print(two_sum([2, 7, 11, 15], 9))  # Output: [0, 1]
```

---

### **5. Find the First Non-Repeating Character**
**Question:** Write a function to find the first non-repeating character in a string.

**Answer (Python):**
```python
from collections import Counter

def first_non_repeating_char(s):
    char_count = Counter(s)
    for i, char in enumerate(s):
        if char_count[char] == 1:
            return i
    return -1

# Test
print(first_non_repeating_char("swiss"))  # Output: 0
```

---

### **6. Find the Longest Substring Without Repeating Characters**
**Question:** Write a function to find the length of the longest substring without repeating characters.

**Answer (Python):**
```python
def length_of_longest_substring(s):
    char_set = set()
    left = 0
    max_length = 0

    for right in range(len(s)):
        while s[right] in char_set:
            char_set.remove(s[left])
            left += 1
        char_set.add(s[right])
        max_length = max(max_length, right - left + 1)
    return max_length

# Test
print(length_of_longest_substring("abcabcbb"))  # Output: 3
```

---

### **7. Binary Search**
**Question:** Implement a binary search algorithm.

**Answer (Python):**
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

# Test
print(binary_search([1, 2, 3, 4, 5, 6], 4))  # Output: 3
```

---

### **8. Find Duplicates in an Array**
**Question:** Write a function to find duplicates in an array.

**Answer (Python):**
```python
def find_duplicates(nums):
    seen = set()
    duplicates = set()
    for num in nums:
        if num in seen:
            duplicates.add(num)
        else:
            seen.add(num)
    return list(duplicates)

# Test
print(find_duplicates([1, 2, 3, 4, 2, 5, 6, 3]))  # Output: [2, 3]
```

---

### **9. Merge Two Sorted Arrays**
**Question:** Merge two sorted arrays into one sorted array.

**Answer (Python):**
```python
def merge_sorted_arrays(arr1, arr2):
    i, j = 0, 0
    merged = []
    while i < len(arr1) and j < len(arr2):
        if arr1[i] < arr2[j]:
            merged.append(arr1[i])
            i += 1
        else:
            merged.append(arr2[j])
            j += 1
    merged.extend(arr1[i:])
    merged.extend(arr2[j:])
    return merged

# Test
print(merge_sorted_arrays([1, 3, 5], [2, 4, 6]))  # Output: [1, 2, 3, 4, 5, 6]
```

---

### **10. Generate Fibonacci Sequence**
**Question:** Generate the first N Fibonacci numbers.

**Answer (Python):**
```python
def generate_fibonacci(n):
    if n <= 0:
        return []
    fib = [0, 1]
    for i in range(2, n):
        fib.append(fib[-1] + fib[-2])
    return fib[:n]

# Test
print(generate_fibonacci(10))  # Output: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

---

Here are **additional CoderPad questions and answers**, focusing on a mix of algorithms, data structures, and problem-solving.

---

### **11. Rotate an Array**
**Question:** Rotate an array `nums` to the right by `k` steps.

**Answer (Python):**
```python
def rotate_array(nums, k):
    k %= len(nums)  # Handle cases where k > len(nums)
    nums[:] = nums[-k:] + nums[:-k]

# Test
nums = [1, 2, 3, 4, 5, 6, 7]
rotate_array(nums, 3)
print(nums)  # Output: [5, 6, 7, 1, 2, 3, 4]
```

---

### **12. Find the Missing Number**
**Question:** Given an array of integers from 0 to n, find the missing number.

**Answer (Python):**
```python
def find_missing_number(nums):
    n = len(nums)
    total = n * (n + 1) // 2  # Sum of numbers from 0 to n
    return total - sum(nums)

# Test
print(find_missing_number([3, 0, 1]))  # Output: 2
```

---

### **13. Check for Anagram**
**Question:** Check if two strings are anagrams of each other.

**Answer (Python):**
```python
def is_anagram(s1, s2):
    return sorted(s1) == sorted(s2)

# Test
print(is_anagram("listen", "silent"))  # Output: True
print(is_anagram("hello", "world"))    # Output: False
```

---

### **14. Find the Median of Two Sorted Arrays**
**Question:** Find the median of two sorted arrays.

**Answer (Python):**
```python
def find_median_sorted_arrays(nums1, nums2):
    merged = sorted(nums1 + nums2)
    mid = len(merged) // 2
    if len(merged) % 2 == 0:
        return (merged[mid - 1] + merged[mid]) / 2
    else:
        return merged[mid]

# Test
print(find_median_sorted_arrays([1, 3], [2]))  # Output: 2
print(find_median_sorted_arrays([1, 2], [3, 4]))  # Output: 2.5
```

---

### **15. Implement a Queue Using Two Stacks**
**Question:** Implement a queue using two stacks.

**Answer (Python):**
```python
class QueueUsingStacks:
    def __init__(self):
        self.stack1 = []
        self.stack2 = []

    def enqueue(self, item):
        self.stack1.append(item)

    def dequeue(self):
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        if not self.stack2:
            return None
        return self.stack2.pop()

# Test
queue = QueueUsingStacks()
queue.enqueue(1)
queue.enqueue(2)
print(queue.dequeue())  # Output: 1
print(queue.dequeue())  # Output: 2
```

---

### **16. Detect a Cycle in a Linked List**
**Question:** Given a linked list, determine if it contains a cycle.

**Answer (Python):**
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def has_cycle(head):
    slow, fast = head, head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False

# Test (Example nodes can be created to test this)
```

---

### **17. Merge K Sorted Lists**
**Question:** Merge k sorted linked lists and return it as one sorted list.

**Answer (Python):**
```python
from heapq import heappush, heappop

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def merge_k_sorted_lists(lists):
    heap = []
    for i, node in enumerate(lists):
        if node:
            heappush(heap, (node.val, i, node))

    dummy = ListNode(0)
    curr = dummy

    while heap:
        val, i, node = heappop(heap)
        curr.next = node
        curr = curr.next
        if node.next:
            heappush(heap, (node.next.val, i, node.next))

    return dummy.next
```

---

### **18. Validate a Binary Search Tree**
**Question:** Check if a given binary tree is a valid Binary Search Tree (BST).

**Answer (Python):**
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def is_valid_bst(root, lower=float('-inf'), upper=float('inf')):
    if not root:
        return True
    if root.val <= lower or root.val >= upper:
        return False
    return (is_valid_bst(root.left, lower, root.val) and
            is_valid_bst(root.right, root.val, upper))
```

---

### **19. Maximum Subarray Sum (Kadane's Algorithm)**
**Question:** Find the maximum sum of a contiguous subarray.

**Answer (Python):**
```python
def max_subarray_sum(nums):
    max_sum = current_sum = nums[0]
    for num in nums[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    return max_sum

# Test
print(max_subarray_sum([-2, 1, -3, 4, -1, 2, 1, -5, 4]))  # Output: 6
```

---

### **20. Generate All Subsets (Power Set)**
**Question:** Generate all subsets of a given set.

**Answer (Python):**
```python
def subsets(nums):
    result = []
    def backtrack(index, current):
        if index == len(nums):
            result.append(current[:])
            return
        current.append(nums[index])
        backtrack(index + 1, current)
        current.pop()
        backtrack(index + 1, current)
    backtrack(0, [])
    return result

# Test
print(subsets([1, 2, 3]))
# Output: [[], [1], [2], [1, 2], [3], [1, 3], [2, 3], [1, 2, 3]]
```

---

Here’s a deeper dive into more **CoderPad interview questions and answers**, focusing on more advanced and practical topics.

---

### **21. Find All Permutations of a String**
**Question:** Write a function to generate all permutations of a string.

**Answer (Python):**
```python
def string_permutations(s):
    def backtrack(path, remaining):
        if not remaining:
            result.append(path)
        for i in range(len(remaining)):
            backtrack(path + remaining[i], remaining[:i] + remaining[i+1:])

    result = []
    backtrack("", s)
    return result

# Test
print(string_permutations("abc"))
# Output: ['abc', 'acb', 'bac', 'bca', 'cab', 'cba']
```

---

### **22. Implement LRU Cache**
**Question:** Design and implement an LRU (Least Recently Used) cache.

**Answer (Python):**
```python
from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity):
        self.cache = OrderedDict()
        self.capacity = capacity

    def get(self, key):
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)
        return self.cache[key]

    def put(self, key, value):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)

# Test
lru = LRUCache(2)
lru.put(1, 1)
lru.put(2, 2)
print(lru.get(1))  # Output: 1
lru.put(3, 3)      # Evicts key 2
print(lru.get(2))  # Output: -1
```

---

### **23. Find the Kth Largest Element**
**Question:** Find the Kth largest element in an unsorted array.

**Answer (Python):**
```python
import heapq

def find_kth_largest(nums, k):
    return heapq.nlargest(k, nums)[-1]

# Test
print(find_kth_largest([3, 2, 1, 5, 6, 4], 2))  # Output: 5
```

---

### **24. Count Inversions in an Array**
**Question:** Count the number of inversions in an array (i.e., where `i < j` and `arr[i] > arr[j]`).

**Answer (Python):**
```python
def count_inversions(arr):
    def merge_sort_and_count(arr):
        if len(arr) < 2:
            return arr, 0
        mid = len(arr) // 2
        left, left_inv = merge_sort_and_count(arr[:mid])
        right, right_inv = merge_sort_and_count(arr[mid:])
        merged, split_inv = merge_and_count(left, right)
        return merged, left_inv + right_inv + split_inv

    def merge_and_count(left, right):
        i = j = 0
        merged = []
        inversions = 0
        while i < len(left) and j < len(right):
            if left[i] <= right[j]:
                merged.append(left[i])
                i += 1
            else:
                merged.append(right[j])
                inversions += len(left) - i
                j += 1
        merged.extend(left[i:])
        merged.extend(right[j:])
        return merged, inversions

    _, total_inversions = merge_sort_and_count(arr)
    return total_inversions

# Test
print(count_inversions([2, 3, 8, 6, 1]))  # Output: 5
```

---

### **25. Find the Longest Palindromic Substring**
**Question:** Find the longest palindromic substring in a given string.

**Answer (Python):**
```python
def longest_palindromic_substring(s):
    def expand_around_center(left, right):
        while left >= 0 and right < len(s) and s[left] == s[right]:
            left -= 1
            right += 1
        return right - left - 1

    start, end = 0, 0
    for i in range(len(s)):
        len1 = expand_around_center(i, i)
        len2 = expand_around_center(i, i + 1)
        max_len = max(len1, len2)
        if max_len > (end - start):
            start = i - (max_len - 1) // 2
            end = i + max_len // 2
    return s[start:end + 1]

# Test
print(longest_palindromic_substring("babad"))  # Output: "bab" or "aba"
```

---

### **26. Trap Rainwater**
**Question:** Given an array representing elevation heights, calculate how much rainwater it can trap.

**Answer (Python):**
```python
def trap_rainwater(height):
    if not height:
        return 0
    left, right = 0, len(height) - 1
    left_max, right_max = height[left], height[right]
    water = 0

    while left < right:
        if height[left] < height[right]:
            if height[left] >= left_max:
                left_max = height[left]
            else:
                water += left_max - height[left]
            left += 1
        else:
            if height[right] >= right_max:
                right_max = height[right]
            else:
                water += right_max - height[right]
            right -= 1
    return water

# Test
print(trap_rainwater([0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1]))  # Output: 6
```

---

### **27. Serialize and Deserialize a Binary Tree**
**Question:** Implement serialization and deserialization of a binary tree.

**Answer (Python):**
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def serialize(root):
    def helper(node):
        if not node:
            result.append("null")
        else:
            result.append(str(node.val))
            helper(node.left)
            helper(node.right)
    result = []
    helper(root)
    return ",".join(result)

def deserialize(data):
    def helper():
        if nodes[0] == "null":
            nodes.pop(0)
            return None
        node = TreeNode(int(nodes.pop(0)))
        node.left = helper()
        node.right = helper()
        return node
    nodes = data.split(",")
    return helper()

# Test
root = TreeNode(1, TreeNode(2), TreeNode(3, TreeNode(4), TreeNode(5)))
data = serialize(root)
print(data)  # Output: "1,2,null,null,3,4,null,null,5,null,null"
new_root = deserialize(data)
```

---

### **28. Find All Paths in a Graph**
**Question:** Write a function to find all paths from a start node to an end node in a directed graph.

**Answer (Python):**
```python
def all_paths(graph, start, end):
    def dfs(node, path):
        if node == end:
            result.append(path[:])
            return
        for neighbor in graph.get(node, []):
            dfs(neighbor, path + [neighbor])
    result = []
    dfs(start, [start])
    return result

# Test
graph = {
    "A": ["B", "C"],
    "B": ["C", "D"],
    "C": ["D"],
    "D": []
}
print(all_paths(graph, "A", "D"))
# Output: [['A', 'B', 'D'], ['A', 'C', 'D']]
```

---

Here’s a comprehensive list of **Data Structures and Algorithms (DSA) questions with answers** for further practice.

---

### **29. Find All Prime Numbers Using Sieve of Eratosthenes**
**Question:** Generate all prime numbers less than or equal to `n`.

**Answer (Python):**
```python
def sieve_of_eratosthenes(n):
    primes = [True] * (n + 1)
    primes[0] = primes[1] = False
    p = 2
    while p * p <= n:
        if primes[p]:
            for i in range(p * p, n + 1, p):
                primes[i] = False
        p += 1
    return [i for i in range(n + 1) if primes[i]]

# Test
print(sieve_of_eratosthenes(30))  # Output: [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
```

---

### **30. Find the Lowest Common Ancestor (LCA) of Two Nodes**
**Question:** Find the LCA of two nodes in a binary tree.

**Answer (Python):**
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def lowest_common_ancestor(root, p, q):
    if not root or root == p or root == q:
        return root
    left = lowest_common_ancestor(root.left, p, q)
    right = lowest_common_ancestor(root.right, p, q)
    return root if left and right else left or right

# Example Usage
# Construct the tree and find the LCA of two nodes
```

---

### **31. Topological Sort (Kahn’s Algorithm)**
**Question:** Implement topological sorting for a Directed Acyclic Graph (DAG).

**Answer (Python):**
```python
from collections import deque, defaultdict

def topological_sort(graph):
    in_degree = {node: 0 for node in graph}
    for node in graph:
        for neighbor in graph[node]:
            in_degree[neighbor] += 1

    queue = deque([node for node in in_degree if in_degree[node] == 0])
    result = []

    while queue:
        current = queue.popleft()
        result.append(current)
        for neighbor in graph[current]:
            in_degree[neighbor] -= 1
            if in_degree[neighbor] == 0:
                queue.append(neighbor)

    return result if len(result) == len(graph) else []

# Test
graph = {
    "A": ["C"],
    "B": ["C", "D"],
    "C": ["E"],
    "D": ["F"],
    "E": ["F"],
    "F": []
}
print(topological_sort(graph))  # Output: ['A', 'B', 'C', 'D', 'E', 'F']
```

---

### **32. Detect a Cycle in a Directed Graph**
**Question:** Check if a Directed Graph has a cycle.

**Answer (Python):**
```python
from collections import defaultdict

def has_cycle(graph):
    visited = set()
    stack = set()

    def dfs(node):
        if node in stack:
            return True
        if node in visited:
            return False
        stack.add(node)
        for neighbor in graph[node]:
            if dfs(neighbor):
                return True
        stack.remove(node)
        visited.add(node)
        return False

    for node in graph:
        if dfs(node):
            return True
    return False

# Test
graph = {
    "A": ["B"],
    "B": ["C"],
    "C": ["A"]
}
print(has_cycle(graph))  # Output: True
```

---

### **33. Kth Smallest Element in a BST**
**Question:** Find the Kth smallest element in a Binary Search Tree.

**Answer (Python):**
```python
def kth_smallest(root, k):
    def inorder(node):
        return inorder(node.left) + [node.val] + inorder(node.right) if node else []
    return inorder(root)[k - 1]

# Example Usage
# Construct the tree and call kth_smallest(root, k)
```

---

### **34. Find Bridges in a Graph**
**Question:** Find all the bridges in an undirected graph using Tarjan's Algorithm.

**Answer (Python):**
```python
from collections import defaultdict

def find_bridges(graph, n):
    discovery = [-1] * n
    low = [-1] * n
    parent = [-1] * n
    time = [0]
    bridges = []

    def dfs(u):
        discovery[u] = low[u] = time[0]
        time[0] += 1
        for v in graph[u]:
            if discovery[v] == -1:
                parent[v] = u
                dfs(v)
                low[u] = min(low[u], low[v])
                if low[v] > discovery[u]:
                    bridges.append((u, v))
            elif v != parent[u]:
                low[u] = min(low[u], discovery[v])

    for i in range(n):
        if discovery[i] == -1:
            dfs(i)
    return bridges

# Test
graph = defaultdict(list, {0: [1], 1: [0, 2, 3], 2: [1], 3: [1]})
print(find_bridges(graph, 4))  # Output: [(1, 3), (1, 2), (0, 1)]
```

---

### **35. Find All Combinations That Sum to a Target**
**Question:** Given an array of integers, find all unique combinations that sum up to a target.

**Answer (Python):**
```python
def combination_sum(candidates, target):
    def backtrack(start, target, path):
        if target == 0:
            result.append(path)
            return
        for i in range(start, len(candidates)):
            if candidates[i] > target:
                continue
            backtrack(i, target - candidates[i], path + [candidates[i]])

    candidates.sort()
    result = []
    backtrack(0, target, [])
    return result

# Test
print(combination_sum([2, 3, 6, 7], 7))  # Output: [[2, 2, 3], [7]]
```

---

### **36. Count Subarrays with a Given Sum**
**Question:** Count the number of subarrays that sum to a given target.

**Answer (Python):**
```python
def count_subarrays_with_sum(nums, target):
    prefix_sum = 0
    count = 0
    prefix_map = {0: 1}

    for num in nums:
        prefix_sum += num
        if prefix_sum - target in prefix_map:
            count += prefix_map[prefix_sum - target]
        prefix_map[prefix_sum] = prefix_map.get(prefix_sum, 0) + 1

    return count

# Test
print(count_subarrays_with_sum([1, 1, 1], 2))  # Output: 2
```

---

### **37. Implement Dijkstra’s Algorithm**
**Question:** Find the shortest path in a weighted graph.

**Answer (Python):**
```python
import heapq

def dijkstra(graph, start):
    distances = {node: float('inf') for node in graph}
    distances[start] = 0
    priority_queue = [(0, start)]

    while priority_queue:
        current_distance, current_node = heapq.heappop(priority_queue)
        if current_distance > distances[current_node]:
            continue
        for neighbor, weight in graph[current_node]:
            distance = current_distance + weight
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                heapq.heappush(priority_queue, (distance, neighbor))

    return distances

# Test
graph = {
    'A': [('B', 1), ('C', 4)],
    'B': [('A', 1), ('C', 2), ('D', 6)],
    'C': [('A', 4), ('B', 2), ('D', 3)],
    'D': [('B', 6), ('C', 3)]
}
print(dijkstra(graph, 'A'))  # Output: {'A': 0, 'B': 1, 'C': 3, 'D': 6}
```

---

































































































