## 58. Length of Last Word

```embed
title: "Length of Last Word - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Length of Last Word - Given a string s consisting of words and spaces, return the length of the last word in the string.  A word is a maximal substring consisting of non-space characters only.     Example 1:   Input: s = \"Hello World\" Output: 5 Explanation: The last word is \"World\" with length 5.   Example 2:   Input: s = \"   fly me   to   the moon  \" Output: 4 Explanation: The last word is \"moon\" with length 4.   Example 3:   Input: s = \"luffy is still joyboy\" Output: 6 Explanation: The last word is \"joyboy\" with length 6.      Constraints:   * 1 <= s.length <= 104  * s consists of only English letters and spaces ' '.  * There will be at least one word in s."
url: "https://leetcode.com/problems/length-of-last-word/"
favicon: ""
aspectRatio: "52"
```


```cpp
class Solution {
    public int lengthOfLastWord(String s) {
        int n = s.length();
        int count = 0;
        int p = n - 1;
        // Find the index of the last non-space character
        for (int i = 0; i < n; i++) {
            if (s.charAt(i) != ' ') {
                p = i;
            }
        }
        // Count characters of the last word backwards
        for (int i = p; i >= 0; i--) {
            if (s.charAt(i) == ' ') {
                break;
            }
            count++;
        }
        return count;
    }
}

```

## 66. Plus One

```embed
title: "Plus One - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Plus One - You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.  Increment the large integer by one and return the resulting array of digits.     Example 1:   Input: digits = [1,2,3] Output: [1,2,4] Explanation: The array represents the integer 123. Incrementing by one gives 123 + 1 = 124. Thus, the result should be [1,2,4].   Example 2:   Input: digits = [4,3,2,1] Output: [4,3,2,2] Explanation: The array represents the integer 4321. Incrementing by one gives 4321 + 1 = 4322. Thus, the result should be [4,3,2,2].   Example 3:   Input: digits = [9] Output: [1,0] Explanation: The array represents the integer 9. Incrementing by one gives 9 + 1 = 10. Thus, the result should be [1,0].      Constraints:   * 1 <= digits.length <= 100  * 0 <= digits[i] <= 9  * digits does not contain any leading 0's."
url: "https://leetcode.com/problems/plus-one/"
favicon: ""
aspectRatio: "52"
```


```java
class Solution {
    public int[] plusOne(int[] digits) {
        int n = digits.length;
        // Traverse from last digit
        for (int i = n - 1; i >= 0; i--) {
            // If digit is less than 9, simply increment and return
            if (digits[i] < 9) {
                digits[i]++;
                return digits;
            }
            
            // If digit is 9, set it to 0 and continue loop (carry)
            digits[i] = 0;
        }
        // If all digits were 9, we need an extra leading 1
        int[] result = new int[n + 1];
        result[0] = 1; // rest will be 0 by default
        return result;
    }
}

```

## 67. Add Binary

```embed
title: "Add Binary - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Add Binary - Given two binary strings a and b, return their sum as a binary string.     Example 1:  Input: a = \"11\", b = \"1\" Output: \"100\"   Example 2:  Input: a = \"1010\", b = \"1011\" Output: \"10101\"      Constraints:   * 1 <= a.length, b.length <= 104  * a and b consist only of '0' or '1' characters.  * Each string does not contain leading zeros except for the zero itself."
url: "https://leetcode.com/problems/add-binary/"
favicon: ""
aspectRatio: "52"
```


```java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder result = new StringBuilder();
        
        int i = a.length() - 1;
        int j = b.length() - 1;
        int carry = 0;
        // Loop through both strings from right to left
        while (i >= 0 || j >= 0 || carry == 1) {
            int sum = carry;
            if (i >= 0) {
                sum += a.charAt(i--) - '0'; // convert char to int
            }
            if (j >= 0) {
                sum += b.charAt(j--) - '0';
            }
            // Append the current bit (sum % 2)
            result.append(sum % 2);
            // Update carry
            carry = sum / 2;
        }
        // Reverse the result to get correct order
        return result.reverse().toString();
    }
}

```

