# Backtracking --
## 17. Letter Combinations of a Phone Number
- [x] Check 
```embed
title: "Letter Combinations of a Phone Number - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Letter Combinations of a Phone Number - Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.  A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.  [https://assets.leetcode.com/uploads/2022/03/15/1200px-telephone-keypad2svg.png]     Example 1:   Input: digits = \"23\" Output: [\"ad\",\"ae\",\"af\",\"bd\",\"be\",\"bf\",\"cd\",\"ce\",\"cf\"]   Example 2:   Input: digits = \"2\" Output: [\"a\",\"b\",\"c\"]      Constraints:   * 1 <= digits.length <= 4  * digits[i] is a digit in the range ['2', '9']."
url: "https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/"
favicon: ""
aspectRatio: "52"
```

```js
var letterCombinations = function(digits) {
    if (digits.length === 0) return [];

    const map = ["", "", "abc", 
			    "def", "ghi", "jkl", 
			    "mno", "pqrs", "tuv", 
			    "wxyz"
	];
    const ans = [];
    const backtrack = (index, cur) => {
        if (index === digits.length) {
            ans.push(cur.join(''));
            return;
        }
        const letters = map[digits[index] - '0'];
        for (const ch of letters) {
            cur.push(ch);                
            backtrack(index + 1, cur);   
            cur.pop();                    
        }
    };
    backtrack(0, []);
    return ans;
};
```

## 46. Permutations
- [x] Check 
```embed
title: "Permutations - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Permutations - Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.     Example 1:  Input: nums = [1,2,3] Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]   Example 2:  Input: nums = [0,1] Output: [[0,1],[1,0]]   Example 3:  Input: nums = [1] Output: [[1]]      Constraints:   * 1 <= nums.length <= 6  * -10 <= nums[i] <= 10  * All the integers of nums are unique."
url: "https://leetcode.com/problems/permutations/description/"
favicon: ""
aspectRatio: "52"
```

```js
var permute = function(nums) {
    const ans = [];
    const backtrack = (curr) => {
        if (curr.length === nums.length) {
            ans.push([...curr]); 
            return;
        }
        for (const num of nums) {
            if (curr.includes(num)) continue; 
            curr.push(num);                  
            backtrack(curr);                 
            curr.pop();                      
        }
    };
    backtrack([]);
    return ans;
};
```

## 51. N-Queens
- [x] Check 
```embed
title: "N-Queens - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? N-Queens - The n-queens puzzle is the problem of placing n queens on an n x n chessboard such that no two queens attack each other.  Given an integer n, return all distinct solutions to the n-queens puzzle. You may return the answer in any order.  Each solution contains a distinct board configuration of the n-queens' placement, where 'Q' and '.' both indicate a queen and an empty space, respectively.     Example 1:  [https://assets.leetcode.com/uploads/2020/11/13/queens.jpg]   Input: n = 4 Output: [[\".Q..\",\"...Q\",\"Q...\",\"..Q.\"],[\"..Q.\",\"Q...\",\"...Q\",\".Q..\"]] Explanation: There exist two distinct solutions to the 4-queens puzzle as shown above   Example 2:   Input: n = 1 Output: [[\"Q\"]]      Constraints:   * 1 <= n <= 9"
url: "https://leetcode.com/problems/n-queens/description/"
favicon: ""
aspectRatio: "52"
```

```js
var solveNQueens = function(n) {
    const ans = [];
    const col = new Array(n).fill(false);
    const diag1 = new Array(2 * n).fill(false); 
    const diag2 = new Array(2 * n).fill(false); 
    const board = Array.from({ length: n }, () => Array(n).fill('.'));
    const backtrack = (row) => {
        if (row === n) {
            ans.push(board.map(r => r.join('')));
            return;
        }
        for (let c = 0; c < n; c++) {
            const d1 = row - c + n;
            const d2 = row + c;
            if (col[c] || diag1[d1] || diag2[d2]) continue;
            board[row][c] = 'Q';
            col[c] = diag1[d1] = diag2[d2] = true;
            backtrack(row + 1);
            board[row][c] = '.';
            col[c] = diag1[d1] = diag2[d2] = false;
        }
    };
    backtrack(0);
    return ans;
};

```

