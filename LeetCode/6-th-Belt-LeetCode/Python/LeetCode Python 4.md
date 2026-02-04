# Binary Search
## 875. Koko Eating Bananas
- [ ] Check 
```embed
title: "Koko Eating Bananas - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Koko Eating Bananas - Koko loves to eat bananas. There are n piles of bananas, the ith pile has piles[i] bananas. The guards have gone and will come back in h hours.  Koko can decide her bananas-per-hour eating speed of k. Each hour, she chooses some pile of bananas and eats k bananas from that pile. If the pile has less than k bananas, she eats all of them instead and will not eat any more bananas during this hour.  Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.  Return the minimum integer k such that she can eat all the bananas within h hours.     Example 1:   Input: piles = [3,6,7,11], h = 8 Output: 4   Example 2:   Input: piles = [30,11,23,4,20], h = 5 Output: 30   Example 3:   Input: piles = [30,11,23,4,20], h = 6 Output: 23      Constraints:   * 1 <= piles.length <= 104  * piles.length <= h <= 109  * 1 <= piles[i] <= 109"
url: "https://leetcode.com/problems/koko-eating-bananas/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def minEatingSpeed(self, piles, h):
        left = 1
        right = 0
        for p in piles:
            if p > right:
                right = p
        while left < right:
            mid = (left + right) // 2
            hours = 0
            for p in piles:
                hours += (p + mid - 1) // mid
            if hours <= h:
                right = mid
            else:
                left = mid + 1
        return left
```

## 1802. Maximum Value at a Given Index in a Bounded Array
- [ ] Check 
```embed
title: "Maximum Value at a Given Index in a Bounded Array - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Maximum Value at a Given Index in a Bounded Array - You are given three positive integers: n, index, and maxSum. You want to construct an array nums (0-indexed) that satisfies the following conditions:   * nums.length == n  * nums[i] is a positive integer where 0 <= i < n.  * abs(nums[i] - nums[i+1]) <= 1 where 0 <= i < n-1.  * The sum of all the elements of nums does not exceed maxSum.  * nums[index] is maximized.  Return nums[index] of the constructed array.  Note that abs(x) equals x if x >= 0, and -x otherwise.     Example 1:   Input: n = 4, index = 2,  maxSum = 6 Output: 2 Explanation: nums = [1,2,2,1] is one array that satisfies all the conditions. There are no arrays that satisfy all the conditions and have nums[2] == 3, so 2 is the maximum nums[2].   Example 2:   Input: n = 6, index = 1,  maxSum = 10 Output: 3      Constraints:   * 1 <= n <= maxSum <= 109  * 0 <= index < n"
url: "https://leetcode.com/problems/maximum-value-at-a-given-index-in-a-bounded-array/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def maxValue(self, n, index, maxSum):
        low = 1
        high = maxSum
        while low < high:
            mid = (low + high + 1) // 2
            if self.valid(n, index, maxSum, mid):
                low = mid
            else:
                high = mid - 1
        return low
    def valid(self, n, index, maxSum, val):
        total = val
        total += self.sideSum(val - 1, index)          
        total += self.sideSum(val - 1, n - index - 1)  
        return total <= maxSum
    def sideSum(self, peak, length):
        if length <= peak:
            return (peak + peak - length + 1) * length // 2
        return (peak + 1) * peak // 2 + (length - peak)
```

