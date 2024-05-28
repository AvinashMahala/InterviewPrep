Sure, I'll provide some common LeetCode-type coding questions with detailed explanations for their solutions in Python.

### 1. Two Sum
**Problem:** Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

**Solution Explanation:** 
We use a hash map (dictionary) to store the difference between the target and each number in the array as we iterate through it. This allows us to check in constant time if the complement of the current number exists in the map.

```python
def two_sum(nums, target):
    num_dict = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in num_dict:
            return [num_dict[complement], i]
        num_dict[num] = i

# Example usage:
nums = [2, 7, 11, 15]
target = 9
print(two_sum(nums, target))  # Output: [0, 1]
```

---

### 2. Add Two Numbers
**Problem:** You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

**Solution Explanation:** 
We iterate through both linked lists, adding corresponding digits along with any carry from the previous iteration. We continue this until we've processed both lists entirely and handled any remaining carry.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def add_two_numbers(l1, l2):
    dummy_head = ListNode(0)
    current, carry = dummy_head, 0
    
    while l1 or l2 or carry:
        val1 = (l1.val if l1 else 0)
        val2 = (l2.val if l2 else 0)
        carry, out = divmod(val1 + val2 + carry, 10)
        
        current.next = ListNode(out)
        current = current.next
        
        l1 = (l1.next if l1 else None)
        l2 = (l2.next if l2 else None)
    
    return dummy_head.next

# Example usage:
# Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
# Output: 7 -> 0 -> 8
```

---

### 3. Longest Substring Without Repeating Characters
**Problem:** Given a string `s`, find the length of the longest substring without repeating characters.

**Solution Explanation:**
We use a sliding window approach with two pointers. We expand the window by moving the right pointer and check if the character at the right pointer is already in the current window. If it is, we shrink the window from the left until the duplicate character is removed.

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

# Example usage:
s = "abcabcbb"
print(length_of_longest_substring(s))  # Output: 3
```

---

### 4. Median of Two Sorted Arrays
**Problem:** Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return the median of the two sorted arrays.

**Solution Explanation:**
We merge the two arrays and find the median. If the total length is odd, the median is the middle element. If it's even, the median is the average of the two middle elements.

```python
def find_median_sorted_arrays(nums1, nums2):
    nums = sorted(nums1 + nums2)
    mid = len(nums) // 2
    
    if len(nums) % 2 == 0:
        return (nums[mid - 1] + nums[mid]) / 2
    else:
        return nums[mid]

# Example usage:
nums1 = [1, 3]
nums2 = [2]
print(find_median_sorted_arrays(nums1, nums2))  # Output: 2.0
```

---

### 5. Longest Palindromic Substring
**Problem:** Given a string `s`, return the longest palindromic substring in `s`.

**Solution Explanation:**
We expand around each character (and each pair of characters) to find the longest palindromic substring by checking how far we can expand while the characters at both ends are the same.

```python
def longest_palindrome(s):
    res = ""
    
    for i in range(len(s)):
        temp = helper(s, i, i)
        if len(temp) > len(res):
            res = temp
        temp = helper(s, i, i + 1)
        if len(temp) > len(res):
            res = temp
            
    return res

def helper(s, l, r):
    while l >= 0 and r < len(s) and s[l] == s[r]:
        l -= 1
        r += 1
    return s[l + 1:r]

# Example usage:
s = "babad"
print(longest_palindrome(s))  # Output: "bab" or "aba"
```

---

### 6. Container With Most Water
**Problem:** Given `n` non-negative integers `a1, a2, ..., an`, where each represents a point at coordinate (i, ai). `n` vertical lines are drawn such that the two endpoints of the line `i` are at (i, ai) and (i, 0). Find two lines, which, together with the x-axis, forms a container, such that the container contains the most water.

**Solution Explanation:**
We use a two-pointer approach. Start with the widest container and then move the pointers towards each other, keeping track of the maximum area calculated.

```python
def max_area(height):
    left, right = 0, len(height) - 1
    max_area = 0
    
    while left < right:
        width = right - left
        max_area = max(max_area, min(height[left], height[right]) * width)
        
        if height[left] < height[right]:
            left += 1
        else:
            right -= 1
    
    return max_area

# Example usage:
height = [1,8,6,2,5,4,8,3,7]
print(max_area(height))  # Output: 49
```

---

