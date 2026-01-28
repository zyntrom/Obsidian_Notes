## Important inbuilt functions in all Lang--

### Sort

```java
import java.util.Arrays;
Arrays.sort(arr); //sorts in place
```

```c++
#include <algorithm>
sort(arr,arr+n) //pass in first and last pointer of the array
```

```python
arr.sort(); # sorts in place
sorted(arr) #returns new sorted array 
```

```js
arr.sort((a,b)=> a-b) //Sorts in accending order b-a for decending order
```

### Math max and min

```java
int mx = Math.max(a, b);
int mn = Math.min(a, b);
```

```c++
#include <algorithm>
int mx = max(a, b);
int mn = min(a, b);
```

```python
mx = max(a, b)
mn = min(a, b)
```

```js
let mx = Math.max(a, b);
let mn = Math.min(a, b);
```

## 31. Next Permutation 
- [x] Check 
### Array Manipulation

```embed
title: "Next Permutation - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Next Permutation - A permutation of an array of integers is an arrangement of its members into a sequence or linear order.   * For example, for arr = [1,2,3], the following are all the permutations of arr: [1,2,3], [1,3,2], [2, 1, 3], [2, 3, 1], [3,1,2], [3,2,1].  The next permutation of an array of integers is the next lexicographically greater permutation of its integer. More formally, if all the permutations of the array are sorted in one container according to their lexicographical order, then the next permutation of that array is the permutation that follows it in the sorted container. If such arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).   * For example, the next permutation of arr = [1,2,3] is [1,3,2].  * Similarly, the next permutation of arr = [2,3,1] is [3,1,2].  * While the next permutation of arr = [3,2,1] is [1,2,3] because [3,2,1] does not have a lexicographical larger rearrangement.  Given an array of integers nums, find the next permutation of nums.  The replacement must be in place [http://en.wikipedia.org/wiki/In-place_algorithm] and use only constant extra memory.     Example 1:   Input: nums = [1,2,3] Output: [1,3,2]   Example 2:   Input: nums = [3,2,1] Output: [1,2,3]   Example 3:   Input: nums = [1,1,5] Output: [1,5,1]      Constraints:   * 1 <= nums.length <= 100  * 0 <= nums[i] <= 100"
url: "https://leetcode.com/problems/next-permutation/description/"
favicon: ""
aspectRatio: "52"
```

```java
class Solution {
    public void nextPermutation(int[] nums) {
        int n = nums.length;
        int i = n - 2;
        while (i >= 0 && nums[i] >= nums[i + 1]) {
            i--;
        }
        if (i >= 0) {
            int j = n - 1;
            while (nums[i] >= nums[j]) {
                j--;
            }
            swap(nums, i, j);
        }
        reverse(nums, i + 1, n - 1);
    }
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
    private void reverse(int[] nums, int left, int right) {
        while (left < right) {
            swap(nums, left++, right--);
        }
    }
}

```

## 50. Pow(x, n)
- [x] Check 
### Divide and Conquer

```embed
title: "Pow(x, n) - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Pow(x, n) - Implement pow(x, n) [http://www.cplusplus.com/reference/valarray/pow/], which calculates x raised to the power n (i.e., xn).     Example 1:   Input: x = 2.00000, n = 10 Output: 1024.00000   Example 2:   Input: x = 2.10000, n = 3 Output: 9.26100   Example 3:   Input: x = 2.00000, n = -2 Output: 0.25000 Explanation: 2-2 = 1/22 = 1/4 = 0.25      Constraints:   * -100.0 < x < 100.0  * -231 <= n <= 231-1  * n is an integer.  * Either x is not zero or n > 0.  * -104 <= xn <= 104"
url: "https://leetcode.com/problems/powx-n/description/"
favicon: ""
aspectRatio: "52"
```

```java
class Solution {
	public double myPow(double x, int n) {
		long pow =n;
		if(pow<0){
			x= 1/x;
			pow=-pow;
		}
		double result =1.0;
		while(pow>0){
			if(pow%2==1){
				result*=x;
			}
			x*=x;
			pow/=2;
		}
		return result;
	}
}
```

## 1040. Moving Stones Until Consecutive II
- [x] Check 
### Greedy/Sliding Window

```embed
title: "Moving Stones Until Consecutive II - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Moving Stones Until Consecutive II - There are some stones in different positions on the X-axis. You are given an integer array stones, the positions of the stones.  Call a stone an endpoint stone if it has the smallest or largest position. In one move, you pick up an endpoint stone and move it to an unoccupied position so that it is no longer an endpoint stone.   * In particular, if the stones are at say, stones = [1,2,5], you cannot move the endpoint stone at position 5, since moving it to any position (such as 0, or 3) will still keep that stone as an endpoint stone.  The game ends when you cannot make any more moves (i.e., the stones are in three consecutive positions).  Return an integer array answer of length 2 where:   * answer[0] is the minimum number of moves you can play, and  * answer[1] is the maximum number of moves you can play.     Example 1:   Input: stones = [7,4,9] Output: [1,2] Explanation: We can move 4 -> 8 for one move to finish the game. Or, we can move 9 -> 5, 4 -> 6 for two moves to finish the game.   Example 2:   Input: stones = [6,5,4,3,10] Output: [2,3] Explanation: We can move 3 -> 8 then 10 -> 7 to finish the game. Or, we can move 3 -> 7, 4 -> 8, 5 -> 9 to finish the game. Notice we cannot move 10 -> 2 to finish the game, because that would be an illegal move.      Constraints:   * 3 <= stones.length <= 104  * 1 <= stones[i] <= 109  * All the values of stones are unique."
url: "https://leetcode.com/problems/moving-stones-until-consecutive-ii/description/"
favicon: ""
aspectRatio: "52"
```