## 526. Beautiful Arrangement
- [x] Check 
```embed
title: "Beautiful Arrangement - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Beautiful Arrangement - Suppose you have n integers labeled 1 through n. A permutation of those n integers perm (1-indexed) is considered a beautiful arrangement if for every i (1 <= i <= n), either of the following is true:   * perm[i] is divisible by i.  * i is divisible by perm[i].  Given an integer n, return the number of the beautiful arrangements that you can construct.     Example 1:   Input: n = 2 Output: 2 Explanation:  The first beautiful arrangement is [1,2]:     - perm[1] = 1 is divisible by i = 1     - perm[2] = 2 is divisible by i = 2 The second beautiful arrangement is [2,1]:     - perm[1] = 2 is divisible by i = 1     - i = 2 is divisible by perm[2] = 1   Example 2:   Input: n = 1 Output: 1      Constraints:   * 1 <= n <= 15"
url: "https://leetcode.com/problems/beautiful-arrangement/description/"
favicon: ""
aspectRatio: "52"
```

```js
var countArrangement = function(n) {
    let count = 0;
    const used = new Array(n + 1).fill(false);
    const backtrack = (pos) => {
        if (pos > n) {
            count++;
            return;
        }
        for (let num = 1; num <= n; num++) {
            if (!used[num] && (num % pos === 0 || pos % num === 0))
            {
                used[num] = true;
                backtrack(pos + 1);
                used[num] = false;
            }
        }
    };
    backtrack(1);
    return count;
};
```

## 39. Combination Sum
- [x] Check 
```embed
title: "Combination Sum - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Combination Sum - Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.  The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.  The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.     Example 1:   Input: candidates = [2,3,6,7], target = 7 Output: [[2,2,3],[7]] Explanation: 2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times. 7 is a candidate, and 7 = 7. These are the only two combinations.   Example 2:   Input: candidates = [2,3,5], target = 8 Output: [[2,2,2,2],[2,3,3],[3,5]]   Example 3:   Input: candidates = [2], target = 1 Output: []      Constraints:   * 1 <= candidates.length <= 30  * 2 <= candidates[i] <= 40  * All elements of candidates are distinct.  * 1 <= target <= 40"
url: "https://leetcode.com/problems/combination-sum/description/"
favicon: ""
aspectRatio: "52"
```

```js
var combinationSum = function(nums, target) {
    nums.sort((a, b) => a - b); 
    const res = [];
    const backtrack = (start, curr, remaining) => {
        if (remaining === 0) {
            res.push([...curr]); 
            return;
        }
        for (let i = start; i < nums.length; i++) {
            if (nums[i] > remaining) break; 
            curr.push(nums[i]); 
            backtrack(i, curr, remaining - nums[i]); 
            curr.pop(); 
        }
    };
    backtrack(0, [], target);
    return res;
};
```

## 40. Combination Sum II
- [x] Check 
```embed
title: "Combination Sum II - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Combination Sum II - Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.  Each number in candidates may only be used once in the combination.  Note: The solution set must not contain duplicate combinations.     Example 1:   Input: candidates = [10,1,2,7,6,1,5], target = 8 Output:  [ [1,1,6], [1,2,5], [1,7], [2,6] ]   Example 2:   Input: candidates = [2,5,2,1,2], target = 5 Output:  [ [1,2,2], [5] ]      Constraints:   * 1 <= candidates.length <= 100  * 1 <= candidates[i] <= 50  * 1 <= target <= 30"
url: "https://leetcode.com/problems/combination-sum-ii/description/"
favicon: ""
aspectRatio: "52"
```

