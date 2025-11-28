
# Two Pointers
## 11. Container With Most Water

```embed
title: "Container With Most Water - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Container With Most Water - You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).  Find two lines that together with the x-axis form a container, such that the container contains the most water.  Return the maximum amount of water a container can store.  Notice that you may not slant the container.     Example 1:  [https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg]   Input: height = [1,8,6,2,5,4,8,3,7] Output: 49 Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.   Example 2:   Input: height = [1,1] Output: 1      Constraints:   * n == height.length  * 2 <= n <= 105  * 0 <= height[i] <= 104"
url: "https://leetcode.com/problems/container-with-most-water/description/"
favicon: ""
aspectRatio: "52"
```

```java
class Solution {
    public int maxArea(int[] height) {
        int left = 0, right = height.length - 1;
        int maxArea = 0;
        while (left < right) {
            // Width of the container
            int width = right - left;
            // Height is determined by the smaller line
            int h = Math.min(height[left], height[right]);
            // Update max area
            maxArea = Math.max(maxArea, width * h);
            // Move the smaller height inward
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }
        return maxArea;
    }
}

```

## 838. Push Dominoes

```embed
title: "Push Dominoes - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Push Dominoes - There are n dominoes in a line, and we place each domino vertically upright. In the beginning, we simultaneously push some of the dominoes either to the left or to the right.  After each second, each domino that is falling to the left pushes the adjacent domino on the left. Similarly, the dominoes falling to the right push their adjacent dominoes standing on the right.  When a vertical domino has dominoes falling on it from both sides, it stays still due to the balance of the forces.  For the purposes of this question, we will consider that a falling domino expends no additional force to a falling or already fallen domino.  You are given a string dominoes representing the initial state where:   * dominoes[i] = 'L', if the ith domino has been pushed to the left,  * dominoes[i] = 'R', if the ith domino has been pushed to the right, and  * dominoes[i] = '.', if the ith domino has not been pushed.  Return a string representing the final state.     Example 1:   Input: dominoes = \"RR.L\" Output: \"RR.L\" Explanation: The first domino expends no additional force on the second domino.   Example 2:  [https://s3-lc-upload.s3.amazonaws.com/uploads/2018/05/18/domino.png]   Input: dominoes = \".L.R...LR..L..\" Output: \"LL.RR.LLRRLL..\"      Constraints:   * n == dominoes.length  * 1 <= n <= 105  * dominoes[i] is either 'L', 'R', or '.'."
url: "https://leetcode.com/problems/push-dominoes/description/"
favicon: ""
aspectRatio: "52"
```

```java
class Solution {
    public String pushDominoes(String dominoes) {
        int n = dominoes.length();
        int[] force = new int[n];
        
        int f = 0;
        // Left to right
        for (int i = 0; i < n; i++) {
            char c = dominoes.charAt(i);
            if (c == 'R') {
                f = n; // max force to the right
            } else if (c == 'L') {
                f = 0;
            } else {
                f = Math.max(f - 1, 0);
            }
            force[i] += f;
        }
        f = 0;
        // Right to left
        for (int i = n - 1; i >= 0; i--) {
            char c = dominoes.charAt(i);
            if (c == 'L') {
                f = n; // max force to the left
            } else if (c == 'R') {
                f = 0;
            } else {
                f = Math.max(f - 1, 0);
            }
            force[i] -= f; // subtract left force
        }
        // Build the final state
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < n; i++) {
            if (force[i] > 0) {
                sb.append('R');
            } else if (force[i] < 0) {
                sb.append('L');
            } else {
                sb.append('.');
            }
        }
        return sb.toString();
    }
}

```

## 881. Boats to Save People

