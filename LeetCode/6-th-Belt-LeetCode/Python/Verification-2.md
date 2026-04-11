## 1. Container With Most Water

```embed
title: "Container With Most Water - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Container With Most Water - You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).  Find two lines that together with the x-axis form a container, such that the container contains the most water.  Return the maximum amount of water a container can store.  Notice that you may not slant the container.     Example 1:  [https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg]   Input: height = [1,8,6,2,5,4,8,3,7] Output: 49 Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.   Example 2:   Input: height = [1,1] Output: 1      Constraints:   * n == height.length  * 2 <= n <= 105  * 0 <= height[i] <= 104"
url: "https://leetcode.com/problems/container-with-most-water/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution(object):
    def maxArea(self, height):
        left = 0
        right = len(height) - 1
        max_water = 0
        while left < right:
            h = min(height[left], height[right])
            width = right - left
            area = h * width
            max_water = max(max_water, area)
            if height[left] < height[right]:
                left += 1
            else:
                right -= 1
        return max_water
```

| Complexity Type | Value |
| --------------- | ----- |
| Time            | O(n)  |
| Space           | O(1)  |
## 2. Trapping Rain Water

```embed
title: "Trapping Rain Water - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Trapping Rain Water - Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.     Example 1:  [https://assets.leetcode.com/uploads/2018/10/22/rainwatertrap.png]   Input: height = [0,1,0,2,1,0,1,3,2,1,2,1] Output: 6 Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.   Example 2:   Input: height = [4,2,0,3,2,5] Output: 9      Constraints:   * n == height.length  * 1 <= n <= 2 * 104  * 0 <= height[i] <= 105"
url: "https://leetcode.com/problems/trapping-rain-water/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution(object):
    def trap(self, height):
        left = 0
        right = len(height) - 1
        left_max = 0
        right_max = 0
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
```

| Complexity Type | Value |
| --------------- | ----- |
| Time            | O(n)  |
| Space           | O(1)  |
## 3. Sliding Window Maximum

```embed
title: "Sliding Window Maximum - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Sliding Window Maximum - You are given an array of integers nums, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position.  Return the max sliding window.     Example 1:   Input: nums = [1,3,-1,-3,5,3,6,7], k = 3 Output: [3,3,5,5,6,7] Explanation:  Window position                Max ---------------               ----- [1  3  -1] -3  5  3  6  7       3  1 [3  -1  -3] 5  3  6  7       3  1  3 [-1  -3  5] 3  6  7       5  1  3  -1 [-3  5  3] 6  7       5  1  3  -1  -3 [5  3  6] 7       6  1  3  -1  -3  5 [3  6  7]      7   Example 2:   Input: nums = [1], k = 1 Output: [1]      Constraints:   * 1 <= nums.length <= 105  * -104 <= nums[i] <= 104  * 1 <= k <= nums.length"
url: "https://leetcode.com/problems/sliding-window-maximum/description/"
favicon: ""
aspectRatio: "52"
```

```python
from collections import deque
class Solution:
    def maxSlidingWindow(self, nums, k):
        n = len(nums)
        result = [0] * (n - k + 1)
        dq = deque()
        for i in range(n):
            if dq and dq[0] == i - k:
                dq.popleft()
            while dq and nums[dq[-1]] < nums[i]:
                dq.pop()
            dq.append(i)
            if i >= k - 1:
                result[i - k + 1] = nums[dq[0]]
        return result
```

| Complexity Type | Value |
| --------------- | ----- |
| Time            | O(n)  |
| Space           | O(k)  |
## 4. Next Greater Element I

