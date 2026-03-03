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
class Solution {
public:
    vector<int> asteroidCollision(vector<int>& asteroids) {
        stack<int> st;
        for (int a : asteroids) {
            bool destroyed = false;
            while (!st.empty() && st.top() > 0 && a < 0) {
                if (abs(st.top()) < abs(a)) {
                    st.pop(); 
                }
                else if (abs(st.top()) == abs(a)) {
                    st.pop(); 
                    destroyed = true;
                    break;
                }
                else {
                    destroyed = true; 
                    break;
                }
            }
            if (!destroyed) {
                st.push(a);
            }
        }
        vector<int> result(st.size());
        for (int i = st.size() - 1; i >= 0; i--) {
            result[i] = st.top();
            st.pop();
        }
        return result;
    }
};
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
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<int> st;
        for (string s : tokens) {
            if (s == "+" || s == "-" || s == "*" || s == "/") {
                
                int b = st.top(); 
                st.pop();
                
                int a = st.top(); 
                st.pop();
                if (s == "+") st.push(a + b);
                else if (s == "-") st.push(a - b);
                else if (s == "*") st.push(a * b);
                else if (s == "/") st.push(a / b);
            }
            else {
                st.push(stoi(s));
            }
        }
        return st.top();
    }
};
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
class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        stack<int> st; 
        int maxArea = 0;
        int n = heights.size();
        for (int i = 0; i <= n; i++) {
            int currentHeight = (i == n) ? 0 : heights[i];
            while (!st.empty() && currentHeight < heights[st.top()]) { 
                int height = heights[st.top()];
                st.pop();
                int width;
                if (st.empty())
                    width = i;
                else
                    width = i - st.top() - 1;
                maxArea = max(maxArea, height * width);
            }
            st.push(i);
        }
        return maxArea;
    }
};
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
class Solution {
public:
    long long subArrayRanges(vector<int>& nums) {
        int n = nums.size();
        long long total = 0;
        for (int i = 0; i < n; i++) {
            int mini = nums[i];
            int maxi = nums[i];
            for (int j = i; j < n; j++) {
                mini = min(mini, nums[j]);
                maxi = max(maxi, nums[j]);
                total += (maxi - mini);
            }
        }
        return total;
    }
};
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
class Solution {
public:
    int sumSubarrayMins(vector<int>& arr) {
        int n = arr.size();
        long long total = 0;
        int mod = 1e9 + 7;
        for (int i = 0; i < n; i++) {
            int mini = arr[i];
            for (int j = i; j < n; j++) {
                mini = min(mini, arr[j]);
                total = (total + mini) % mod;
            }
        }
        return total;
    }
};
```

## Infix to Prefix
- [ ] Check 

```cpp
#include <bits/stdc++.h>
using namespace std;

int precedence(char c) {
    if (c == '+' || c == '-') return 1;
    if (c == '*' || c == '/') return 2;
    if (c == '^') return 3;
    return -1;
}
string infixToPrefix(string s) {
    
    reverse(s.begin(), s.end());
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == '(')
            s[i] = ')';
        else if (s[i] == ')')
            s[i] = '(';
    }
    stack<char> st;
    string result = "";
    for (int i = 0; i < s.length(); i++) {
        
        char c = s[i];
        if (isalnum(c)) {
            result += c;
        }
        else if (c == '(') {
            st.push(c);
        }
        else if (c == ')') {
            while (!st.empty() && st.top() != '(') {
                result += st.top();
                st.pop();
            }
            st.pop(); 
        }
        else {
            while (!st.empty() && precedence(st.top()) >= precedence(c)) {
                result += st.top();
                st.pop();
            }
            st.push(c);
        }
    }
    while (!st.empty()) {
        result += st.top();
        st.pop();
    }
    reverse(result.begin(), result.end());
    return result;
}
int main() {
    string s = "(A-B/C)*(A/K-L)";
    cout << infixToPrefix(s);
}
```

## Postfix to Prefix
- [ ] Check 

```cpp
#include <bits/stdc++.h>
using namespace std;
string postfixToPrefix(string s) {
    stack<string> st;
    for (int i = 0; i < s.length(); i++) {       
        char c = s[i];
        if (isalnum(c)) {
            string temp(1, c);
            st.push(temp);
        }
        else {
            string op2 = st.top(); st.pop();
            string op1 = st.top(); st.pop();
            string result = c + op1 + op2;
            st.push(result);
        }
    }
    return st.top();
}
int main() {
    string s = "AB+C*";
    cout << postfixToPrefix(s);
}
```

## Postfix to Infix
- [ ] Check 

```cpp
#include <bits/stdc++.h>
using namespace std;