```java
import java.util.*;
class Solution {
	public int[] numMovesStonesII(int[] stones) {
		Arrays.sort(stones);
		int n =stones.length;
		int max1= stones[n-1] -stones[1] -(n-2);
		int max2 =stones[n-2] -stones[0]-(n-2);
		int maxMoves =Math.max(max1,max2);
		int minMoves = Integer.MAX_VALUE;
		for(int i=0;i<n;i++){
			int j=i;
			while((j+1) <n && stones[j+1]-stones[i]+1<=n){
				j++;
			}
			int stonesInWindow=j-i+1;
			if(stonesInWindow ==n-1 && stones[j]-stones[i]+1 ==n-1){
				minMoves = Math.min(minMoves,2);
			}
			else{
				minMoves =Math.min(minMoves,n-stonesInWindow);
			}
		}
		return new int[] {minMoves,maxMoves};
	}
}
```

## 2592. Maximize Greatness of an Array
- [x] Check 
### Greedy/Sorting

```embed
title: "Maximize Greatness of an Array - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Maximize Greatness of an Array - You are given a 0-indexed integer array nums. You are allowed to permute nums into a new array perm of your choosing.  We define the greatness of nums be the number of indices 0 <= i < nums.length for which perm[i] > nums[i].  Return the maximum possible greatness you can achieve after permuting nums.     Example 1:   Input: nums = [1,3,5,2,1,3,1] Output: 4 Explanation: One of the optimal rearrangements is perm = [2,5,1,3,3,1,1]. At indices = 0, 1, 3, and 4, perm[i] > nums[i]. Hence, we return 4.  Example 2:   Input: nums = [1,2,3,4] Output: 3 Explanation: We can prove the optimal perm is [2,3,4,1]. At indices = 0, 1, and 2, perm[i] > nums[i]. Hence, we return 3.      Constraints:   * 1 <= nums.length <= 105  * 0 <= nums[i] <= 109"
url: "https://leetcode.com/problems/maximize-greatness-of-an-array/description/"
favicon: ""
aspectRatio: "52"
```

```java
import java.util.Arrays;

class Solution {
    public int maximizeGreatness(int[] nums) {
        Arrays.sort(nums);
        int n = nums.length;
        int i = 0, j = 0, greatness = 0;
        while (i < n && j < n) {
            if (nums[j] > nums[i]) {
                greatness++;
                i++;
                j++;
            } else {
                j++;
            }
        }
        return greatness;
    }
}

```

## 128. Longest Consecutive Sequence
- [x] Check 
### Hash Table

```embed
title: "Longest Consecutive Sequence - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Longest Consecutive Sequence - Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.  You must write an algorithm that runs in O(n) time.     Example 1:   Input: nums = [100,4,200,1,3,2] Output: 4 Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.   Example 2:   Input: nums = [0,3,7,2,5,8,4,6,0,1] Output: 9   Example 3:   Input: nums = [1,0,1,2] Output: 3      Constraints:   * 0 <= nums.length <= 105  * -109 <= nums[i] <= 109"
url: "https://leetcode.com/problems/longest-consecutive-sequence/description/"
favicon: ""
aspectRatio: "52"
```

```java
import java.util.*;

class Solution {
    public int longestConsecutive(int[] nums) {
        Arrays.sort(nums);
        int n = nums.length;
        int maxLength = 1;
        int currLength = 1;
        if (n <= 0) return 0;
        for (int i = 1; i < n; i++) {
            if (nums[i] == nums[i - 1]) {
                continue;
            } else if (nums[i] == nums[i - 1] + 1) {
                currLength++;
            } else {
                currLength = 1;
            }
            maxLength = Math.max(maxLength, currLength);
        }
        return maxLength;
    }
}

```

## 786. K-th Smallest Prime Fraction
- [x] Check 
### Heap

```embed
title: "K-th Smallest Prime Fraction - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? K-th Smallest Prime Fraction - You are given a sorted integer array arr containing 1 and prime numbers, where all the integers of arr are unique. You are also given an integer k.  For every i and j where 0 <= i < j < arr.length, we consider the fraction arr[i] / arr[j].  Return the kth smallest fraction considered. Return your answer as an array of integers of size 2, where answer[0] == arr[i] and answer[1] == arr[j].     Example 1:   Input: arr = [1,2,3,5], k = 3 Output: [2,5] Explanation: The fractions to be considered in sorted order are: 1/5, 1/3, 2/5, 1/2, 3/5, and 2/3. The third fraction is 2/5.   Example 2:   Input: arr = [1,7], k = 1 Output: [1,7]      Constraints:   * 2 <= arr.length <= 1000  * 1 <= arr[i] <= 3 * 104  * arr[0] == 1  * arr[i] is a prime number for i > 0.  * All the numbers of arr are unique and sorted in strictly increasing order.  * 1 <= k <= arr.length * (arr.length - 1) / 2     Follow up: Can you solve the problem with better than O(n2) complexity?"
url: "https://leetcode.com/problems/k-th-smallest-prime-fraction/description/"
favicon: ""
aspectRatio: "52"
```

```java
import java.util.*;
class Solution {
    public int[] kthSmallestPrimeFraction(int[] arr, int k) {
        List<int[]> frac = new ArrayList<>();
        int n = arr.length;
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                frac.add(new int[]{arr[i], arr[j]});
            }
        }
        Collections.sort(frac, (a, b) -> {
            double f1 = (double) a[0] / a[1];
            double f2 = (double) b[0] / b[1];
            return Double.compare(f1, f2);
        });
        return frac.get(k - 1);
    }
}
```
