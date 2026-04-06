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

```

## 3. Permutations

```python

```

## 4. Generate Parentheses

```python

```

## 5. Combination Sum

```python

```

## 6. Combination Sum  II

```python

```

## 7. Word Search

```python

```

## 8. Palindrome Partitioning

```python

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