```embed
title: "Next Greater Element I - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Next Greater Element I - The next greater element of some element x in an array is the first greater element that is to the right of x in the same array.  You are given two distinct 0-indexed integer arrays nums1 and nums2, where nums1 is a subset of nums2.  For each 0 <= i < nums1.length, find the index j such that nums1[i] == nums2[j] and determine the next greater element of nums2[j] in nums2. If there is no next greater element, then the answer for this query is -1.  Return an array ans of length nums1.length such that ans[i] is the next greater element as described above.     Example 1:   Input: nums1 = [4,1,2], nums2 = [1,3,4,2] Output: [-1,3,-1] Explanation: The next greater element for each value of nums1 is as follows: - 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1. - 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3. - 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.   Example 2:   Input: nums1 = [2,4], nums2 = [1,2,3,4] Output: [3,-1] Explanation: The next greater element for each value of nums1 is as follows: - 2 is underlined in nums2 = [1,2,3,4]. The next greater element is 3. - 4 is underlined in nums2 = [1,2,3,4]. There is no next greater element, so the answer is -1.      Constraints:   * 1 <= nums1.length <= nums2.length <= 1000  * 0 <= nums1[i], nums2[i] <= 104  * All integers in nums1 and nums2 are unique.  * All the integers of nums1 also appear in nums2.     Follow up: Could you find an O(nums1.length + nums2.length) solution?"
url: "https://leetcode.com/problems/next-greater-element-i/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution(object):
    def nextGreaterElement(self, nums1, nums2):
        stack = []
        mp = {}
        for num in nums2:
            while stack and stack[-1] < num:
                mp[stack.pop()] = num
            stack.append(num)
        while stack:
            mp[stack.pop()] = -1
        return [mp[num] for num in nums1]
```

| Complexity Type | Value    |
| --------------- | -------- |
| Time            | O(n + m) |
| Space           | O(n)     |
## 5. Remove K Digits

```embed
title: "Remove K Digits - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Remove K Digits - Given string num representing a non-negative integer num, and an integer k, return the smallest possible integer after removing k digits from num.     Example 1:   Input: num = \"1432219\", k = 3 Output: \"1219\" Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.   Example 2:   Input: num = \"10200\", k = 1 Output: \"200\" Explanation: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.   Example 3:   Input: num = \"10\", k = 2 Output: \"0\" Explanation: Remove all the digits from the number and it is left with nothing which is 0.      Constraints:   * 1 <= k <= num.length <= 105  * num consists of only digits.  * num does not have any leading zeros except for the zero itself."
url: "https://leetcode.com/problems/remove-k-digits/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution(object):
    def removeKdigits(self, num, k):
        stack = []
        for c in num:
            while stack and k > 0 and stack[-1] > c:
                stack.pop()
                k -= 1
            stack.append(c)
        while stack and k > 0:
            stack.pop()
            k -= 1
        result = ''.join(stack).lstrip('0')
        return result if result else "0"
```

| Complexity Type | Value |
| --------------- | ----- |
| Time            | O(n)  |
| Space           | O(n)  |
## 6. Pow(x, n)

```embed
title: "Pow(x, n) - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Pow(x, n) - Implement pow(x, n) [http://www.cplusplus.com/reference/valarray/pow/], which calculates x raised to the power n (i.e., xn).     Example 1:   Input: x = 2.00000, n = 10 Output: 1024.00000   Example 2:   Input: x = 2.10000, n = 3 Output: 9.26100   Example 3:   Input: x = 2.00000, n = -2 Output: 0.25000 Explanation: 2-2 = 1/22 = 1/4 = 0.25      Constraints:   * -100.0 < x < 100.0  * -231 <= n <= 231-1  * n is an integer.  * Either x is not zero or n > 0.  * -104 <= xn <= 104"
url: "https://leetcode.com/problems/powx-n/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def myPow(self, x, n):
        pow_val = n
        if pow_val < 0:
            x = 1.0 / x
            pow_val = -pow_val
        return self.fastPow(x, pow_val)
    def fastPow(self, x, n):
        if n == 0:
            return 1.0
        half = self.fastPow(x, n // 2)
        if n % 2 == 0:
            return half * half
        else:
            return half * half * x
```

| Complexity Type | Value    |
| --------------- | -------- |
| Time            | O(log n) |
| Space           | O(log n) |
## 7. 3Sum Closest