### 7. Merge Two Sorted Lists
**Problem:** Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.

**Solution Explanation:**
We use a dummy node to simplify the merging process. We compare the heads of the two lists and attach the smaller one to the merged list. We continue this until we reach the end of one list, then attach the remaining part of the other list.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def merge_two_lists(l1, l2):
    dummy = ListNode()
    current = dummy
    
    while l1 and l2:
        if l1.val < l2.val:
            current.next = l1
            l1 = l1.next
        else:
            current.next = l2
            l2 = l2.next
        current = current.next
    
    current.next = l1 or l2
    
    return dummy.next

# Example usage:
# Input: 1->2->4, 1->3->4
# Output: 1->1->2->3->4->4
```

---

### 8. Reverse Linked List
**Problem:** Reverse a singly linked list.

**Solution Explanation:**
We iterate through the list, reversing the pointers as we go. We keep track of the previous node and the current node.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def reverse_list(head):
    prev = None
    current = head
    
    while current:
        next_node = current.next
        current.next = prev
        prev = current
        current = next_node
        
    return prev

# Example usage:
# Input: 1->2->3->4->5->NULL
# Output: 5->4->3->2->1->NULL
```

---

### 9. Merge Intervals
**Problem:** Given a collection of intervals, merge all overlapping intervals.

**Solution Explanation:**
We sort the intervals by their starting points. Then we iterate through the sorted intervals and merge them if they overlap.

```python
def merge_intervals(intervals):
    intervals.sort(key=lambda x: x[0])
    merged = []
    
    for interval in intervals:
        if not merged or merged[-1][1] < interval[0]:
            merged.append(interval)
        else:
            merged[-1][1] = max(merged[-1][1], interval[1])
    
    return merged

# Example usage:
intervals = [[1,3],[2,6],[8,10],[15,18]]
print(merge_intervals(intervals))  # Output: [[1,6],[8,10],[15,18]]
```

---

### 10

. Valid Parentheses
**Problem:** Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

**Solution Explanation:**
We use a stack to keep track of opening brackets. For each closing bracket, we check if it matches the most recent opening bracket.

```python
def is_valid(s):
    stack = []
    mapping = {")": "(", "}": "{", "]": "["}
    
    for char in s:
        if char in mapping:
            top_element = stack.pop() if stack else '#'
            if mapping[char] != top_element:
                return False
        else:
            stack.append(char)
    
    return not stack

# Example usage:
s = "()[]{}"
print(is_valid(s))  # Output: True
```

---

### 11. Remove Duplicates from Sorted Array
**Problem:** Given a sorted array nums, remove the duplicates in-place such that each element appears only once and returns the new length.

**Solution Explanation:**
We use a two-pointer approach where one pointer iterates through the array and the other keeps track of the position of unique elements.

```python
def remove_duplicates(nums):
    if not nums:
        return 0
    
    i = 0
    for j in range(1, len(nums)):
        if nums[j] != nums[i]:
            i += 1
            nums[i] = nums[j]
    
    return i + 1

# Example usage:
nums = [1,1,2]
print(remove_duplicates(nums))  # Output: 2, nums = [1, 2]
```

---

### 12. Maximum Subarray
**Problem:** Given an integer array nums, find the contiguous subarray which has the largest sum and return its sum.

**Solution Explanation:**
We use Kadane's algorithm, which involves iterating through the array while keeping track of the maximum sum subarray ending at each position.

```python
def max_subarray(nums):
    max_sum = current_sum = nums[0]
    
    for num in nums[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    
    return max_sum

# Example usage:
nums = [-2,1,-3,4,-1,2,1,-5,4]
print(max_subarray(nums))  # Output: 6
```

---

### 13. Climbing Stairs
**Problem:** You are climbing a staircase. It takes `n` steps to reach the top. Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Solution Explanation:**
This problem can be solved using dynamic programming. The number of ways to reach step `n` is the sum of the ways to reach steps `n-1` and `n-2`.

```python
def climb_stairs(n):
    if n == 1:
        return 1
    dp = [0] * (n + 1)
    dp[1], dp[2] = 1, 2
    
    for i in range(3, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]
    
    return dp[n]

# Example usage:
n = 3
print(climb_stairs(n))  # Output: 3
```

---

### 14. Coin Change
**Problem:** You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

**Solution Explanation:**
We use dynamic programming to build up the solution. We initialize a dp array where dp[i] represents the minimum number of coins needed to make amount i.

