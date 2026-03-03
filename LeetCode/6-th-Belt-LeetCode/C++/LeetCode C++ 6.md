# Two Pointers

## 11. Container With Most Water
- [ ] Check 
```embed
title: "Container With Most Water - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Container With Most Water - You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).  Find two lines that together with the x-axis form a container, such that the container contains the most water.  Return the maximum amount of water a container can store.  Notice that you may not slant the container.     Example 1:  [https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg]   Input: height = [1,8,6,2,5,4,8,3,7] Output: 49 Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.   Example 2:   Input: height = [1,1] Output: 1      Constraints:   * n == height.length  * 2 <= n <= 105  * 0 <= height[i] <= 104"
url: "https://leetcode.com/problems/container-with-most-water/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 838. Push Dominoes
- [ ] Check 
```embed
title: "Push Dominoes - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Push Dominoes - There are n dominoes in a line, and we place each domino vertically upright. In the beginning, we simultaneously push some of the dominoes either to the left or to the right.  After each second, each domino that is falling to the left pushes the adjacent domino on the left. Similarly, the dominoes falling to the right push their adjacent dominoes standing on the right.  When a vertical domino has dominoes falling on it from both sides, it stays still due to the balance of the forces.  For the purposes of this question, we will consider that a falling domino expends no additional force to a falling or already fallen domino.  You are given a string dominoes representing the initial state where:   * dominoes[i] = 'L', if the ith domino has been pushed to the left,  * dominoes[i] = 'R', if the ith domino has been pushed to the right, and  * dominoes[i] = '.', if the ith domino has not been pushed.  Return a string representing the final state.     Example 1:   Input: dominoes = \"RR.L\" Output: \"RR.L\" Explanation: The first domino expends no additional force on the second domino.   Example 2:  [https://s3-lc-upload.s3.amazonaws.com/uploads/2018/05/18/domino.png]   Input: dominoes = \".L.R...LR..L..\" Output: \"LL.RR.LLRRLL..\"      Constraints:   * n == dominoes.length  * 1 <= n <= 105  * dominoes[i] is either 'L', 'R', or '.'."
url: "https://leetcode.com/problems/push-dominoes/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

