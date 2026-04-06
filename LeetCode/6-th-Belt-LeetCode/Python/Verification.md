## 1. Letter Combinations of a Phone Number

```embed
title: "Letter Combinations of a Phone Number - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Letter Combinations of a Phone Number - Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.  A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.  [https://assets.leetcode.com/uploads/2022/03/15/1200px-telephone-keypad2svg.png]     Example 1:   Input: digits = \"23\" Output: [\"ad\",\"ae\",\"af\",\"bd\",\"be\",\"bf\",\"cd\",\"ce\",\"cf\"]   Example 2:   Input: digits = \"2\" Output: [\"a\",\"b\",\"c\"]      Constraints:   * 1 <= digits.length <= 4  * digits[i] is a digit in the range ['2', '9']."
url: "https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def letterCombinations(self, digits):
        if not digits:
            return []
        mapping = ["", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"]
        ans = []
        def backtrack(index, path):
            if index == len(digits):
                ans.append("".join(path))
                return
            letters = mapping[int(digits[index])]
            for ch in letters:
                path.append(ch)           
                backtrack(index + 1, path) 
                path.pop()                  
        backtrack(0, [])
        return ans
```

## 2. Subsets

```embed
title: "Subsets - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Subsets - Given an integer array nums of unique elements, return all possible subsets (the power set).  The solution set must not contain duplicate subsets. Return the solution in any order.     Example 1:   Input: nums = [1,2,3] Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]   Example 2:   Input: nums = [0] Output: [[],[0]]      Constraints:   * 1 <= nums.length <= 10  * -10 <= nums[i] <= 10  * All the numbers of nums are unique."
url: "https://leetcode.com/problems/subsets/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def subsets(self, nums):
        res = []
        def backtrack(index, path):
            res.append(path[:])  
            for i in range(index, len(nums)):
                path.append(nums[i])        
                backtrack(i + 1, path)     
                path.pop()                  
        backtrack(0, [])
        return res
```

## 3. Permutations

```embed
title: "Permutations - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Permutations - Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.     Example 1:  Input: nums = [1,2,3] Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]   Example 2:  Input: nums = [0,1] Output: [[0,1],[1,0]]   Example 3:  Input: nums = [1] Output: [[1]]      Constraints:   * 1 <= nums.length <= 6  * -10 <= nums[i] <= 10  * All the integers of nums are unique."
url: "https://leetcode.com/problems/permutations/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def permute(self, nums):
        ans = []
        def backtrack(curr):
            if len(curr) == len(nums):
                ans.append(curr[:]) 
                return
            for num in nums:
                if num in curr:  
                    continue
                curr.append(num)      
                backtrack(curr)       
                curr.pop()             
        backtrack([])
        return ans
```

## 4. Generate Parentheses

```embed
title: "Generate Parentheses - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Generate Parentheses - Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.     Example 1:  Input: n = 3 Output: [\"((()))\",\"(()())\",\"(())()\",\"()(())\",\"()()()\"]   Example 2:  Input: n = 1 Output: [\"()\"]      Constraints:   * 1 <= n <= 8"
url: "https://leetcode.com/problems/generate-parentheses/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def generateParenthesis(self, n):
        res = []
        def backtrack(cur, open_count, close_count):
            if len(cur) == 2 * n:
                res.append("".join(cur))
                return
            if open_count < n:
                cur.append('(')
                backtrack(cur, open_count + 1, close_count)  
                cur.pop()
            if close_count < open_count:
                cur.append(')')
                backtrack(cur, open_count, close_count + 1)  
                cur.pop()                                  
        backtrack([], 0, 0)
        return res
```

## 5. Combination Sum

```embed
title: "Combination Sum - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Combination Sum - Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.  The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.  The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.     Example 1:   Input: candidates = [2,3,6,7], target = 7 Output: [[2,2,3],[7]] Explanation: 2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times. 7 is a candidate, and 7 = 7. These are the only two combinations.   Example 2:   Input: candidates = [2,3,5], target = 8 Output: [[2,2,2,2],[2,3,3],[3,5]]   Example 3:   Input: candidates = [2], target = 1 Output: []      Constraints:   * 1 <= candidates.length <= 30  * 2 <= candidates[i] <= 40  * All elements of candidates are distinct.  * 1 <= target <= 40"
url: "https://leetcode.com/problems/combination-sum/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def combinationSum(self, nums, target):
        nums.sort() 
        res = []
        def backtrack(remaining, start, curr):
            if remaining == 0:
                res.append(curr[:]) 
                return
            for i in range(start, len(nums)):
                if nums[i] > remaining:
                    break  
                curr.append(nums[i])            
                backtrack(remaining - nums[i], i, curr) 
                curr.pop()                       
        backtrack(target, 0, [])
        return res
```

## 6. Combination Sum  II

```embed
title: "Combination Sum II - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Combination Sum II - Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.  Each number in candidates may only be used once in the combination.  Note: The solution set must not contain duplicate combinations.     Example 1:   Input: candidates = [10,1,2,7,6,1,5], target = 8 Output:  [ [1,1,6], [1,2,5], [1,7], [2,6] ]   Example 2:   Input: candidates = [2,5,2,1,2], target = 5 Output:  [ [1,2,2], [5] ]      Constraints:   * 1 <= candidates.length <= 100  * 1 <= candidates[i] <= 50  * 1 <= target <= 30"
url: "https://leetcode.com/problems/combination-sum-ii/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def combinationSum2(self, nums, target):
        nums.sort() 
        res = []
        def backtrack(remaining, start, curr):
            if remaining == 0:
                res.append(curr[:]) 
                return
            for i in range(start, len(nums)):
                if i > start and nums[i] == nums[i - 1]:
                    continue
                if nums[i] > remaining:
                    break
                curr.append(nums[i])                     
                backtrack(remaining - nums[i], i + 1, curr)
                curr.pop()
        backtrack(target, 0, [])
        return res
```

