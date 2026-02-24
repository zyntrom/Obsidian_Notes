## 60. Permutation Sequence
- [x] Check 
### Math/Factorial

```embed
title: "Permutation Sequence - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Permutation Sequence - The set [1, 2, 3, ..., n] contains a total of n! unique permutations.  By listing and labeling all of the permutations in order, we get the following sequence for n = 3:   1. \"123\"  2. \"132\"  3. \"213\"  4. \"231\"  5. \"312\"  6. \"321\"  Given n and k, return the kth permutation sequence.     Example 1:  Input: n = 3, k = 3 Output: \"213\"   Example 2:  Input: n = 4, k = 9 Output: \"2314\"   Example 3:  Input: n = 3, k = 1 Output: \"123\"      Constraints:   * 1 <= n <= 9  * 1 <= k <= n!"
url: "https://leetcode.com/problems/permutation-sequence/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def getPermutation(self, n, k):
        nums = []
        fact = 1
        i = 1
        while i <= n:
            nums.append(i)
            fact = fact * i
            i = i + 1
        k = k - 1 
        result = ""
        i = n
        while i > 0:
            fact = fact // i
            idx = k // fact
            result = result + str(nums[idx])
            nums.pop(idx)
            k = k % fact
            i = i - 1
        return result
```

## 1823. Find the Winner of the Circular Game
- [x] Check 
### Queue/Simulation

```embed
title: "Find the Winner of the Circular Game - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Find the Winner of the Circular Game - There are n friends that are playing a game. The friends are sitting in a circle and are numbered from 1 to n in clockwise order. More formally, moving clockwise from the ith friend brings you to the (i+1)th friend for 1 <= i < n, and moving clockwise from the nth friend brings you to the 1st friend.  The rules of the game are as follows:   1. Start at the 1st friend.  2. Count the next k friends in the clockwise direction including the friend you started at. The counting wraps around the circle and may count some friends more than once.  3. The last friend you counted leaves the circle and loses the game.  4. If there is still more than one friend in the circle, go back to step 2 starting from the friend immediately clockwise of the friend who just lost and repeat.  5. Else, the last friend in the circle wins the game.  Given the number of friends, n, and an integer k, return the winner of the game.     Example 1:  [https://assets.leetcode.com/uploads/2021/03/25/ic234-q2-ex11.png]   Input: n = 5, k = 2 Output: 3 Explanation: Here are the steps of the game: 1) Start at friend 1. 2) Count 2 friends clockwise, which are friends 1 and 2. 3) Friend 2 leaves the circle. Next start is friend 3. 4) Count 2 friends clockwise, which are friends 3 and 4. 5) Friend 4 leaves the circle. Next start is friend 5. 6) Count 2 friends clockwise, which are friends 5 and 1. 7) Friend 1 leaves the circle. Next start is friend 3. 8) Count 2 friends clockwise, which are friends 3 and 5. 9) Friend 5 leaves the circle. Only friend 3 is left, so they are the winner.  Example 2:   Input: n = 6, k = 5 Output: 1 Explanation: The friends leave in this order: 5, 4, 6, 2, 3. The winner is friend 1.      Constraints:   * 1 <= k <= n <= 500     Follow up:  Could you solve this problem in linear time with constant space?"
url: "https://leetcode.com/problems/find-the-winner-of-the-circular-game/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def findTheWinner(self, n, k):
        winner = 0
        i = 1
        while i <= n:
            winner = (winner + k) % i
            i = i + 1
        return winner + 1
```

## 53. Maximum Subarray
- [x] Check 
```embed
title: "Maximum Subarray - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Maximum Subarray - Given an integer array nums, find the subarray with the largest sum, and return its sum.     Example 1:   Input: nums = [-2,1,-3,4,-1,2,1,-5,4] Output: 6 Explanation: The subarray [4,-1,2,1] has the largest sum 6.   Example 2:   Input: nums = [1] Output: 1 Explanation: The subarray [1] has the largest sum 1.   Example 3:   Input: nums = [5,4,-1,7,8] Output: 23 Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.      Constraints:   * 1 <= nums.length <= 105  * -104 <= nums[i] <= 104     Follow up: If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle."
url: "https://leetcode.com/problems/maximum-subarray/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def maxSubArray(self, nums):
        current_sum = nums[0]
        max_sum = nums[0]
        i = 1
        while i < len(nums):
            current_sum = max(nums[i], current_sum + nums[i])
            max_sum = max(max_sum, current_sum)
            i = i + 1
        return max_sum
```

## 416. Partition Equal Subset Sum
- [x] Check 
```embed
title: "Partition Equal Subset Sum - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Partition Equal Subset Sum - Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.     Example 1:   Input: nums = [1,5,11,5] Output: true Explanation: The array can be partitioned as [1, 5, 5] and [11].   Example 2:   Input: nums = [1,2,3,5] Output: false Explanation: The array cannot be partitioned into equal sum subsets.      Constraints:   * 1 <= nums.length <= 200  * 1 <= nums[i] <= 100"
url: "https://leetcode.com/problems/partition-equal-subset-sum/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def canPartition(self, nums):
        total = 0
        for num in nums:
            total = total + num
            
        if total % 2 != 0:
            return False
        target = total // 2
        dp = [False] * (target + 1)
        dp[0] = True
          
        for num in nums:
            s = target
            while s >= num:
                dp[s] = dp[s] or dp[s - num]
                s = s - 1
        return dp[target]
```