```embed
title: "3Sum Closest - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? 3Sum Closest - Given an integer array nums of length n and an integer target, find three integers at distinct indices in nums such that the sum is closest to target.  Return the sum of the three integers.  You may assume that each input would have exactly one solution.     Example 1:   Input: nums = [-1,2,1,-4], target = 1 Output: 2 Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).   Example 2:   Input: nums = [0,0,0], target = 1 Output: 0 Explanation: The sum that is closest to the target is 0. (0 + 0 + 0 = 0).      Constraints:   * 3 <= nums.length <= 500  * -1000 <= nums[i] <= 1000  * -104 <= target <= 104"
url: "https://leetcode.com/problems/3sum-closest/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution(object):
    def threeSumClosest(self, nums, target):
        nums.sort()
        n = len(nums)
        closest_sum = nums[0] + nums[1] + nums[2]
        for i in range(n - 2):
            left = i + 1
            right = n - 1
            while left < right:
                current_sum = nums[i] + nums[left] + nums[right]
                if abs(target - current_sum) < abs(target - closest_sum):
                    closest_sum = current_sum
                if current_sum < target:
                    left += 1
                elif current_sum > target:
                    right -= 1
                else:
                    return current_sum  
        return closest_sum
```

| Complexity Type | Value |
| --------------- | ----- |
| Time            | O(n²) |
| Space           | O(1)  |
## 8. Sum of Subarray Ranges

```embed
title: "Sum of Subarray Ranges - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Sum of Subarray Ranges - You are given an integer array nums. The range of a subarray of nums is the difference between the largest and smallest element in the subarray.  Return the sum of all subarray ranges of nums.  A subarray is a contiguous non-empty sequence of elements within an array.     Example 1:   Input: nums = [1,2,3] Output: 4 Explanation: The 6 subarrays of nums are the following: [1], range = largest - smallest = 1 - 1 = 0  [2], range = 2 - 2 = 0 [3], range = 3 - 3 = 0 [1,2], range = 2 - 1 = 1 [2,3], range = 3 - 2 = 1 [1,2,3], range = 3 - 1 = 2 So the sum of all ranges is 0 + 0 + 0 + 1 + 1 + 2 = 4.  Example 2:   Input: nums = [1,3,3] Output: 4 Explanation: The 6 subarrays of nums are the following: [1], range = largest - smallest = 1 - 1 = 0 [3], range = 3 - 3 = 0 [3], range = 3 - 3 = 0 [1,3], range = 3 - 1 = 2 [3,3], range = 3 - 3 = 0 [1,3,3], range = 3 - 1 = 2 So the sum of all ranges is 0 + 0 + 0 + 2 + 0 + 2 = 4.   Example 3:   Input: nums = [4,-2,-3,4,1] Output: 59 Explanation: The sum of all subarray ranges of nums is 59.      Constraints:   * 1 <= nums.length <= 1000  * -109 <= nums[i] <= 109     Follow-up: Could you find a solution with O(n) time complexity?"
url: "https://leetcode.com/problems/sum-of-subarray-ranges/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution(object):
    def subArrayRanges(self, nums):
        n = len(nums)
        total = 0
        for i in range(n):
            mini = nums[i]
            maxi = nums[i]
            for j in range(i, n):
                mini = min(mini, nums[j])
                maxi = max(maxi, nums[j])
                total += (maxi - mini)
        return total
```

| Complexity Type | Value |
| --------------- | ----- |
| Time            | O(n²) |
| Space           | O(1)  |
## 9. Moving Stones Until Consecutive II