##  881. Boats to Save People
- [ ] Check 
```embed
title: "Boats to Save People - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Boats to Save People - You are given an array people where people[i] is the weight of the ith person, and an infinite number of boats where each boat can carry a maximum weight of limit. Each boat carries at most two people at the same time, provided the sum of the weight of those people is at most limit.  Return the minimum number of boats to carry every given person.     Example 1:   Input: people = [1,2], limit = 3 Output: 1 Explanation: 1 boat (1, 2)   Example 2:   Input: people = [3,2,2,1], limit = 3 Output: 3 Explanation: 3 boats (1, 2), (2) and (3)   Example 3:   Input: people = [3,5,3,4], limit = 5 Output: 4 Explanation: 4 boats (3), (3), (4), (5)      Constraints:   * 1 <= people.length <= 5 * 104  * 1 <= people[i] <= limit <= 3 * 104"
url: "https://leetcode.com/problems/boats-to-save-people/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 795. Number of Subarrays with Bounded Maximum
- [ ] Check 
```embed
title: "Number of Subarrays with Bounded Maximum - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Number of Subarrays with Bounded Maximum - Given an integer array nums and two integers left and right, return the number of contiguous non-empty subarrays such that the value of the maximum array element in that subarray is in the range [left, right].  The test cases are generated so that the answer will fit in a 32-bit integer.     Example 1:   Input: nums = [2,1,4,3], left = 2, right = 3 Output: 3 Explanation: There are three subarrays that meet the requirements: [2], [2, 1], [3].   Example 2:   Input: nums = [2,9,2,5,6], left = 2, right = 8 Output: 7      Constraints:   * 1 <= nums.length <= 105  * 0 <= nums[i] <= 109  * 0 <= left <= right <= 109"
url: "https://leetcode.com/problems/number-of-subarrays-with-bounded-maximum/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 3Sum Closest
- [ ] Check 
```embed
title: "3Sum Closest - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? 3Sum Closest - Given an integer array nums of length n and an integer target, find three integers at distinct indices in nums such that the sum is closest to target.  Return the sum of the three integers.  You may assume that each input would have exactly one solution.     Example 1:   Input: nums = [-1,2,1,-4], target = 1 Output: 2 Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).   Example 2:   Input: nums = [0,0,0], target = 1 Output: 0 Explanation: The sum that is closest to the target is 0. (0 + 0 + 0 = 0).      Constraints:   * 3 <= nums.length <= 500  * -1000 <= nums[i] <= 1000  * -104 <= target <= 104"
url: "https://leetcode.com/problems/3sum-closest/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 19. Remove Nth Node From End of List
- [ ] Check 
```embed
title: "Remove Nth Node From End of List - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Remove Nth Node From End of List - Given the head of a linked list, remove the nth node from the end of the list and return its head.     Example 1:  [https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg]   Input: head = [1,2,3,4,5], n = 2 Output: [1,2,3,5]   Example 2:   Input: head = [1], n = 1 Output: []   Example 3:   Input: head = [1,2], n = 1 Output: [1]      Constraints:   * The number of nodes in the list is sz.  * 1 <= sz <= 30  * 0 <= Node.val <= 100  * 1 <= n <= sz     Follow up: Could you do this in one pass?"
url: "https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 948. Bag of Tokens
- [ ] Check 
```embed
title: "Bag of Tokens - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Bag of Tokens - You start with an initial power of power, an initial score of 0, and a bag of tokens given as an integer array tokens, where each tokens[i] denotes the value of tokeni.  Your goal is to maximize the total score by strategically playing these tokens. In one move, you can play an unplayed token in one of the two ways (but not both for the same token):   * Face-up: If your current power is at least tokens[i], you may play tokeni, losing tokens[i] power and gaining 1 score.  * Face-down: If your current score is at least 1, you may play tokeni, gaining tokens[i] power and losing 1 score.  Return the maximum possible score you can achieve after playing any number of tokens.     Example 1:  Input: tokens = [100], power = 50  Output: 0  Explanation: Since your score is 0 initially, you cannot play the token face-down. You also cannot play it face-up since your power (50) is less than tokens[0] (100).  Example 2:  Input: tokens = [200,100], power = 150  Output: 1  Explanation: Play token1 (100) face-up, reducing your power to 50 and increasing your score to 1.  There is no need to play token0, since you cannot play it face-up to add to your score. The maximum score achievable is 1.  Example 3:  Input: tokens = [100,200,300,400], power = 200  Output: 2  Explanation: Play the tokens in this order to get a score of 2:   1. Play token0 (100) face-up, reducing power to 100 and increasing score to 1.  2. Play token3 (400) face-down, increasing power to 500 and reducing score to 0.  3. Play token1 (200) face-up, reducing power to 300 and increasing score to 1.  4. Play token2 (300) face-up, reducing power to 0 and increasing score to 2.  The maximum score achievable is 2.     Constraints:   * 0 <= tokens.length <= 1000  * 0 <= tokens[i], power < 104"
url: "https://leetcode.com/problems/bag-of-tokens/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 1679. Max Number of K-Sum Pairs
- [ ] Check 
```embed
title: "Max Number of K-Sum Pairs - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Max Number of K-Sum Pairs - You are given an integer array nums and an integer k.  In one operation, you can pick two numbers from the array whose sum equals k and remove them from the array.  Return the maximum number of operations you can perform on the array.     Example 1:   Input: nums = [1,2,3,4], k = 5 Output: 2 Explanation: Starting with nums = [1,2,3,4]: - Remove numbers 1 and 4, then nums = [2,3] - Remove numbers 2 and 3, then nums = [] There are no more pairs that sum up to 5, hence a total of 2 operations.  Example 2:   Input: nums = [3,1,3,4,3], k = 6 Output: 1 Explanation: Starting with nums = [3,1,3,4,3]: - Remove the first two 3's, then nums = [1,4,3] There are no more pairs that sum up to 6, hence a total of 1 operation.     Constraints:   * 1 <= nums.length <= 105  * 1 <= nums[i] <= 109  * 1 <= k <= 109"
url: "https://leetcode.com/problems/max-number-of-k-sum-pairs/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 1679. Max Number of K-Sum Pairs
- [ ] Check 
```embed
title: "Max Number of K-Sum Pairs - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Max Number of K-Sum Pairs - You are given an integer array nums and an integer k.  In one operation, you can pick two numbers from the array whose sum equals k and remove them from the array.  Return the maximum number of operations you can perform on the array.     Example 1:   Input: nums = [1,2,3,4], k = 5 Output: 2 Explanation: Starting with nums = [1,2,3,4]: - Remove numbers 1 and 4, then nums = [2,3] - Remove numbers 2 and 3, then nums = [] There are no more pairs that sum up to 5, hence a total of 2 operations.  Example 2:   Input: nums = [3,1,3,4,3], k = 6 Output: 1 Explanation: Starting with nums = [3,1,3,4,3]: - Remove the first two 3's, then nums = [1,4,3] There are no more pairs that sum up to 6, hence a total of 1 operation.     Constraints:   * 1 <= nums.length <= 105  * 1 <= nums[i] <= 109  * 1 <= k <= 109"
url: "https://leetcode.com/problems/max-number-of-k-sum-pairs/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 
- [ ] Check 

```cpp

```

##
- [ ] Check 

```cpp

```

