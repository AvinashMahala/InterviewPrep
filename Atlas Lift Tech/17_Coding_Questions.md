### Coding Questions and Sample Answers

---

#### 1. Reverse a String
**Problem Statement:**
Write a function to reverse a string.

**Sample Answer:**
```csharp
public string ReverseString(string input)
{
    char[] charArray = input.ToCharArray();
    Array.Reverse(charArray);
    return new string(charArray);
}
```

**Explanation:**
This function converts the input string to a character array, reverses the array, and then constructs a new string from the reversed array.

---

#### 2. Check if a Number is Prime
**Problem Statement:**
Write a function to check if a number is prime.

**Sample Answer:**
```csharp
public bool IsPrime(int number)
{
    if (number <= 1) return false;
    for (int i = 2; i <= Math.Sqrt(number); i++)
    {
        if (number % i == 0) return false;
    }
    return true;
}
```

**Explanation:**
This function checks if the input number is prime by dividing it by all numbers from 2 to the square root of the number. If it is divisible by any of these numbers, it is not prime.

---

#### 3. Find the Factorial of a Number
**Problem Statement:**
Write a function to find the factorial of a number.

**Sample Answer:**
```csharp
public int Factorial(int number)
{
    if (number == 0) return 1;
    return number * Factorial(number - 1);
}
```

**Explanation:**
This function uses recursion to calculate the factorial of a number. The base case is when the number is 0, and it returns 1. For other cases, it multiplies the number by the factorial of the number minus one.

---

#### 4. Find the Maximum Element in an Array
**Problem Statement:**
Write a function to find the maximum element in an array.

**Sample Answer:**
```csharp
public int FindMax(int[] array)
{
    int max = array[0];
    for (int i = 1; i < array.Length; i++)
    {
        if (array[i] > max)
        {
            max = array[i];
        }
    }
    return max;
}
```

**Explanation:**
This function iterates through the array and keeps track of the maximum value found so far.

---

#### 5. Merge Two Sorted Arrays
**Problem Statement:**
Write a function to merge two sorted arrays into a single sorted array.

**Sample Answer:**
```csharp
public int[] MergeSortedArrays(int[] arr1, int[] arr2)
{
    int[] mergedArray = new int[arr1.Length + arr2.Length];
    int i = 0, j = 0, k = 0;
    
    while (i < arr1.Length && j < arr2.Length)
    {
        if (arr1[i] <= arr2[j])
        {
            mergedArray[k++] = arr1[i++];
        }
        else
        {
            mergedArray[k++] = arr2[j++];
        }
    }
    
    while (i < arr1.Length)
    {
        mergedArray[k++] = arr1[i++];
    }
    
    while (j < arr2.Length)
    {
        mergedArray[k++] = arr2[j++];
    }
    
    return mergedArray;
}
```

**Explanation:**
This function merges two sorted arrays by comparing the elements of both arrays and placing the smaller one in the merged array. It continues until all elements are merged.

---

#### 6. Implement Binary Search
**Problem Statement:**
Write a function to perform binary search on a sorted array.

**Sample Answer:**
```csharp
public int BinarySearch(int[] array, int target)
{
    int left = 0;
    int right = array.Length - 1;
    
    while (left <= right)
    {
        int mid = left + (right - left) / 2;
        
        if (array[mid] == target)
        {
            return mid;
        }
        
        if (array[mid] < target)
        {
            left = mid + 1;
        }
        else
        {
            right = mid - 1;
        }
    }
    
    return -1; // Target not found
}
```

**Explanation:**
This function uses the binary search algorithm to find the target value in a sorted array. It returns the index of the target value or -1 if the target is not found.

---

#### 7. Check for Balanced Parentheses
**Problem Statement:**
Write a function to check if a string has balanced parentheses.