```embed
title: "Boats to Save People - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Boats to Save People - You are given an array people where people[i] is the weight of the ith person, and an infinite number of boats where each boat can carry a maximum weight of limit. Each boat carries at most two people at the same time, provided the sum of the weight of those people is at most limit.  Return the minimum number of boats to carry every given person.     Example 1:   Input: people = [1,2], limit = 3 Output: 1 Explanation: 1 boat (1, 2)   Example 2:   Input: people = [3,2,2,1], limit = 3 Output: 3 Explanation: 3 boats (1, 2), (2) and (3)   Example 3:   Input: people = [3,5,3,4], limit = 5 Output: 4 Explanation: 4 boats (3), (3), (4), (5)      Constraints:   * 1 <= people.length <= 5 * 104  * 1 <= people[i] <= limit <= 3 * 104"
url: "https://leetcode.com/problems/boats-to-save-people/description/"
favicon: ""
aspectRatio: "52"
```

```java
import java.util.Arrays;

class Solution {
    public int numRescueBoats(int[] people, int limit) {
        Arrays.sort(people);
        int i = 0, j = people.length - 1;
        int boats = 0;
        while (i <= j) {
            if (people[i] + people[j] <= limit) {
                i++; // lightest person goes with heaviest
            }
            j--; // heaviest person always goes
            boats++;
        }
        return boats;
    }
}

```

## 795. Number of Subarrays with Bounded Maximum

```embed
title: "Number of Subarrays with Bounded Maximum - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Number of Subarrays with Bounded Maximum - Given an integer array nums and two integers left and right, return the number of contiguous non-empty subarrays such that the value of the maximum array element in that subarray is in the range [left, right].  The test cases are generated so that the answer will fit in a 32-bit integer.     Example 1:   Input: nums = [2,1,4,3], left = 2, right = 3 Output: 3 Explanation: There are three subarrays that meet the requirements: [2], [2, 1], [3].   Example 2:   Input: nums = [2,9,2,5,6], left = 2, right = 8 Output: 7      Constraints:   * 1 <= nums.length <= 105  * 0 <= nums[i] <= 109  * 0 <= left <= right <= 109"
url: "https://leetcode.com/problems/number-of-subarrays-with-bounded-maximum/description/"
favicon: ""
aspectRatio: "52"
```

```java
class Solution {
    public int numSubarrayBoundedMax(int[] nums, int left, int right) {
        return count(nums, right) - count(nums, left - 1);
    }
    private int count(int[] nums, int bound) {
        int count = 0, current = 0;
        for (int num : nums) {
            if (num <= bound) {
                current++;
                count += current;
            } else {
                current = 0;
            }
        }
        return count;
    }
}
```

## 16. 3Sum Closest

```embed
title: "3Sum Closest - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? 3Sum Closest - Given an integer array nums of length n and an integer target, find three integers in nums such that the sum is closest to target.  Return the sum of the three integers.  You may assume that each input would have exactly one solution.     Example 1:   Input: nums = [-1,2,1,-4], target = 1 Output: 2 Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).   Example 2:   Input: nums = [0,0,0], target = 1 Output: 0 Explanation: The sum that is closest to the target is 0. (0 + 0 + 0 = 0).      Constraints:   * 3 <= nums.length <= 500  * -1000 <= nums[i] <= 1000  * -104 <= target <= 104"
url: "https://leetcode.com/problems/3sum-closest/description/"
favicon: ""
aspectRatio: "52"
```

```java
import java.util.Arrays;

class Solution {
    public int threeSumClosest(int[] nums, int target) {
        Arrays.sort(nums);
        int n = nums.length;
        int closestSum = nums[0] + nums[1] + nums[2]; // initial sum
        for (int i = 0; i < n - 2; i++) {
            int left = i + 1;
            int right = n - 1;
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if (Math.abs(sum - target) < Math.abs(closestSum - target)) {
                    closestSum = sum;
                }
                if (sum < target) {
                    left++;
                } else if (sum > target) {
                    right--;
                } else {
                    // Exact match found
                    return target;
                }
            }
        }
        return closestSum;
    }
}

```