```js
var combinationSum2 = function(nums, target) {
    nums.sort((a, b) => a - b);
    const res = [];
    const backtrack = (start, curr, remaining) => {
        if (remaining === 0) {
            res.push([...curr]); 
            return;
        }
        for (let i = start; i < nums.length; i++) {
            if (i > start && nums[i] === nums[i - 1]) continue;
            if (nums[i] > remaining) break;
            curr.push(nums[i]);                     
            backtrack(i + 1, curr, remaining - nums[i]); 
            curr.pop();
        }
    };
    backtrack(0, [], target);
    return res;
};
```

## 491. Non-decreasing Subsequences
- [x] Check 
```embed
title: "Non-decreasing Subsequences - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Non-decreasing Subsequences - Given an integer array nums, return all the different possible non-decreasing subsequences of the given array with at least two elements. You may return the answer in any order.     Example 1:   Input: nums = [4,6,7,7] Output: [[4,6],[4,6,7],[4,6,7,7],[4,7],[4,7,7],[6,7],[6,7,7],[7,7]]   Example 2:   Input: nums = [4,4,3,2,1] Output: [[4,4]]      Constraints:   * 1 <= nums.length <= 15  * -100 <= nums[i] <= 100"
url: "https://leetcode.com/problems/non-decreasing-subsequences/description/"
favicon: ""
aspectRatio: "52"
```

```js
var findSubsequences = function(nums) {
    const res = [];
    const backtrack = (idx, path) => {
        if (path.length >= 2) {
            res.push([...path]); 
        }
        const used = new Set();
        for (let i = idx; i < nums.length; i++) {
            if (used.has(nums[i])) 
            continue;
            if (path.length > 0 && nums[i] < path[path.length - 1])
            continue;
            used.add(nums[i]);
            path.push(nums[i]);          
            backtrack(i + 1, path);      
            path.pop();                  
        }
    };
    backtrack(0, []);
    return res;
};
```

## 22. Generate Parentheses
- [x] Check 
```embed
title: "Generate Parentheses - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Generate Parentheses - Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.     Example 1:  Input: n = 3 Output: [\"((()))\",\"(()())\",\"(())()\",\"()(())\",\"()()()\"]   Example 2:  Input: n = 1 Output: [\"()\"]      Constraints:   * 1 <= n <= 8"
url: "https://leetcode.com/problems/generate-parentheses/description/"
favicon: ""
aspectRatio: "52"
```

```js
var generateParenthesis = function(n) {
    const res = [];
    const backtrack = (cur, open, close) => {
        if (cur.length === 2 * n) {
            res.push(cur.join('')); 
            return;
        }
        if (open < n) {
            cur.push('(');                 
            backtrack(cur, open + 1, close); 
            cur.pop();                     
        }
        if (close < open) {
            cur.push(')');                 
            backtrack(cur, open, close + 1); 
            cur.pop();                     
        }
    };
    backtrack([], 0, 0);
    return res;
};
```

## 79. Word Search
- [x] Check 
```embed
title: "Word Search - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Word Search - Given an m x n grid of characters board and a string word, return true if word exists in the grid.  The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.     Example 1:  [https://assets.leetcode.com/uploads/2020/11/04/word2.jpg]   Input: board = [[\"A\",\"B\",\"C\",\"E\"],[\"S\",\"F\",\"C\",\"S\"],[\"A\",\"D\",\"E\",\"E\"]], word = \"ABCCED\" Output: true   Example 2:  [https://assets.leetcode.com/uploads/2020/11/04/word-1.jpg]   Input: board = [[\"A\",\"B\",\"C\",\"E\"],[\"S\",\"F\",\"C\",\"S\"],[\"A\",\"D\",\"E\",\"E\"]], word = \"SEE\" Output: true   Example 3:  [https://assets.leetcode.com/uploads/2020/10/15/word3.jpg]   Input: board = [[\"A\",\"B\",\"C\",\"E\"],[\"S\",\"F\",\"C\",\"S\"],[\"A\",\"D\",\"E\",\"E\"]], word = \"ABCB\" Output: false      Constraints:   * m == board.length  * n = board[i].length  * 1 <= m, n <= 6  * 1 <= word.length <= 15  * board and word consists of only lowercase and uppercase English letters.     Follow up: Could you use search pruning to make your solution faster with a larger board?"
url: "https://leetcode.com/problems/word-search/description/"
favicon: ""
aspectRatio: "52"
```