**Sample Answer:**
```csharp
public bool IsBalanced(string input)
{
    Stack<char> stack = new Stack<char>();
    
    foreach (char c in input)
    {
        if (c == '(' || c == '{' || c == '[')
        {
            stack.Push(c);
        }
        else if (c == ')' || c == '}' || c == ']')
        {
            if (stack.Count == 0) return false;
            char top = stack.Pop();
            if ((c == ')' && top != '(') ||
                (c == '}' && top != '{') ||
                (c == ']' && top != '['))
            {
                return false;
            }
        }
    }
    
    return stack.Count == 0;
}
```

**Explanation:**
This function uses a stack to check for balanced parentheses in a string. It pushes opening parentheses onto the stack and pops them when it encounters a matching closing parenthesis. If the stack is empty at the end, the parentheses are balanced.

---

#### 8. Find the Length of the Longest Substring Without Repeating Characters
**Problem Statement:**
Write a function to find the length of the longest substring without repeating characters.

**Sample Answer:**
```csharp
public int LengthOfLongestSubstring(string s)
{
    Dictionary<char, int> dict = new Dictionary<char, int>();
    int maxLength = 0, start = 0;
    
    for (int i = 0; i < s.Length; i++)
    {
        if (dict.ContainsKey(s[i]))
        {
            start = Math.Max(start, dict[s[i]] + 1);
        }
        
        dict[s[i]] = i;
        maxLength = Math.Max(maxLength, i - start + 1);
    }
    
    return maxLength;
}
```

**Explanation:**
This function uses a sliding window approach with a dictionary to keep track of the characters and their indices. It updates the start index to ensure no repeating characters are within the current window and calculates the maximum length of the substring.

---

#### 9. Find the Common Elements in Two Arrays
**Problem Statement:**
Write a function to find the common elements in two arrays.

**Sample Answer:**
```csharp
public int[] FindCommonElements(int[] arr1, int[] arr2)
{
    HashSet<int> set1 = new HashSet<int>(arr1);
    List<int> commonElements = new List<int>();
    
    foreach (int num in arr2)
    {
        if (set1.Contains(num))
        {
            commonElements.Add(num);
            set1.Remove(num); // To avoid duplicates
        }
    }
    
    return commonElements.ToArray();
}
```

**Explanation:**
This function uses a hash set to store the elements of the first array and iterates through the second array to find common elements. It avoids duplicates by removing the element from the set once it is added to the result list.

---

#### 10. Perform In-order Traversal of a Binary Tree
**Problem Statement:**
Write a function to perform in-order traversal of a binary tree.

**Sample Answer:**
```csharp
public void InOrderTraversal(TreeNode root)
{
    if (root == null) return;
    InOrderTraversal(root.left);
    Console.WriteLine(root.val);
    InOrderTraversal(root.right);
}
```

**Explanation:**
This function performs in-order traversal of a binary tree recursively. It visits the left subtree, then the root node, and finally the right subtree.

---

### More Coding Questions and Sample Answers

---

#### 11. Find the Kth Largest Element in an Array
**Problem Statement:**
Write a function to find the Kth largest element in an array.

**Sample Answer:**
```csharp
public int FindKthLargest(int[] nums, int k)
{
    Array.Sort(nums);
    return nums[nums.Length - k];
}
```

**Explanation:**
This function sorts the array in ascending order and returns the Kth largest element by accessing the (length - k) index.

---

#### 12. Implement a Queue Using Stacks
**Problem Statement:**
Write a function to implement a queue using two stacks.

**Sample Answer:**
```csharp
public class MyQueue
{
    private Stack<int> stack1 = new Stack<int>();
    private Stack<int> stack2 = new Stack<int>();

    public void Enqueue(int x)
    {
        stack1.Push(x);
    }

    public int Dequeue()
    {
        if (stack2.Count == 0)
        {
            while (stack1.Count > 0)
            {
                stack2.Push(stack1.Pop());
            }
        }
        return stack2.Pop();
    }

    public int Peek()
    {
        if (stack2.Count == 0)
        {
            while (stack1.Count > 0)
            {
                stack2.Push(stack1.Pop());
            }
        }
        return stack2.Peek();
    }

    public bool IsEmpty()
    {
        return stack1.Count == 0 && stack2.Count == 0;
    }
}
```