```python
def coin_change(coins, amount):
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0
    
    for coin in coins:
        for x in range(coin, amount + 1):
            dp[x] = min(dp[x], dp[x - coin] + 1)
    
    return dp[amount] if dp[amount] != float('inf') else -1

# Example usage:
coins = [1, 2, 5]
amount = 11
print(coin_change(coins, amount))  # Output: 3
```

---

### 15. Longest Increasing Subsequence
**Problem:** Given an integer array nums, return the length of the longest strictly increasing subsequence.

**Solution Explanation:**
We use dynamic programming where dp[i] represents the length of the longest increasing subsequence ending at index i.

```python
def length_of_lis(nums):
    if not nums:
        return 0
    dp = [1] * len(nums)
    
    for i in range(len(nums)):
        for j in range(i):
            if nums[i] > nums[j]:
                dp[i] = max(dp[i], dp[j] + 1)
    
    return max(dp)

# Example usage:
nums = [10, 9, 2, 5, 3, 7, 101, 18]
print(length_of_lis(nums))  # Output: 4
```

---

### 16. Merge k Sorted Lists
**Problem:** Merge `k` sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

**Solution Explanation:**
We use a min-heap to efficiently get the smallest element among the heads of the k lists.

```python
from heapq import heappush, heappop

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def merge_k_lists(lists):
    heap = []
    for l in lists:
        if l:
            heappush(heap, (l.val, l))
    
    dummy = ListNode()
    current = dummy
    
    while heap:
        val, node = heappop(heap)
        current.next = ListNode(val)
        current = current.next
        if node.next:
            heappush(heap, (node.next.val, node.next))
    
    return dummy.next

# Example usage:
# Input: k sorted linked lists
# Output: one sorted linked list
```

---

### 17. Word Break
**Problem:** Given a string `s` and a dictionary of strings `wordDict`, return true if `s` can be segmented into a space-separated sequence of one or more dictionary words.

**Solution Explanation:**
We use dynamic programming to check if the string can be segmented. We maintain a boolean array `dp` where dp[i] is True if the substring s[:i] can be segmented.

```python
def word_break(s, wordDict):
    dp = [False] * (len(s) + 1)
    dp[0] = True
    
    for i in range(1, len(s) + 1):
        for word in wordDict:
            if dp[i - len(word)] and s[i - len(word):i] == word:
                dp[i] = True
                break
    
    return dp[len(s)]

# Example usage:
s = "leetcode"
wordDict = ["leet", "code"]
print(word_break(s, wordDict))  # Output: True
```

---

### 18. Valid Palindrome
**Problem:** Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

**Solution Explanation:**
We use two pointers to check if the string is a palindrome. We ignore non-alphanumeric characters and compare the characters from both ends.

```python
def is_palindrome(s):
    left, right = 0, len(s) - 1
    
    while left < right:
        while left < right and not s[left].isalnum():
            left += 1
        while left < right and not s[right].isalnum():
            right -= 1
        if s[left].lower() != s[right].lower():
            return False
        left += 1
        right -= 1
    
    return True

# Example usage:
s = "A man, a plan, a canal: Panama"
print(is_palindrome(s))  # Output: True
```

---

### 19. Rotate Image
**Problem:** You are given an n x n 2D matrix representing an image. Rotate the image by 90 degrees (clockwise).

**Solution Explanation:**
We first transpose the matrix and then reverse each row to get the rotated matrix.

```python
def rotate(matrix):
    n = len(matrix)
    
    for i in range(n):
        for j in range(i, n):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
    
    for i in range(n):
        matrix[i].reverse()

# Example usage:
matrix = [
  [1,2,3],
  [4,5,6],
  [7,8,9]
]
rotate(matrix)
print(matrix)  # Output: [[7,4,1],[8,5,2],[9,6,3]]
```

---

### 20. Group Anagrams
**Problem:** Given an array of strings, group the anagrams together. You can return the answer in any order.

**Solution Explanation:**
We use a hash map to group anagrams. The key is a tuple of sorted characters, and the value is a list of words that match that key.

```python
def group_anagrams(strs):
    anagrams = {}
    
    for s in strs

:
        key = tuple(sorted(s))
        if key not in anagrams:
            anagrams[key] = []
        anagrams[key].append(s)
    
    return list(anagrams.values())

# Example usage:
strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
print(group_anagrams(strs))  # Output: [['eat', 'tea', 'ate'], ['tan', 'nat'], ['bat']]
```