## 2300. Successful Pairs of Spells and Potions
- [ ] Check 
```embed
title: "Successful Pairs of Spells and Potions - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Successful Pairs of Spells and Potions - You are given two positive integer arrays spells and potions, of length n and m respectively, where spells[i] represents the strength of the ith spell and potions[j] represents the strength of the jth potion.  You are also given an integer success. A spell and potion pair is considered successful if the product of their strengths is at least success.  Return an integer array pairs of length n where pairs[i] is the number of potions that will form a successful pair with the ith spell.     Example 1:   Input: spells = [5,1,3], potions = [1,2,3,4,5], success = 7 Output: [4,0,3] Explanation: - 0th spell: 5 * [1,2,3,4,5] = [5,10,15,20,25]. 4 pairs are successful. - 1st spell: 1 * [1,2,3,4,5] = [1,2,3,4,5]. 0 pairs are successful. - 2nd spell: 3 * [1,2,3,4,5] = [3,6,9,12,15]. 3 pairs are successful. Thus, [4,0,3] is returned.   Example 2:   Input: spells = [3,1,2], potions = [8,5,8], success = 16 Output: [2,0,2] Explanation: - 0th spell: 3 * [8,5,8] = [24,15,24]. 2 pairs are successful. - 1st spell: 1 * [8,5,8] = [8,5,8]. 0 pairs are successful.  - 2nd spell: 2 * [8,5,8] = [16,10,16]. 2 pairs are successful.  Thus, [2,0,2] is returned.      Constraints:   * n == spells.length  * m == potions.length  * 1 <= n, m <= 105  * 1 <= spells[i], potions[i] <= 105  * 1 <= success <= 1010"
url: "https://leetcode.com/problems/successful-pairs-of-spells-and-potions/description/"
favicon: ""
aspectRatio: "52"
```

```python 
class Solution:
    def successfulPairs(self, spells, potions, success):
        potions.sort()
        n = len(potions)
        ans = [0] * len(spells)
        for i in range(len(spells)):
            spell = spells[i]
            need = (success + spell - 1) // spell
            left = 0
            right = n - 1
            idx = n 
            while left <= right:
                mid = (left + right) // 2
                if potions[mid] >= need:
                    idx = mid
                    right = mid - 1
                else:
                    left = mid + 1
            ans[i] = n - idx  
        return ans
```

## 300. Longest Increasing Subsequence
- [ ] Check 
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

# Sliding Window
## 567. Permutation in String
- [ ] Check 
```embed
title: "Permutation in String - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Permutation in String - Given two strings s1 and s2, return true if s2 contains a permutation of s1, or false otherwise.  In other words, return true if one of s1's permutations is the substring of s2.     Example 1:   Input: s1 = \"ab\", s2 = \"eidbaooo\" Output: true Explanation: s2 contains one permutation of s1 (\"ba\").   Example 2:   Input: s1 = \"ab\", s2 = \"eidboaoo\" Output: false      Constraints:   * 1 <= s1.length, s2.length <= 104  * s1 and s2 consist of lowercase English letters."
url: "https://leetcode.com/problems/permutation-in-string/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def checkInclusion(self, s1, s2):
        if len(s1) > len(s2):
            return False
        freq1 = [0] * 26
        freq2 = [0] * 26
        letters = "abcdefghijklmnopqrstuvwxyz"
        for c in s1:
            idx = letters.index(c)
            freq1[idx] += 1
        k = len(s1)
        for i in range(len(s2)):
            idx_add = letters.index(s2[i])
            freq2[idx_add] += 1
            if i >= k:
                idx_remove = letters.index(s2[i - k])
                freq2[idx_remove] -= 1
            if self.matches(freq1, freq2):
                return True
        return False
    def matches(self, a, b):
        for i in range(26):
            if a[i] != b[i]:
                return False
        return True
```

## 904. Fruit Into Baskets
- [ ] Check 
```embed
title: "Fruit Into Baskets - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Fruit Into Baskets - You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.  You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:   * You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold.  * Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.  * Once you reach a tree with fruit that cannot fit in your baskets, you must stop.  Given the integer array fruits, return the maximum number of fruits you can pick.     Example 1:   Input: fruits = [1,2,1] Output: 3 Explanation: We can pick from all 3 trees.   Example 2:   Input: fruits = [0,1,2,2] Output: 3 Explanation: We can pick from trees [1,2,2]. If we had started at the first tree, we would only pick from trees [0,1].   Example 3:   Input: fruits = [1,2,3,2,2] Output: 4 Explanation: We can pick from trees [2,3,2,2]. If we had started at the first tree, we would only pick from trees [1,2].      Constraints:   * 1 <= fruits.length <= 105  * 0 <= fruits[i] < fruits.length"
url: "https://leetcode.com/problems/fruit-into-baskets/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def totalFruit(self, fruits):
        count_map = {}
        left = 0
        max_len = 0
        for right in range(len(fruits)):
            fruit = fruits[right]
            if fruit in count_map:
                count_map[fruit] += 1
            else:
                count_map[fruit] = 1
            while len(count_map) > 2:
                left_fruit = fruits[left]
                count_map[left_fruit] -= 1
                if count_map[left_fruit] == 0:
                    del count_map[left_fruit]
                left += 1
            window_len = right - left + 1
            if window_len > max_len:
                max_len = window_len
        return max_len
```