```embed
title: "Moving Stones Until Consecutive II - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Moving Stones Until Consecutive II - There are some stones in different positions on the X-axis. You are given an integer array stones, the positions of the stones.  Call a stone an endpoint stone if it has the smallest or largest position. In one move, you pick up an endpoint stone and move it to an unoccupied position so that it is no longer an endpoint stone.   * In particular, if the stones are at say, stones = [1,2,5], you cannot move the endpoint stone at position 5, since moving it to any position (such as 0, or 3) will still keep that stone as an endpoint stone.  The game ends when you cannot make any more moves (i.e., the stones are in three consecutive positions).  Return an integer array answer of length 2 where:   * answer[0] is the minimum number of moves you can play, and  * answer[1] is the maximum number of moves you can play.     Example 1:   Input: stones = [7,4,9] Output: [1,2] Explanation: We can move 4 -> 8 for one move to finish the game. Or, we can move 9 -> 5, 4 -> 6 for two moves to finish the game.   Example 2:   Input: stones = [6,5,4,3,10] Output: [2,3] Explanation: We can move 3 -> 8 then 10 -> 7 to finish the game. Or, we can move 3 -> 7, 4 -> 8, 5 -> 9 to finish the game. Notice we cannot move 10 -> 2 to finish the game, because that would be an illegal move.      Constraints:   * 3 <= stones.length <= 104  * 1 <= stones[i] <= 109  * All the values of stones are unique."
url: "https://leetcode.com/problems/moving-stones-until-consecutive-ii/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution(object):
    def numMovesStonesII(self, stones):
	    stones.sort()
        n = len(stones)
        max1 = stones[n - 1] - stones[1] - (n - 2)
        max2 = stones[n - 2] - stones[0] - (n - 2)
        maxMoves = max(max1, max2)
        minMoves = float("inf")
        j = 0
        for i in range(n):
            while j + 1 < n and stones[j + 1] - stones[i] + 1 <= n:
                j += 1
            stonesInWindow = j - i + 1
            if stonesInWindow == n - 1 and stones[j] - stones[i] + 1 == n - 1:
                minMoves = min(minMoves, 2)
            else:
                minMoves = min(minMoves, n - stonesInWindow)
        return [minMoves, maxMoves]
```

| Complexity Type | Value      |
| --------------- | ---------- |
| Time            | O(n log n) |
| Space           | O(1)       |
## 10. Remove Nth Node From End of List

```embed
title: "Remove Nth Node From End of List - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Remove Nth Node From End of List - Given the head of a linked list, remove the nth node from the end of the list and return its head.     Example 1:  [https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg]   Input: head = [1,2,3,4,5], n = 2 Output: [1,2,3,5]   Example 2:   Input: head = [1], n = 1 Output: []   Example 3:   Input: head = [1,2], n = 1 Output: [1]      Constraints:   * The number of nodes in the list is sz.  * 1 <= sz <= 30  * 0 <= Node.val <= 100  * 1 <= n <= sz     Follow up: Could you do this in one pass?"
url: "https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution(object):
    def removeNthFromEnd(self, head, n):
        dummy = ListNode(0)
        dummy.next = head
        fast = dummy
        slow = dummy
        for _ in range(n + 1):
            fast = fast.next
        while fast is not None:
            fast = fast.next
            slow = slow.next
        slow.next = slow.next.next     
        return dummy.next
```

| Complexity Type | Value |
| --------------- | ----- |
| Time            | O(n)  |
| Space           | O(1)  |
## 11. Longest Increasing Subsequence

```embed
title: "Longest Increasing Subsequence - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Longest Increasing Subsequence - Given an integer array nums, return the length of the longest strictly increasing subsequence.     Example 1:   Input: nums = [10,9,2,5,3,7,101,18] Output: 4 Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.   Example 2:   Input: nums = [0,1,0,3,2,3] Output: 4   Example 3:   Input: nums = [7,7,7,7,7,7,7] Output: 1      Constraints:   * 1 <= nums.length <= 2500  * -104 <= nums[i] <= 104     Follow up: Can you come up with an algorithm that runs in O(n log(n)) time complexity?"
url: "https://leetcode.com/problems/longest-increasing-subsequence/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def lengthOfLIS(self, nums):
        dp = [0] * len(nums) 
        length = 0
        for num in nums:
            left = 0
            right = length
            while left < right:
                mid = (left + right) // 2
                if dp[mid] < num:
                    left = mid + 1
                else:
                    right = mid
            dp[left] = num
            if left == length:
                length += 1
        return length
```

|Complexity Type|Value|
|---|---|
|Time|O(n log n)|
|Space|O(n)|
## 12. Restore IP Addresses