string postfixToInfix(string s) {
    stack<string> st;
    for (int i = 0; i < s.length(); i++) {
        char c = s[i];
        if (isalnum(c)) {
            string temp(1, c);
            st.push(temp);
        }
        else {
            string op2 = st.top(); st.pop();
            string op1 = st.top(); st.pop();
            string result = "(" + op1 + c + op2 + ")";
            st.push(result);
        }
    }
    return st.top();
}
int main() {
    string s = "AB+C*";
    cout << postfixToInfix(s);
}
```

# Stack/Greedy

## 402. Remove K Digits
- [ ] Check 
```embed
title: "Remove K Digits - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Remove K Digits - Given string num representing a non-negative integer num, and an integer k, return the smallest possible integer after removing k digits from num.     Example 1:   Input: num = \"1432219\", k = 3 Output: \"1219\" Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.   Example 2:   Input: num = \"10200\", k = 1 Output: \"200\" Explanation: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.   Example 3:   Input: num = \"10\", k = 2 Output: \"0\" Explanation: Remove all the digits from the number and it is left with nothing which is 0.      Constraints:   * 1 <= k <= num.length <= 105  * num consists of only digits.  * num does not have any leading zeros except for the zero itself."
url: "https://leetcode.com/problems/remove-k-digits/description/"
favicon: ""
aspectRatio: "52"
```

```cpp
class Solution {
public:
    string removeKdigits(string num, int k) {
        string st = "";
        for (char c : num) {
            while (!st.empty() && k > 0 && st.back() > c) {
                st.pop_back();
                k--;
            }
            st.push_back(c);
        }
        while (!st.empty() && k > 0) {
            st.pop_back();
            k--;
        }
        int i = 0;
        while (i < st.size() && st[i] == '0') {
            i++;
        }
        string result = st.substr(i);
        if (result == "")
            return "0";
        return result;
    }
};
```

#  Stack/Hash Map

## 496. Next Greater Element I
- [ ] Check 
```embed
title: "Next Greater Element I - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Next Greater Element I - The next greater element of some element x in an array is the first greater element that is to the right of x in the same array.  You are given two distinct 0-indexed integer arrays nums1 and nums2, where nums1 is a subset of nums2.  For each 0 <= i < nums1.length, find the index j such that nums1[i] == nums2[j] and determine the next greater element of nums2[j] in nums2. If there is no next greater element, then the answer for this query is -1.  Return an array ans of length nums1.length such that ans[i] is the next greater element as described above.     Example 1:   Input: nums1 = [4,1,2], nums2 = [1,3,4,2] Output: [-1,3,-1] Explanation: The next greater element for each value of nums1 is as follows: - 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1. - 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3. - 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.   Example 2:   Input: nums1 = [2,4], nums2 = [1,2,3,4] Output: [3,-1] Explanation: The next greater element for each value of nums1 is as follows: - 2 is underlined in nums2 = [1,2,3,4]. The next greater element is 3. - 4 is underlined in nums2 = [1,2,3,4]. There is no next greater element, so the answer is -1.      Constraints:   * 1 <= nums1.length <= nums2.length <= 1000  * 0 <= nums1[i], nums2[i] <= 104  * All integers in nums1 and nums2 are unique.  * All the integers of nums1 also appear in nums2.     Follow up: Could you find an O(nums1.length + nums2.length) solution?"
url: "https://leetcode.com/problems/next-greater-element-i/description/"
favicon: ""
aspectRatio: "52"
```

```cpp
class Solution {
public:
    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        stack<int> st;
        unordered_map<int, int> mp;
        for (int num : nums2) {
            
            while (!st.empty() && st.top() < num) {
                mp[st.top()] = num;
                st.pop();
            }
            st.push(num);
        }
        while (!st.empty()) {
            mp[st.top()] = -1;
            st.pop();
        }
        vector<int> result;
        for (int num : nums1) {
            result.push_back(mp[num]);
        }
        return result;
    }
};
```