## 69. Sqrt(x)

```embed
title: "Sqrt(x) - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Sqrt(x) - Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well.  You must not use any built-in exponent function or operator.   * For example, do not use pow(x, 0.5) in c++ or x ** 0.5 in python.     Example 1:   Input: x = 4 Output: 2 Explanation: The square root of 4 is 2, so we return 2.   Example 2:   Input: x = 8 Output: 2 Explanation: The square root of 8 is 2.82842..., and since we round it down to the nearest integer, 2 is returned.      Constraints:   * 0 <= x <= 231 - 1"
url: "https://leetcode.com/problems/sqrtx/"
favicon: ""
aspectRatio: "52"
```


```java
class Solution {
    public int mySqrt(int x) {
        if (x < 2) return x;
        int left = 1, right = x / 2;
        int ans = 0;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            long sq = (long) mid * mid; // avoid overflow
            if (sq == x) {
                return mid;
            } else if (sq < x) {
                ans = mid;       // store last valid value
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return ans;
    }
}

```

## 70. Climbing Stairs

```embed
title: "Climbing Stairs - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Climbing Stairs - You are climbing a staircase. It takes n steps to reach the top.  Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?     Example 1:   Input: n = 2 Output: 2 Explanation: There are two ways to climb to the top. 1. 1 step + 1 step 2. 2 steps   Example 2:   Input: n = 3 Output: 3 Explanation: There are three ways to climb to the top. 1. 1 step + 1 step + 1 step 2. 1 step + 2 steps 3. 2 steps + 1 step      Constraints:   * 1 <= n <= 45"
url: "https://leetcode.com/problems/climbing-stairs/"
favicon: ""
aspectRatio: "52"
```


```java
class Solution {
    public int climbStairs(int n) {
        if (n <= 2) return n;
        int a = 1; // ways to reach step 1
        int b = 2; // ways to reach step 2
        for (int i = 3; i <= n; i++) {
            int c = a + b; // current ways
            a = b;        // shift
            b = c;        // shift
        }
        return b;
    }
}

```

## 83. Remove Duplicates from Sorted List

```embed
title: "Remove Duplicates from Sorted List - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Remove Duplicates from Sorted List - Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.     Example 1:  [https://assets.leetcode.com/uploads/2021/01/04/list1.jpg]   Input: head = [1,1,2] Output: [1,2]   Example 2:  [https://assets.leetcode.com/uploads/2021/01/04/list2.jpg]   Input: head = [1,1,2,3,3] Output: [1,2,3]      Constraints:   * The number of nodes in the list is in the range [0, 300].  * -100 <= Node.val <= 100  * The list is guaranteed to be sorted in ascending order."
url: "https://leetcode.com/problems/remove-duplicates-from-sorted-list/"
favicon: ""
aspectRatio: "52"
```


```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null) return null;
        ListNode current = head;
        while (current != null && current.next != null) {
            if (current.val == current.next.val) {
                // skip the duplicate
                current.next = current.next.next;
            } else {
                current = current.next; // move forward
            }
        }
        return head;
    }
}

```

## 88. Merge Sorted Array

```embed
title: "Merge Sorted Array - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Merge Sorted Array - You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.  Merge nums1 and nums2 into a single array sorted in non-decreasing order.  The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.     Example 1:   Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3 Output: [1,2,2,3,5,6] Explanation: The arrays we are merging are [1,2,3] and [2,5,6]. The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.   Example 2:   Input: nums1 = [1], m = 1, nums2 = [], n = 0 Output: [1] Explanation: The arrays we are merging are [1] and []. The result of the merge is [1].   Example 3:   Input: nums1 = [0], m = 0, nums2 = [1], n = 1 Output: [1] Explanation: The arrays we are merging are [] and [1]. The result of the merge is [1]. Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.      Constraints:   * nums1.length == m + n  * nums2.length == n  * 0 <= m, n <= 200  * 1 <= m + n <= 200  * -109 <= nums1[i], nums2[j] <= 109     Follow up: Can you come up with an algorithm that runs in O(m + n) time?"
url: "https://leetcode.com/problems/merge-sorted-array/"
favicon: ""
aspectRatio: "52"
```