```embed
title: "Restore IP Addresses - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Restore IP Addresses - A valid IP address consists of exactly four integers separated by single dots. Each integer is between 0 and 255 (inclusive) and cannot have leading zeros.   * For example, \"0.1.2.201\" and \"192.168.1.1\" are valid IP addresses, but \"0.011.255.245\", \"192.168.1.312\" and \"192.168@1.1\" are invalid IP addresses.  Given a string s containing only digits, return all possible valid IP addresses that can be formed by inserting dots into s. You are not allowed to reorder or remove any digits in s. You may return the valid IP addresses in any order.     Example 1:   Input: s = \"25525511135\" Output: [\"255.255.11.135\",\"255.255.111.35\"]   Example 2:   Input: s = \"0000\" Output: [\"0.0.0.0\"]   Example 3:   Input: s = \"101023\" Output: [\"1.0.10.23\",\"1.0.102.3\",\"10.1.0.23\",\"10.10.2.3\",\"101.0.2.3\"]      Constraints:   * 1 <= s.length <= 20  * s consists of digits only."
url: "https://leetcode.com/problems/restore-ip-addresses/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution(object):
    def restoreIpAddresses(self, s):
        result = []   
        def backtrack(start, path):
            if len(path) == 4 and start == len(s):
                result.append(".".join(path))
                return
            if len(path) == 4:
                return
            for length in range(1, 4): 
                if start + length > len(s):
                    break
                part = s[start:start + length]
                if (part.startswith('0') and len(part) > 1) or int(part) > 255:
                    continue
                backtrack(start + length, path + [part])
        backtrack(0, [])
        return result
```

| Complexity Type | Value |
| --------------- | ----- |
| Time            | O(1)  |
| Space           | O(1)  |
## 13. Permutation Sequence

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

|Complexity Type|Value|
|---|---|
|Time|O(n²)|
|Space|O(n)|
## 14. Sum of Subarray Minimums

```embed
title: "Sum of Subarray Minimums - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Sum of Subarray Minimums - Given an array of integers arr, find the sum of min(b), where b ranges over every (contiguous) subarray of arr. Since the answer may be large, return the answer modulo 109 + 7.     Example 1:   Input: arr = [3,1,2,4] Output: 17 Explanation:  Subarrays are [3], [1], [2], [4], [3,1], [1,2], [2,4], [3,1,2], [1,2,4], [3,1,2,4].  Minimums are 3, 1, 2, 4, 1, 1, 2, 1, 1, 1. Sum is 17.   Example 2:   Input: arr = [11,81,94,43,3] Output: 444      Constraints:   * 1 <= arr.length <= 3 * 104  * 1 <= arr[i] <= 3 * 104"
url: "https://leetcode.com/problems/sum-of-subarray-minimums/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution(object):
    def sumSubarrayMins(self, arr):
        mod = 10**9 + 7
        n = len(arr)
        stack = []
        result = 0
        for i in range(n + 1):
            while stack and (i == n or arr[stack[-1]] > arr[i]):
                mid = stack.pop()
                left = stack[-1] if stack else -1
                right = i
                count = (mid - left) * (right - mid)
                result += arr[mid] * count
            stack.append(i)
        
        return result % mod
```
## 15. Rat in a Maze

```embed
title: "Rat in a Maze | Practice | GeeksforGeeks "
image: "https://media.geeksforgeeks.org/wp-content/cdn-uploads/gfg_200x200-min.png"
description: "Consider a rat placed at position (0, 0) in an n x n square matrix maze[][]. The rat's goal is to reach the destination at position (n-1, n-1). The rat can move in four possible directions:&nbsp;'U'(up),&nbsp;'D'(down),&nbsp;'L' (left),&nbsp;'R' (rig"
url: "https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1"
favicon: ""
aspectRatio: "100"
```

```python
class Solution:
    def ratInMaze(self, maze):
        n = len(maze)
        result = []
        directions = [(1, 0, 'D'), (0, -1, 'L'), (0, 1, 'R'), (-1, 0, 'U')]
        visited = [[False] * n for _ in range(n)]
        def backtrack(x, y, path):
            if x == n - 1 and y == n - 1:
                result.append(path)
                return
            for dx, dy, move in directions:
                nx, ny = x + dx, y + dy
                if (0 <= nx < n and 0 <= ny < n and
                    not visited[nx][ny] and maze[nx][ny] == 1):
                    visited[nx][ny] = True
                    backtrack(nx, ny, path + move)
                    visited[nx][ny] = False 
        if maze[0][0] == 1:
            visited[0][0] = True
            backtrack(0, 0, "")
        
        return sorted(result)
```