```js
var exist = function(board, word) {
    const m = board.length, n = board[0].length;
    const backtrack = (i, j, idx) => {
        if (idx === word.length) return true;
        if (i < 0 || j < 0 || i >= m || j >= n) return false;
        if (board[i][j] !== word[idx]) return false;
        const temp = board[i][j];
        board[i][j] = '#'; 
        const found = 
            backtrack(i + 1, j, idx + 1) ||
            backtrack(i - 1, j, idx + 1) ||
            backtrack(i, j + 1, idx + 1) ||
            backtrack(i, j - 1, idx + 1);
        board[i][j] = temp; 
        return found;
    };
    for (let i = 0; i < m; i++) {
        for (let j = 0; j < n; j++) {
            if (backtrack(i, j, 0)) return true;
        }
    }
    return false;
};
```

## 131. Palindrome Partitioning
- [x] Check 
```embed
title: "Palindrome Partitioning - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Palindrome Partitioning - Given a string s, partition s such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of s.     Example 1:  Input: s = \"aab\" Output: [[\"a\",\"a\",\"b\"],[\"aa\",\"b\"]]   Example 2:  Input: s = \"a\" Output: [[\"a\"]]      Constraints:   * 1 <= s.length <= 16  * s contains only lowercase English letters."
url: "https://leetcode.com/problems/palindrome-partitioning/description/"
favicon: ""
aspectRatio: "52"
```

```js
var partition = function(s) {
    const res = [];
    const backtrack = (start, path) => {
        if (start === s.length) {
            res.push([...path]); 
            return;
        }
        for (let end = start; end < s.length; end++) {
            if (isPal(s, start, end)) {
                path.push(s.substring(start, end + 1)); 
                backtrack(end + 1, path);              
                path.pop();                             
            }
        }
    };
    const isPal = (s, l, r) => {
        while (l < r) {
            if (s[l] !== s[r]) return false;
            l++;
            r--;
        }
        return true;
    };
    backtrack(0, []);
    return res;
};
```

## 78. Subsets
- [x] Check 
```embed
title: "Subsets - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Subsets - Given an integer array nums of unique elements, return all possible subsets (the power set).  The solution set must not contain duplicate subsets. Return the solution in any order.     Example 1:   Input: nums = [1,2,3] Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]   Example 2:   Input: nums = [0] Output: [[],[0]]      Constraints:   * 1 <= nums.length <= 10  * -10 <= nums[i] <= 10  * All the numbers of nums are unique."
url: "https://leetcode.com/problems/subsets/description/"
favicon: ""
aspectRatio: "52"
```

```js
var subsets = function(nums) {
    const res = [];
    const backtrack = (index, path) => {
        res.push([...path]); 
        for (let i = index; i < nums.length; i++) {
            path.push(nums[i]);      
            backtrack(i + 1, path);  
            path.pop();              
        }
    };
    backtrack(0, []);
    return res;
};
```

