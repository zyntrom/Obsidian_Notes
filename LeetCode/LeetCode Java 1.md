## 1. Two Sum

```embed
title: "Two Sum - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Two Sum - Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.  You may assume that each input would have exactly one solution, and you may not use the same element twice.  You can return the answer in any order.     Example 1:   Input: nums = [2,7,11,15], target = 9 Output: [0,1] Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].   Example 2:   Input: nums = [3,2,4], target = 6 Output: [1,2]   Example 3:   Input: nums = [3,3], target = 6 Output: [0,1]      Constraints:   * 2 <= nums.length <= 104  * -109 <= nums[i] <= 109  * -109 <= target <= 109  * Only one valid answer exists.     Follow-up: Can you come up with an algorithm that is less than O(n2) time complexity?"
url: "https://leetcode.com/problems/two-sum/description/"
favicon: ""
aspectRatio: "52"
```


```java
public class TwoSum {
    public static int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int num = nums[i];
            int complement = target - num;
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
          
	        map.put(num, i);
        }
        return new int[] {};
    }
}
```

## 9. Palindrome Number

```embed
title: "Palindrome Number - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Palindrome Number - Given an integer x, return true if x is a palindrome, and false otherwise.     Example 1:   Input: x = 121 Output: true Explanation: 121 reads as 121 from left to right and from right to left.   Example 2:   Input: x = -121 Output: false Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.   Example 3:   Input: x = 10 Output: false Explanation: Reads 01 from right to left. Therefore it is not a palindrome.      Constraints:   * -231 <= x <= 231 - 1     Follow up: Could you solve it without converting the integer to a string?"
url: "https://leetcode.com/problems/palindrome-number/"
favicon: ""
aspectRatio: "52"
```


```java
class Solution {
    public boolean isPalindrome(int x) {
        int rev = 0;
        int n = x;
        if (x < 0) {
            return false;
        }
        while (n != 0) {
            rev = rev * 10 + (n % 10);
            n = n / 10;
        }
        if (rev == x) {
            return true;
        } else {
            return false;
        }
    }
}
```

## 3. Roman to integer

```java
class Solution {
    public int romanToInt(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        map.put('I', 1);
        map.put('V', 5);
        map.put('X', 10);
        map.put('L', 50);
        map.put('C', 100);
        map.put('D', 500);
        map.put('M', 1000);
        int total = 0;
        for (int i = 0; i < s.length(); i++) {
            int value = map.get(s.charAt(i));
            if (i + 1 < s.length()) {
                int nextValue = map.get(s.charAt(i + 1));
                if (value < nextValue) {
                    total -= value;
                } else {
                    total += value;
                }
            } else {
                total += value;
            }
        }
        return total;
    }
}

```

## 4. Longest Common Prefix

```cpp
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) return "";
        String prefix = strs[0];
        for (int i = 1; i < strs.length; i++) {
            while (strs[i].indexOf(prefix) != 0) {
                prefix = prefix.substring(0, prefix.length() - 1)
                if (prefix.isEmpty()) {
                    return "";
                }
            }
        }
        return prefix;
    }
}
```

## 5. Valid Parentheses

```cpp
class Solution {
    public boolean isValid(String s) {
        int l = s.length();
        Stack<Character> stack = new Stack<>();
        for (int i = 0; i < l; i++) {
            char c = s.charAt(i);
            
            if (c == '(' || c == '{' || c == '[') {
                stack.push(c);
            }
            else if (c == ')' || c == '}' || c == ']') {
                if (stack.isEmpty()) return false;
                char top = stack.peek();
                if ((c == ')' && top == '(') || 
                    (c == ']' && top == '[') || 
                    (c == '}' && top == '{')) {
                    stack.pop();
                } else {
                    return false;
                }
            }
        }
        
        return stack.isEmpty();
    }
}

```

## 6. Merge Two Sorted Lists

```cpp
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
 
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(-1);
        ListNode curr = dummy;
        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                curr.next = list1;
                list1 = list1.next;
            } else {
                curr.next = list2;
                list2 = list2.next;
            }
            curr = curr.next;
        }
        if (list1 != null) {
            curr.next = list1;
        } else {
            curr.next = list2;
        }
        return dummy.next;
    }
}

```

## 7.  Remove Duplicates from Sorted Array

```cpp

class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) return 0;
        int i = 0;
        for (int j = 1; j < nums.length; j++) {
            if (nums[j] != nums[i]) {
                i++;
                nums[i] = nums[j];
            }
        }
        return i + 1;
    }
}

```

## 8. Remove Element

```cpp
class Solution {
    public int removeElement(int[] nums, int val) {
        int k = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                nums[k] = nums[i];
                k++;
            }
        }
        return k;
    }
}

```

## 9. Find the Index of the First Occurrence in a String

```cpp
class Solution {
    public int strStr(String haystack, String needle) {
        int nh = haystack.length();
        int nn = needle.length();
        if (nn == 0) return 0; // optional: LeetCode expects this
        for (int i = 0; i <= nh - nn; i++) {
            int j = 0;
            while (j < nn && haystack.charAt(i + j) == needle.charAt(j)) {
                j++;
            }
            if (j == nn) {
                return i;
            }
        }
        return -1;
    }
}

```

## 10. Search Insert Position

```cpp
class Solution {
    public int searchInsert(int[] nums, int target) {
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            if (nums[i] >= target) {
                return i;
            }
        }
        return n; // insert at the end
    }
}

```

