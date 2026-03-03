# Stack

## 735. Asteroid Collision
- [ ] Check 
```embed
title: "Asteroid Collision - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Asteroid Collision - We are given an array asteroids of integers representing asteroids in a row. The indices of the asteroid in the array represent their relative position in space.  For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.  Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.     Example 1:   Input: asteroids = [5,10,-5] Output: [5,10] Explanation: The 10 and -5 collide resulting in 10. The 5 and 10 never collide.   Example 2:   Input: asteroids = [8,-8] Output: [] Explanation: The 8 and -8 collide exploding each other.   Example 3:   Input: asteroids = [10,2,-5] Output: [10] Explanation: The 2 and -5 collide resulting in -5. The 10 and -5 collide resulting in 10.   Example 4:   Input: asteroids = [3,5,-6,2,-1,4]​​​​​​​ Output: [-6,2,4] Explanation: The asteroid -6 makes the asteroid 3 and 5 explode, and then continues going left. On the other side, the asteroid 2 makes the asteroid -1 explode and then continues going right, without reaching asteroid 4.      Constraints:   * 2 <= asteroids.length <= 104  * -1000 <= asteroids[i] <= 1000  * asteroids[i] != 0"
url: "https://leetcode.com/problems/asteroid-collision/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 150. Evaluate Reverse Polish Notation
- [ ] Check 
```embed
title: "Evaluate Reverse Polish Notation - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Evaluate Reverse Polish Notation - You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation [http://en.wikipedia.org/wiki/Reverse_Polish_notation].  Evaluate the expression. Return an integer that represents the value of the expression.  Note that:   * The valid operators are '+', '-', '*', and '/'.  * Each operand may be an integer or another expression.  * The division between two integers always truncates toward zero.  * There will not be any division by zero.  * The input represents a valid arithmetic expression in a reverse polish notation.  * The answer and all the intermediate calculations can be represented in a 32-bit integer.     Example 1:   Input: tokens = [\"2\",\"1\",\"+\",\"3\",\"*\"] Output: 9 Explanation: ((2 + 1) * 3) = 9   Example 2:   Input: tokens = [\"4\",\"13\",\"5\",\"/\",\"+\"] Output: 6 Explanation: (4 + (13 / 5)) = 6   Example 3:   Input: tokens = [\"10\",\"6\",\"9\",\"3\",\"+\",\"-11\",\"*\",\"/\",\"*\",\"17\",\"+\",\"5\",\"+\"] Output: 22 Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5 = ((10 * (6 / (12 * -11))) + 17) + 5 = ((10 * (6 / -132)) + 17) + 5 = ((10 * 0) + 17) + 5 = (0 + 17) + 5 = 17 + 5 = 22      Constraints:   * 1 <= tokens.length <= 104  * tokens[i] is either an operator: \"+\", \"-\", \"*\", or \"/\", or an integer in the range [-200, 200]."
url: "https://leetcode.com/problems/evaluate-reverse-polish-notation/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 84. Largest Rectangle in Histogram
- [ ] Check 
```embed
title: "Largest Rectangle in Histogram - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Largest Rectangle in Histogram - Given an array of integers heights representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.     Example 1:  [https://assets.leetcode.com/uploads/2021/01/04/histogram.jpg]   Input: heights = [2,1,5,6,2,3] Output: 10 Explanation: The above is a histogram where width of each bar is 1. The largest rectangle is shown in the red area, which has an area = 10 units.   Example 2:  [https://assets.leetcode.com/uploads/2021/01/04/histogram-1.jpg]   Input: heights = [2,4] Output: 4      Constraints:   * 1 <= heights.length <= 105  * 0 <= heights[i] <= 104"
url: "https://leetcode.com/problems/largest-rectangle-in-histogram/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 2104. Sum of Subarray Ranges
- [ ] Check 
```embed
title: "Sum of Subarray Ranges - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Sum of Subarray Ranges - You are given an integer array nums. The range of a subarray of nums is the difference between the largest and smallest element in the subarray.  Return the sum of all subarray ranges of nums.  A subarray is a contiguous non-empty sequence of elements within an array.     Example 1:   Input: nums = [1,2,3] Output: 4 Explanation: The 6 subarrays of nums are the following: [1], range = largest - smallest = 1 - 1 = 0  [2], range = 2 - 2 = 0 [3], range = 3 - 3 = 0 [1,2], range = 2 - 1 = 1 [2,3], range = 3 - 2 = 1 [1,2,3], range = 3 - 1 = 2 So the sum of all ranges is 0 + 0 + 0 + 1 + 1 + 2 = 4.  Example 2:   Input: nums = [1,3,3] Output: 4 Explanation: The 6 subarrays of nums are the following: [1], range = largest - smallest = 1 - 1 = 0 [3], range = 3 - 3 = 0 [3], range = 3 - 3 = 0 [1,3], range = 3 - 1 = 2 [3,3], range = 3 - 3 = 0 [1,3,3], range = 3 - 1 = 2 So the sum of all ranges is 0 + 0 + 0 + 2 + 0 + 2 = 4.   Example 3:   Input: nums = [4,-2,-3,4,1] Output: 59 Explanation: The sum of all subarray ranges of nums is 59.      Constraints:   * 1 <= nums.length <= 1000  * -109 <= nums[i] <= 109     Follow-up: Could you find a solution with O(n) time complexity?"
url: "https://leetcode.com/problems/sum-of-subarray-ranges/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## 907. Sum of Subarray Minimums
- [ ] Check 
```embed
title: "Sum of Subarray Minimums - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Sum of Subarray Minimums - Given an array of integers arr, find the sum of min(b), where b ranges over every (contiguous) subarray of arr. Since the answer may be large, return the answer modulo 109 + 7.     Example 1:   Input: arr = [3,1,2,4] Output: 17 Explanation:  Subarrays are [3], [1], [2], [4], [3,1], [1,2], [2,4], [3,1,2], [1,2,4], [3,1,2,4].  Minimums are 3, 1, 2, 4, 1, 1, 2, 1, 1, 1. Sum is 17.   Example 2:   Input: arr = [11,81,94,43,3] Output: 444      Constraints:   * 1 <= arr.length <= 3 * 104  * 1 <= arr[i] <= 3 * 104"
url: "https://leetcode.com/problems/sum-of-subarray-minimums/description/"
favicon: ""
aspectRatio: "52"
```

```cpp

```

## Infix to Prefix
- [ ] Check 

```cpp

```

## Infix to Prefix
- [ ] Check 

```cpp

```