## 1239. Maximum Length of a Concatenated String with Unique Characters
- [x] Check 
```embed
title: "Maximum Length of a Concatenated String with Unique Characters - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Maximum Length of a Concatenated String with Unique Characters - You are given an array of strings arr. A string s is formed by the concatenation of a subsequence of arr that has unique characters.  Return the maximum possible length of s.  A subsequence is an array that can be derived from another array by deleting some or no elements without changing the order of the remaining elements.     Example 1:   Input: arr = [\"un\",\"iq\",\"ue\"] Output: 4 Explanation: All the valid concatenations are: - \"\" - \"un\" - \"iq\" - \"ue\" - \"uniq\" (\"un\" + \"iq\") - \"ique\" (\"iq\" + \"ue\") Maximum length is 4.   Example 2:   Input: arr = [\"cha\",\"r\",\"act\",\"ers\"] Output: 6 Explanation: Possible longest valid concatenations are \"chaers\" (\"cha\" + \"ers\") and \"acters\" (\"act\" + \"ers\").   Example 3:   Input: arr = [\"abcdefghijklmnopqrstuvwxyz\"] Output: 26 Explanation: The only string in arr has all 26 characters.      Constraints:   * 1 <= arr.length <= 16  * 1 <= arr[i].length <= 26  * arr[i] contains only lowercase English letters."
url: "https://leetcode.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/description/"
favicon: ""
aspectRatio: "52"
```

```js
var maxLength = function(arr) {
    let max = 0;

    const backtrack = (idx, cur, len) => {
        max = Math.max(max, len);
        for (let i = idx; i < arr.length; i++) {
            if (isUnique(cur, arr[i])) {
                backtrack(i + 1, cur + arr[i], len + arr[i].length);
            }
        }
    };
    const isUnique = (a, b) => {
        const freq = new Array(26).fill(0);
        for (const c of a) freq[c.charCodeAt(0) - 97]++;
        for (const c of b) {
            if (freq[c.charCodeAt(0) - 97]++ > 0) return false;
        }
        return true;
    };
    backtrack(0, "", 0);
    return max;
};

```

## 1219. Path with Maximum Gold
- [x] Check 
```embed
title: "Path with Maximum Gold - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Path with Maximum Gold - In a gold mine grid of size m x n, each cell in this mine has an integer representing the amount of gold in that cell, 0 if it is empty.  Return the maximum amount of gold you can collect under the conditions:   * Every time you are located in a cell you will collect all the gold in that cell.  * From your position, you can walk one step to the left, right, up, or down.  * You can't visit the same cell more than once.  * Never visit a cell with 0 gold.  * You can start and stop collecting gold from any position in the grid that has some gold.     Example 1:   Input: grid = [[0,6,0],[5,8,7],[0,9,0]] Output: 24 Explanation: [[0,6,0],  [5,8,7],  [0,9,0]] Path to get the maximum gold, 9 -> 8 -> 7.   Example 2:   Input: grid = [[1,0,7],[2,0,6],[3,4,5],[0,3,0],[9,0,20]] Output: 28 Explanation: [[1,0,7],  [2,0,6],  [3,4,5],  [0,3,0],  [9,0,20]] Path to get the maximum gold, 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7.      Constraints:   * m == grid.length  * n == grid[i].length  * 1 <= m, n <= 15  * 0 <= grid[i][j] <= 100  * There are at most 25 cells containing gold."
url: "https://leetcode.com/problems/path-with-maximum-gold/description/"
favicon: ""
aspectRatio: "52"
```

```js
var getMaximumGold = function(grid) {
    let max = 0;
    const m = grid.length, n = grid[0].length;
    const backtrack = (i, j, sum) => {
        if (i < 0 || j < 0 || i >= m || j >= n || grid[i][j] === 0) return;
        const gold = grid[i][j];
        grid[i][j] = 0;   
        sum += gold;
        max = Math.max(max, sum);
        backtrack(i + 1, j, sum);
        backtrack(i - 1, j, sum);
        backtrack(i, j + 1, sum);
        backtrack(i, j - 1, sum)
        grid[i][j] = gold; 
    };
    for (let i = 0; i < m; i++) {
        for (let j = 0; j < n; j++) {
            if (grid[i][j] > 0) backtrack(i, j, 0);
        }
    }
    return max;
};
```