## 7. Word Search

```embed
title: "Word Search - LeetCode"
image: "https://leetcode.com/static/images/LeetCode_Sharing.png"
description: "Can you solve this real interview question? Word Search - Given an m x n grid of characters board and a string word, return true if word exists in the grid.  The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.     Example 1:  [https://assets.leetcode.com/uploads/2020/11/04/word2.jpg]   Input: board = [[\"A\",\"B\",\"C\",\"E\"],[\"S\",\"F\",\"C\",\"S\"],[\"A\",\"D\",\"E\",\"E\"]], word = \"ABCCED\" Output: true   Example 2:  [https://assets.leetcode.com/uploads/2020/11/04/word-1.jpg]   Input: board = [[\"A\",\"B\",\"C\",\"E\"],[\"S\",\"F\",\"C\",\"S\"],[\"A\",\"D\",\"E\",\"E\"]], word = \"SEE\" Output: true   Example 3:  [https://assets.leetcode.com/uploads/2020/10/15/word3.jpg]   Input: board = [[\"A\",\"B\",\"C\",\"E\"],[\"S\",\"F\",\"C\",\"S\"],[\"A\",\"D\",\"E\",\"E\"]], word = \"ABCB\" Output: false      Constraints:   * m == board.length  * n = board[i].length  * 1 <= m, n <= 6  * 1 <= word.length <= 15  * board and word consists of only lowercase and uppercase English letters.     Follow up: Could you use search pruning to make your solution faster with a larger board?"
url: "https://leetcode.com/problems/word-search/description/"
favicon: ""
aspectRatio: "52"
```

```python
class Solution:
    def exist(self, board, word):
        m, n = len(board), len(board[0])
        def backtrack(i, j, idx):
            if idx == len(word):
                return True
            if i < 0 or j < 0 or i >= m or j >= n:
                return False
            if board[i][j] != word[idx]:
                return False
            temp = board[i][j]
            board[i][j] = '#'
            found = (
                backtrack(i + 1, j, idx + 1) or
                backtrack(i - 1, j, idx + 1) or
                backtrack(i, j + 1, idx + 1) or
                backtrack(i, j - 1, idx + 1)
            )
            board[i][j] = temp
            return found
        for i in range(m):
            for j in range(n):
                if backtrack(i, j, 0):
                    return True
        return False
```

## 8. Palindrome Partitioning

```python
class Solution:
    def partition(self, s):
        res = []
        def is_palindrome(l, r):
            while l < r:
                if s[l] != s[r]:
                    return False
                l += 1
                r -= 1
            return True
        def backtrack(start, path):
            if start == len(s):
                res.append(path[:])  
                return
            for end in range(start, len(s)):
                if is_palindrome(start, end):
                    path.append(s[start:end + 1])  
                    backtrack(end + 1, path)       
                    path.pop()                      
        backtrack(0, [])
        return res
```

## 9. N-Queens

```python
class Solution:
    def solveNQueens(self, n):
        self.n = n
        self.ans = []
        self.col = [False] * n
        self.diag1 = [False] * (2 * n)
        self.diag2 = [False] * (2 * n)
        board = [['.'] * n for _ in range(n)]   
        self.backtrack(0, board)
        return self.ans
    def backtrack(self, row, board):
        if row == self.n:
            self.ans.append(self.toList(board))
            return
        for c in range(self.n):
            d1 = row - c + self.n
            d2 = row + c     
            if self.col[c] or self.diag1[d1] or self.diag2[d2]:
                continue
            board[row][c] = 'Q'
            self.col[c] = self.diag1[d1] = self.diag2[d2] = True
            self.backtrack(row + 1, board)
            board[row][c] = '.'
            self.col[c] = self.diag1[d1] = self.diag2[d2] = False
    def toList(self, board):
        res = []
        for r in board:
            res.append(''.join(r))
        return res
```

## 10. Partition Equal Subset Sum

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

## 11. Max Number of K-Sum Pairs

```python
class Solution(object):
    def maxOperations(self, nums, k):
        nums.sort()
        left = 0
        right = len(nums) - 1
        count = 0
        while left < right:
            s = nums[left] + nums[right]
            if s == k:
                count += 1
                left += 1
                right -= 1
            elif s < k:
                left += 1
            else:
                right -= 1
        return count
```

## 12. Path with Maximum Gold

```python
class Solution:
    def getMaximumGold(self, grid):
        self.max_gold = 0
        m = len(grid)
        n = len(grid[0])
        def backtrack(i, j, current_sum):
            if i < 0 or j < 0 or i >= m or j >= n or grid[i][j]==0:
                return
            gold = grid[i][j]
            grid[i][j] = 0   
            current_sum += gold
            if current_sum > self.max_gold:
                self.max_gold = current_sum
            backtrack(i + 1, j, current_sum)
            backtrack(i - 1, j, current_sum)
            backtrack(i, j + 1, current_sum)
            backtrack(i, j - 1, current_sum)
            grid[i][j] = gold
        for i in range(m):
            for j in range(n):
                if grid[i][j] > 0:
                    backtrack(i, j, 0)
        return self.max_gold
```

## 13. Find the Winner of the Circular Game

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

## 14. Unique Paths

```python
class Solution(object):
    def uniquePaths(self, m, n):
        dp = [1] * n
        for i in range(1, m):
            for j in range(1, n):
                dp[j] += dp[j - 1]
        return dp[n - 1]
```