## 5. Longest Palindromic Substring
- [x] Check 
```embed
title: "Longest Palindromic Substring - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Longest Palindromic Substring - Given a string s, return the longest palindromic substring in s.     Example 1:   Input: s = \"babad\" Output: \"bab\" Explanation: \"aba\" is also a valid answer.   Example 2:   Input: s = \"cbbd\" Output: \"bb\"      Constraints:   * 1 <= s.length <= 1000  * s consist of only digits and English letters."
url: "https://leetcode.com/problems/longest-palindromic-substring/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def longestPalindrome(self, s):
        ans = ""
        i = 0
        while i < len(s):
            j = i
            while j < len(s):
                sub = s[i:j + 1]
                if self.isPalindrome(sub) and len(sub) > len(ans):
                    ans = sub
                j = j + 1
            i = i + 1
        return ans
    def isPalindrome(self, string):
        l = 0
        r = len(string) - 1
        while l < r:
            if string[l] != string[r]:
                return False
            l = l + 1
            r = r - 1
        return True
```

## 646. Maximum Length of Pair Chain
- [x] Check 
```embed
title: "Maximum Length of Pair Chain - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Maximum Length of Pair Chain - You are given an array of n pairs pairs where pairs[i] = [lefti, righti] and lefti < righti.  A pair p2 = [c, d] follows a pair p1 = [a, b] if b < c. A chain of pairs can be formed in this fashion.  Return the length longest chain which can be formed.  You do not need to use up all the given intervals. You can select pairs in any order.     Example 1:   Input: pairs = [[1,2],[2,3],[3,4]] Output: 2 Explanation: The longest chain is [1,2] -> [3,4].   Example 2:   Input: pairs = [[1,2],[7,8],[4,5]] Output: 3 Explanation: The longest chain is [1,2] -> [4,5] -> [7,8].      Constraints:   * n == pairs.length  * 1 <= n <= 1000  * -1000 <= lefti < righti <= 1000"
url: "https://leetcode.com/problems/maximum-length-of-pair-chain/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def findLongestChain(self, pairs):
        pairs.sort(key=lambda x: x[1])
        count = 1
        last_end = pairs[0][1]
        i = 1
        while i < len(pairs):
            if pairs[i][0] > last_end:
                count = count + 1
                last_end = pairs[i][1]
            i = i + 1
        return count
```

## 21. Merge Two Sorted Lists
- [x] Check 
### Linked List Manipulation

```embed
title: "Merge Two Sorted Lists - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Merge Two Sorted Lists - You are given the heads of two sorted linked lists list1 and list2.  Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.  Return the head of the merged linked list.     Example 1:  [https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg]   Input: list1 = [1,2,4], list2 = [1,3,4] Output: [1,1,2,3,4,4]   Example 2:   Input: list1 = [], list2 = [] Output: []   Example 3:   Input: list1 = [], list2 = [0] Output: [0]      Constraints:   * The number of nodes in both lists is in the range [0, 50].  * -100 <= Node.val <= 100  * Both list1 and list2 are sorted in non-decreasing order."
url: "https://leetcode.com/problems/merge-two-sorted-lists/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def mergeTwoLists(self, list1, list2):
        dummy = ListNode(0)
        tail = dummy
        while list1 is not None and list2 is not None:
            if list1.val < list2.val:
                tail.next = list1
                list1 = list1.next
            else:
                tail.next = list2
                list2 = list2.next
            tail = tail.next
        if list1 is not None:
            tail.next = list1
        else:
            tail.next = list2
        return dummy.next
```

## 234. Palindrome Linked List
- [x] Check 
### Linked List/Two Pointers

```embed
title: "Palindrome Linked List - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Palindrome Linked List - Given the head of a singly linked list, return true if it is a palindrome or false otherwise.     Example 1:  [https://assets.leetcode.com/uploads/2021/03/03/pal1linked-list.jpg]   Input: head = [1,2,2,1] Output: true   Example 2:  [https://assets.leetcode.com/uploads/2021/03/03/pal2linked-list.jpg]   Input: head = [1,2] Output: false      Constraints:   * The number of nodes in the list is in the range [1, 105].  * 0 <= Node.val <= 9     Follow up: Could you do it in O(n) time and O(1) space?"
url: "https://leetcode.com/problems/palindrome-linked-list/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def isPalindrome(self, head):
        if head is None or head.next is None:
            return True
        slow = head
        fast = head
        while fast is not None and fast.next is not None:
            slow = slow.next
            fast = fast.next.next
        second = self.reverse(slow)
        first = head
        while second is not None:
            if first.val != second.val:
                return False
            first = first.next
            second = second.next
        return True
    def reverse(self, head):
        prev = None
        curr = head
        while curr is not None:
            next_node = curr.next
            curr.next = prev
            prev = curr
            curr = next_node
        return prev
```