## 2024. Maximize the Confusion of an Exam
- [ ] Check 
```embed
title: "Maximize the Confusion of an Exam - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Maximize the Confusion of an Exam - A teacher is writing a test with n true/false questions, with 'T' denoting true and 'F' denoting false. He wants to confuse the students by maximizing the number of consecutive questions with the same answer (multiple trues or multiple falses in a row).  You are given a string answerKey, where answerKey[i] is the original answer to the ith question. In addition, you are given an integer k, the maximum number of times you may perform the following operation:   * Change the answer key for any question to 'T' or 'F' (i.e., set answerKey[i] to 'T' or 'F').  Return the maximum number of consecutive 'T's or 'F's in the answer key after performing the operation at most k times.     Example 1:   Input: answerKey = \"TTFF\", k = 2 Output: 4 Explanation: We can replace both the 'F's with 'T's to make answerKey = \"TTTT\". There are four consecutive 'T's.   Example 2:   Input: answerKey = \"TFFT\", k = 1 Output: 3 Explanation: We can replace the first 'T' with an 'F' to make answerKey = \"FFFT\". Alternatively, we can replace the second 'T' with an 'F' to make answerKey = \"TFFF\". In both cases, there are three consecutive 'F's.   Example 3:   Input: answerKey = \"TTFTTFTT\", k = 1 Output: 5 Explanation: We can replace the first 'F' to make answerKey = \"TTTTTFTT\" Alternatively, we can replace the second 'F' to make answerKey = \"TTFTTTTT\".  In both cases, there are five consecutive 'T's.      Constraints:   * n == answerKey.length  * 1 <= n <= 5 * 104  * answerKey[i] is either 'T' or 'F'  * 1 <= k <= n"
url: "https://leetcode.com/problems/maximize-the-confusion-of-an-exam/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def maxConsecutiveAnswers(self, answerKey, k):
        return max(
            self.maxWithChar(answerKey, k, 'T'),
            self.maxWithChar(answerKey, k, 'F')
        )
    def maxWithChar(self, s, k, ch):
        left = 0
        max_len = 0
        flips = 0
        for right in range(len(s)):
            if s[right] != ch:
                flips += 1
            while flips > k:
                if s[left] != ch:
                    flips -= 1
                left += 1
            window_len = right - left + 1
            if window_len > max_len:
                max_len = window_len
        return max_len
```

## 1004. Max Consecutive Ones III
- [ ] Check 
```embed
title: "Max Consecutive Ones III - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Max Consecutive Ones III - Given a binary array nums and an integer k, return the maximum number of consecutive 1's in the array if you can flip at most k 0's.     Example 1:   Input: nums = [1,1,1,0,0,0,1,1,1,1,0], k = 2 Output: 6 Explanation: [1,1,1,0,0,1,1,1,1,1,1] Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.  Example 2:   Input: nums = [0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1], k = 3 Output: 10 Explanation: [0,0,1,1,1,1,1,1,1,1,1,1,0,0,0,1,1,1,1] Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.      Constraints:   * 1 <= nums.length <= 105  * nums[i] is either 0 or 1.  * 0 <= k <= nums.length"
url: "https://leetcode.com/problems/max-consecutive-ones-iii/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def longestOnes(self, nums, k):
        left = 0
        max_len = 0
        zero_count = 0
        for right in range(len(nums)):
            if nums[right] == 0:
                zero_count += 1
            while zero_count > k:
                if nums[left] == 0:
                    zero_count -= 1
                left += 1
            window_len = right - left + 1
            if window_len > max_len:
                max_len = window_len
        return max_len
```

# Sliding Window/Deque

## 239. Sliding Window Maximum
- [ ] Check 
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