**Explanation:**
This implementation uses two stacks to maintain the order of elements in a queue. `Enqueue` operation pushes elements onto `stack1`, and `Dequeue` operation transfers elements from `stack1` to `stack2` to maintain the FIFO order.

---

#### 13. Detect a Cycle in a Linked List
**Problem Statement:**
Write a function to detect if a cycle exists in a linked list.

**Sample Answer:**
```csharp
public class ListNode
{
    public int val;
    public ListNode next;
    public ListNode(int x) { val = x; next = null; }
}

public bool HasCycle(ListNode head)
{
    if (head == null || head.next == null) return false;

    ListNode slow = head;
    ListNode fast = head.next;

    while (slow != fast)
    {
        if (fast == null || fast.next == null) return false;
        slow = slow.next;
        fast = fast.next.next;
    }
    return true;
}
```

**Explanation:**
This function uses Floyd’s Tortoise and Hare algorithm to detect a cycle in a linked list. It uses two pointers moving at different speeds. If there is a cycle, the fast pointer will eventually meet the slow pointer.

---

#### 14. Implement Merge Sort
**Problem Statement:**
Write a function to implement the merge sort algorithm.

**Sample Answer:**
```csharp
public void MergeSort(int[] array)
{
    if (array.Length <= 1) return;

    int mid = array.Length / 2;
    int[] left = new int[mid];
    int[] right = new int[array.Length - mid];

    Array.Copy(array, 0, left, 0, mid);
    Array.Copy(array, mid, right, 0, array.Length - mid);

    MergeSort(left);
    MergeSort(right);
    Merge(array, left, right);
}

private void Merge(int[] array, int[] left, int[] right)
{
    int i = 0, j = 0, k = 0;

    while (i < left.Length && j < right.Length)
    {
        if (left[i] <= right[j])
        {
            array[k++] = left[i++];
        }
        else
        {
            array[k++] = right[j++];
        }
    }

    while (i < left.Length)
    {
        array[k++] = left[i++];
    }

    while (j < right.Length)
    {
        array[k++] = right[j++];
    }
}
```

**Explanation:**
This function implements the merge sort algorithm by recursively splitting the array into halves, sorting each half, and merging them back together in sorted order.

---

#### 15. Find the First Non-Repeated Character in a String
**Problem Statement:**
Write a function to find the first non-repeated character in a string.

**Sample Answer:**
```csharp
public char FirstNonRepeatedCharacter(string str)
{
    Dictionary<char, int> countMap = new Dictionary<char, int>();

    foreach (char c in str)
    {
        if (countMap.ContainsKey(c))
        {
            countMap[c]++;
        }
        else
        {
            countMap[c] = 1;
        }
    }

    foreach (char c in str)
    {
        if (countMap[c] == 1)
        {
            return c;
        }
    }

    return '\0'; // Return null character if no non-repeated character is found
}
```

**Explanation:**
This function uses a dictionary to count the occurrences of each character in the string and then iterates through the string to find the first character with a count of one.

---

#### 16. Implement a Basic Calculator
**Problem Statement:**
Write a function to implement a basic calculator to evaluate a simple expression string.

**Sample Answer:**
```csharp
public int Calculate(string s)
{
    Stack<int> stack = new Stack<int>();
    int currentNumber = 0;
    char operation = '+';
    
    for (int i = 0; i < s.Length; i++)
    {
        char currentChar = s[i];
        
        if (char.IsDigit(currentChar))
        {
            currentNumber = currentNumber * 10 + (currentChar - '0');
        }
        
        if (!char.IsDigit(currentChar) && !char.IsWhiteSpace(currentChar) || i == s.Length - 1)
        {
            if (operation == '+')
            {
                stack.Push(currentNumber);
            }
            else if (operation == '-')
            {
                stack.Push(-currentNumber);
            }
            else if (operation == '*')
            {
                stack.Push(stack.Pop() * currentNumber);
            }
            else if (operation == '/')
            {
                stack.Push(stack.Pop() / currentNumber);
            }
            
            operation = currentChar;
            currentNumber = 0;
        }
    }
    
    int result = 0;
    while (stack.Count != 0)
    {
        result += stack.Pop();
    }
    
    return result;
}
```

