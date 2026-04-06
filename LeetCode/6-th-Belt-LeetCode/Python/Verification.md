## 1. Letter Combinations of a Phone Number

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

```

## 10. Partition Equal Subset Sum

```python

```

## 11. Max Number of K-Sum Pairs

```python

```

## 12. Path with Maximum Gold

```python

```

## 13. Find the Winner of the Circular Game

```python

```

## 14. Unique Paths

```python

```