Certainly! Here are 20 more common LeetCode-type coding questions with detailed explanations for their solutions in Python.

### 21. Find the Duplicate Number
**Problem:** Given an array `nums` containing `n + 1` integers where each integer is between 1 and `n` (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

**Solution Explanation:**
We use Floyd's Tortoise and Hare (Cycle Detection) algorithm to detect the duplicate number.

```python
def find_duplicate(nums):
    slow = fast = nums[0]
    
    while True:
        slow = nums[slow]
        fast = nums[nums[fast]]
        if slow == fast:
            break
            
    slow = nums[0]
    while slow != fast:
        slow = nums[slow]
        fast = nums[fast]
    
    return slow

# Example usage:
nums = [1, 3, 4, 2, 2]
print(find_duplicate(nums))  # Output: 2
```

---

### 22. Find Minimum in Rotated Sorted Array
**Problem:** Suppose an array of length `n` sorted in ascending order is rotated between 1 and `n` times. Given the rotated array, find the minimum element.

**Solution Explanation:**
We use binary search to find the minimum element in the rotated array.

```python
def find_min(nums):
    left, right = 0, len(nums) - 1
    
    while left < right:
        mid = (left + right) // 2
        if nums[mid] > nums[right]:
            left = mid + 1
        else:
            right = mid
    
    return nums[left]

# Example usage:
nums = [3, 4, 5, 1, 2]
print(find_min(nums))  # Output: 1
```

---

### 23. Search in Rotated Sorted Array
**Problem:** Given an integer array `nums` sorted in ascending order, and an integer `target`, find the index of the target in the rotated array. If not found, return -1.

**Solution Explanation:**
We use binary search while considering the pivot point in the rotated array.

```python
def search(nums, target):
    left, right = 0, len(nums) - 1
    
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        if nums[left] <= nums[mid]:
            if nums[left] <= target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] < target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
    
    return -1

# Example usage:
nums = [4, 5, 6, 7, 0, 1, 2]
target = 0
print(search(nums, target))  # Output: 4
```

---

### 24. Word Search
**Problem:** Given a 2D board and a word, find if the word exists in the grid. The word can be constructed from letters of sequentially adjacent cells, where "adjacent" cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

**Solution Explanation:**
We use backtracking to explore all possible paths for the word in the grid.

```python
def exist(board, word):
    def dfs(board, word, i, j, k):
        if k == len(word):
            return True
        if i < 0 or i >= len(board) or j < 0 or j >= len(board[0]) or board[i][j] != word[k]:
            return False
        
        tmp = board[i][j]
        board[i][j] = '#'
        res = (dfs(board, word, i+1, j, k+1) or 
               dfs(board, word, i-1, j, k+1) or 
               dfs(board, word, i, j+1, k+1) or 
               dfs(board, word, i, j-1, k+1))
        board[i][j] = tmp
        return res
    
    for i in range(len(board)):
        for j in range(len(board[0])):
            if dfs(board, word, i, j, 0):
                return True
    return False

# Example usage:
board = [
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]
word = "ABCCED"
print(exist(board, word))  # Output: True
```

---

### 25. Binary Tree Inorder Traversal
**Problem:** Given the root of a binary tree, return the inorder traversal of its nodes' values.

**Solution Explanation:**
We use a stack to simulate the inorder traversal iteratively.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def inorder_traversal(root):
    res, stack = [], []
    while root or stack:
        while root:
            stack.append(root)
            root = root.left
        root = stack.pop()
        res.append(root.val)
        root = root.right
    return res

# Example usage:
# Input: root = [1,null,2,3]
# Output: [1,3,2]
```

---

### 26. Symmetric Tree
**Problem:** Given a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

**Solution Explanation:**
We use a recursive approach to compare the left and right subtrees.

```python
def is_symmetric(root):
    def is_mirror(t1, t2):
        if not t1 and not t2:
            return True
        if not t1 or not t2:
            return False
        return (t1.val == t2.val and 
                is_mirror(t1.right, t2.left) and 
                is_mirror(t1.left, t2.right))
    
    return is_mirror(root, root)

# Example usage:
# Input: root = [1,2,2,3,4,4,3]
# Output: True
```

---

### 27. Maximum Depth of Binary Tree
**Problem:** Given the root of a binary tree, return its maximum depth.

**Solution Explanation:**
We use a recursive depth-first search to find the maximum depth.

```python
def max_depth(root):
    if not root:
        return 0
    return 1 + max(max_depth(root.left), max_depth(root.right))

# Example usage:
# Input: root = [3,9,20,null,null,15,7]
# Output: 3
```

---

### 28. Construct Binary Tree from Preorder and Inorder Traversal
**Problem:** Given two integer arrays `preorder` and `inorder` where `preorder` is the preorder traversal of a binary tree and `inorder` is the inorder traversal of the same tree, construct and return the binary tree.

**Solution Explanation:**
We use the preorder array to determine the root nodes and the inorder array to determine the structure of the tree.

```python
def build_tree(preorder, inorder):
    if not preorder or not inorder:
        return None
    
    root = TreeNode(preorder[0])
    mid = inorder.index(preorder[0])
    
    root.left = build_tree(preorder[1:mid+1], inorder[:mid])
    root.right = build_tree(preorder[mid+1:], inorder[mid+1:])
    
    return root

# Example usage:
# Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
# Output: [3,9,20,null,null,15,7]
```

---

### 29. Kth Smallest Element in a BST
**Problem:** Given the root of a binary search tree, and an integer `k`, return the `k`th smallest value (1-indexed) of all the values of the nodes in the tree.

**Solution Explanation:**
We perform an inorder traversal to get the elements in sorted order and then return the k-th smallest element.

```python
def kth_smallest(root, k):
    stack = []
    
    while True:
        while root:
            stack.append(root)
            root = root.left
        root = stack.pop()
        k -= 1
        if k == 0:
            return root.val
        root = root.right

# Example usage:
# Input: root = [3,1,4,null,2], k = 1
# Output: 1
```

---

### 30. Lowest Common Ancestor of a Binary Tree
**Problem:** Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

**Solution Explanation:**
We use a recursive approach to find the LCA by traversing the tree and checking if the current node is an ancestor of the given nodes.

```python
def lowest_common_ancestor(root, p, q):
    if not root or root == p or root == q:
        return root
    left = lowest_common_ancestor(root.left, p, q)
    right = lowest_common_ancestor(root.right, p, q)
    if left and right:
        return root
    return left if left else right

# Example usage:
# Input: root =

 [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
# Output: 3
```

---

### 31. Serialize and Deserialize Binary Tree
**Problem:** Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

**Solution Explanation:**
We use level-order traversal to serialize the tree into a string and deserialize it back using a queue.

```python
class Codec:
    def serialize(self, root):
        if not root:
            return ""
        queue = [root]
        res = []
        while queue:
            node = queue.pop(0)
            if node:
                res.append(str(node.val))
                queue.append(node.left)
                queue.append(node.right)
            else:
                res.append("#")
        return ",".join(res)

    def deserialize(self, data):
        if not data:
            return None
        nodes = data.split(",")
        root = TreeNode(int(nodes[0]))
        queue = [root]
        i = 1
        while queue:
            node = queue.pop(0)
            if nodes[i] != "#":
                node.left = TreeNode(int(nodes[i]))
                queue.append(node.left)
            i += 1
            if nodes[i] != "#":
                node.right = TreeNode(int(nodes[i]))
                queue.append(node.right)
            i += 1
        return root

# Example usage:
# codec = Codec()
# tree = codec.deserialize("1,2,3,#,#,4,5")
# serialized = codec.serialize(tree)
# print(serialized)  # Output: "1,2,3,#,#,4,5"
```

---

### 32. Combination Sum
**Problem:** Given an array of distinct integers `candidates` and a target integer `target`, return a list of all unique combinations of `candidates` where the chosen numbers sum to `target`. The same number may be chosen from `candidates` an unlimited number of times.

**Solution Explanation:**
We use backtracking to find all possible combinations that sum to the target.

```python
def combination_sum(candidates, target):
    res = []
    
    def backtrack(remain, comb, start):
        if remain == 0:
            res.append(list(comb))
            return
        elif remain < 0:
            return
        
        for i in range(start, len(candidates)):
            comb.append(candidates[i])
            backtrack(remain - candidates[i], comb, i)
            comb.pop()
    
    backtrack(target, [], 0)
    return res

# Example usage:
candidates = [2,3,6,7]
target = 7
print(combination_sum(candidates, target))  # Output: [[2,2,3], [7]]
```

---

### 33. Subsets
**Problem:** Given an integer array `nums`, return all possible subsets (the power set).

**Solution Explanation:**
We use backtracking to generate all subsets.

```python
def subsets(nums):
    res = []
    
    def backtrack(start, path):
        res.append(list(path))
        for i in range(start, len(nums)):
            path.append(nums[i])
            backtrack(i + 1, path)
            path.pop()
    
    backtrack(0, [])
    return res

# Example usage:
nums = [1,2,3]
print(subsets(nums))  # Output: [[], [1], [2], [3], [1,2], [1,3], [2,3], [1,2,3]]
```

---

### 34. Permutations
**Problem:** Given an array `nums` of distinct integers, return all possible permutations.

**Solution Explanation:**
We use backtracking to generate all permutations.

```python
def permute(nums):
    res = []
    
    def backtrack(start):
        if start == len(nums):
            res.append(list(nums))
            return
        
        for i in range(start, len(nums)):
            nums[start], nums[i] = nums[i], nums[start]
            backtrack(start + 1)
            nums[start], nums[i] = nums[i], nums[start]
    
    backtrack(0)
    return res

# Example usage:
nums = [1,2,3]
print(permute(nums))  # Output: [[1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], [3,2,1]]
```

---

### 35. Palindrome Partitioning
**Problem:** Given a string `s`, partition `s` such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of `s`.

**Solution Explanation:**
We use backtracking to find all possible partitions and check if each substring is a palindrome.

```python
def partition(s):
    res = []
    
    def backtrack(start, path):
        if start == len(s):
            res.append(list(path))
            return
        
        for i in range(start, len(s)):
            if is_palindrome(s, start, i):
                path.append(s[start:i+1])
                backtrack(i + 1, path)
                path.pop()
    
    def is_palindrome(s, low, high):
        while low < high:
            if s[low] != s[high]:
                return False
            low += 1
            high -= 1
        return True
    
    backtrack(0, [])
    return res

# Example usage:
s = "aab"
print(partition(s))  # Output: [["a","a","b"], ["aa","b"]]
```

---

### 36. Unique Paths
**Problem:** A robot is located at the top-left corner of a `m x n` grid. The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid. How many possible unique paths are there?

**Solution Explanation:**
We use dynamic programming to find the number of unique paths.

```python
def unique_paths(m, n):
    dp = [[1] * n for _ in range(m)]
    
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = dp[i-1][j] + dp[i][j-1]
    
    return dp[-1][-1]

# Example usage:
m = 3
n = 7
print(unique_paths(m, n))  # Output: 28
```

---

### 37. Minimum Path Sum
**Problem:** Given a `m x n` grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

**Solution Explanation:**
We use dynamic programming to find the minimum path sum.

```python
def min_path_sum(grid):
    m, n = len(grid), len(grid[0])
    dp = [[0] * n for _ in range(m)]
    dp[0][0] = grid[0][0]
    
    for i in range(1, m):
        dp[i][0] = dp[i-1][0] + grid[i][0]
    
    for j in range(1, n):
        dp[0][j] = dp[0][j-1] + grid[0][j]
    
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = grid[i][j] + min(dp[i-1][j], dp[i][j-1])
    
    return dp[-1][-1]

# Example usage:
grid = [
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
print(min_path_sum(grid))  # Output: 7
```

---

### 38. Decode Ways
**Problem:** A message containing letters from A-Z can be encoded into numbers using the following mapping: 'A' -> 1, 'B' -> 2, ..., 'Z' -> 26. Given a string s containing only digits, return the number of ways to decode it.

**Solution Explanation:**
We use dynamic programming to find the number of ways to decode the string.

```python
def num_decodings(s):
    if not s or s[0] == '0':
        return 0
    
    n = len(s)
    dp = [0] * (n + 1)
    dp[0], dp[1] = 1, 1
    
    for i in range(2, n + 1):
        if 1 <= int(s[i-1:i]) <= 9:
            dp[i] += dp[i-1]
        if 10 <= int(s[i-2:i]) <= 26:
            dp[i] += dp[i-2]
    
    return dp[n]

# Example usage:
s = "226"
print(num_decodings(s))  # Output: 3
```

---