**Explanation:**
This function evaluates a simple arithmetic expression string using a stack to handle intermediate results and operations.

---

#### 17. Check if a Binary Tree is a Valid Binary Search Tree (BST)
**Problem Statement:**
Write a function to check if a binary tree is a valid BST.

**Sample Answer:**
```csharp
public class TreeNode
{
    public int val;
    public TreeNode left;
    public TreeNode right;
    public TreeNode(int x) { val = x; }
}

public bool IsValidBST(TreeNode root)
{
    return IsValidBST(root, null, null);
}

private bool IsValidBST(TreeNode node, int? lower, int? upper)
{
    if (node == null) return true;

    int val = node.val;
    if (lower.HasValue && val <= lower.Value) return false;
    if (upper.HasValue && val >= upper.Value) return false;

    if (!IsValidBST(node.right, val, upper)) return false;
    if (!IsValidBST(node.left, lower, val)) return false;

    return true;
}
```

**Explanation:**
This function checks if a binary tree is a valid BST by recursively ensuring that each node's value is within the allowed range defined by its parent nodes.

---

#### 18. Find the Lowest Common Ancestor of a Binary Tree
**Problem Statement:**
Write a function to find the lowest common ancestor (LCA) of two nodes in a binary tree.

**Sample Answer:**
```csharp
public TreeNode LowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q)
{
    if (root == null || root == p || root == q) return root;

    TreeNode left = LowestCommonAncestor(root.left, p, q);
    TreeNode right = LowestCommonAncestor(root.right, p, q);

    if (left != null && right != null) return root;
    return left ?? right;
}
```

**Explanation:**
This function finds the LCA of two nodes in a binary tree by recursively searching for the nodes in the left and right subtrees and returning the common ancestor.

---

#### 19. Implement Depth-First Search (DFS) on a Graph
**Problem Statement:**
Write a function to perform depth-first search (DFS) on a graph.

**Sample Answer:**
```csharp
public void DFS(Dictionary<int, List<int>> graph, int start)
{
    HashSet<int> visited = new HashSet<int>();
    Stack<int> stack = new Stack<int>();

    stack.Push(start);

    while (stack.Count > 0)
    {
        int node = stack.Pop();

        if (!visited.Contains(node))
        {
            Console.WriteLine(node);
            visited.Add(node);

            foreach (var neighbor in graph[node])
            {
                if (!visited.Contains(neighbor))
                {
                    stack.Push(neighbor);
                }
            }
        }
    }
}
```

**Explanation:**
This function performs DFS on a graph represented as an adjacency list. It uses a stack to manage the traversal order and a set to keep track of visited nodes.

---

#### 20. Find the Longest Palindromic Substring
**

Problem Statement:**
Write a function to find the longest palindromic substring in a given string.

**Sample Answer:**
```csharp
public string LongestPalindrome(string s)
{
    if (string.IsNullOrEmpty(s)) return "";

    int start = 0, maxLength = 1;

    for (int i = 0; i < s.Length; i++)
    {
        int len1 = ExpandAroundCenter(s, i, i);
        int len2 = ExpandAroundCenter(s, i, i + 1);
        int len = Math.Max(len1, len2);

        if (len > maxLength)
        {
            start = i - (len - 1) / 2;
            maxLength = len;
        }
    }

    return s.Substring(start, maxLength);
}

private int ExpandAroundCenter(string s, int left, int right)
{
    while (left >= 0 && right < s.Length && s[left] == s[right])
    {
        left--;
        right++;
    }
    return right - left - 1;
}
```

**Explanation:**
This function finds the longest palindromic substring by expanding around each character (and each pair of characters) to find the maximum-length palindrome.

---