```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m - 1;      // pointer for nums1
        int j = n - 1;      // pointer for nums2
        int k = m + n - 1;  // pointer for final position
        while (i >= 0 && j >= 0) {
            if (nums1[i] > nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }
        // If nums2 still has remaining elements
        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
}

```

## 94. Binary Tree Inorder Traversal

```embed
title: "Binary Tree Inorder Traversal - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Binary Tree Inorder Traversal - Given the root of a binary tree, return the inorder traversal of its nodes' values.     Example 1:  Input: root = [1,null,2,3]  Output: [1,3,2]  Explanation:  [https://assets.leetcode.com/uploads/2024/08/29/screenshot-2024-08-29-202743.png]  Example 2:  Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]  Output: [4,2,6,5,7,1,3,9,8]  Explanation:  [https://assets.leetcode.com/uploads/2024/08/29/tree_2.png]  Example 3:  Input: root = []  Output: []  Example 4:  Input: root = [1]  Output: [1]     Constraints:   * The number of nodes in the tree is in the range [0, 100].  * -100 <= Node.val <= 100     Follow up: Recursive solution is trivial, could you do it iteratively?"
url: "https://leetcode.com/problems/binary-tree-inorder-traversal/"
favicon: ""
aspectRatio: "52"
```


```java
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        inorder(root, result);
        return result;
    }
    private void inorder(TreeNode node, List<Integer> result) {
        if (node == null) return;
        
        inorder(node.left, result);   // Left
        result.add(node.val);         // Root
        inorder(node.right, result);  // Right
    }
}

```

## 100. Same Tree

```embed
title: "Same Tree - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Same Tree - Given the roots of two binary trees p and q, write a function to check if they are the same or not.  Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.     Example 1:  [https://assets.leetcode.com/uploads/2020/12/20/ex1.jpg]   Input: p = [1,2,3], q = [1,2,3] Output: true   Example 2:  [https://assets.leetcode.com/uploads/2020/12/20/ex2.jpg]   Input: p = [1,2], q = [1,null,2] Output: false   Example 3:  [https://assets.leetcode.com/uploads/2020/12/20/ex3.jpg]   Input: p = [1,2,1], q = [1,1,2] Output: false      Constraints:   * The number of nodes in both trees is in the range [0, 100].  * -104 <= Node.val <= 104"
url: "https://leetcode.com/problems/same-tree/"
favicon: ""
aspectRatio: "52"
```


```java
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        // Both nodes are null → trees match here
        if (p == null && q == null) return true;
        // One is null and the other is not → mismatch
        if (p == null || q == null) return false;
        // Values don't match → mismatch
        if (p.val != q.val) return false;
        // Check left subtree AND right subtree
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }
}

```

## 101. Symmetric Tree

```embed
title: "Symmetric Tree - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Symmetric Tree - Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).     Example 1:  [https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg]   Input: root = [1,2,2,3,4,4,3] Output: true   Example 2:  [https://assets.leetcode.com/uploads/2021/02/19/symtree2.jpg]   Input: root = [1,2,2,null,3,null,3] Output: false      Constraints:   * The number of nodes in the tree is in the range [1, 1000].  * -100 <= Node.val <= 100     Follow up: Could you solve it both recursively and iteratively?"
url: "https://leetcode.com/problems/symmetric-tree/"
favicon: ""
aspectRatio: "52"
```


```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        return isMirror(root.left, root.right);
    }
    private boolean isMirror(TreeNode t1, TreeNode t2) {
        // If both nodes are null → symmetric
        if (t1 == null && t2 == null) return true;
        // One is null but not the other → not symmetric
        if (t1 == null || t2 == null) return false;
        // Values must match AND subtrees must be mirrors
        return (t1.val == t2.val)
            && isMirror(t1.left, t2.right)
            && isMirror(t1.right, t2.left);
    }
}

```

