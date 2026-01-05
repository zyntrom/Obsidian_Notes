![[Pasted image 20260103090754.png]]

```java
import java.io.*;
import java.util.*;

public class Solution {
    public static void main(String[] args) {
        /* Enter your code here. Read input from STDIN. Print output to STDOUT.
           Your class should be named Solution. */
        Scanner s = new Scanner(System.in);
        String str = s.nextLine();
        String tokens[] = str.trim().split("\\s+");
        Stack<String> stack = new Stack<>();
        for (String token : tokens) {
            if (token.equals("+") || token.equals("-") ||
                token.equals("*") || token.equals("/")) {
                String op2 = stack.pop();
                String op1 = stack.pop();
                String expr = token + " " + op1 + " " + op2;
                stack.push(expr);
            } else {
                stack.push(token);
            }
        }
        System.out.print(stack.pop());
    }
}
```

![[Pasted image 20260103091057.png]]

```java
import java.util.*;

public class Solution {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        String num = s.next();
        int k = s.nextInt();
        StringBuilder sb = new StringBuilder(num);
        for (int i = 0; i < k; i++) {
            int j = 0;
            while (j < sb.length() - 1 && sb.charAt(j) <= sb.charAt(j + 1)) {
                j++;
            }
            sb.deleteCharAt(j);
        }
        while (sb.length() > 0 && sb.charAt(0) == '0') {
            sb.deleteCharAt(0);
        }
        if (sb.length() == 0) {
            System.out.println("0");
        } else {
            System.out.println(sb.toString());
        }
    }
}

```

![[Pasted image 20260103091144.png]]

```java
import java.io.*;
import java.util.*;

public class Solution {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int n = s.nextInt();
        int arr[] = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = s.nextInt();
        }
        int k = s.nextInt();
        for (int i = 0; i <= n - k; i++) {
            int max = arr[i];
            for (int j = i; j < i + k; j++) {
                if (arr[j] > max) {
                    max = arr[j];
                }
            }
            System.out.print(max + " ");
        }
    }
}

```

![[Pasted image 20260103091218.png]]

```java
import java.util.*;

public class Solution {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int n = s.nextInt();
        ArrayList<Integer> arr = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            arr.add(s.nextInt());
        }
        Stack<Integer> st = new Stack<>();
        for (int a : arr) {
            boolean destroyed = false;
            while (!st.isEmpty() && st.peek() > 0 && a < 0) {
                if (Math.abs(st.peek()) < Math.abs(a)) {
                    st.pop();
                    continue;
                } 
                else if (Math.abs(st.peek()) == Math.abs(a)) {
                    st.pop();
                }
                destroyed = true;
                break;
            }
            if (!destroyed) {
                st.push(a);
            }
        }
        if (st.isEmpty()) {
            System.out.print("Everything Destroyed");
        } else {
            for (int a : st) {
                System.out.print(a + " ");
            }
        }
    }
}

```

![[Pasted image 20260105091611.png]]

```java
import java.util.*;

public class PostfixToInfix {

    // Check if token is an operator
    static boolean isOperator(String token) {
        return token.equals("+") || token.equals("-") ||
               token.equals("*") || token.equals("/");
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        // Read the postfix expression
        String postfix = sc.nextLine();
        Stack<String> stack = new Stack<>();
        // Split input by spaces
        String[] tokens = postfix.split("\\s+");
        for (String token : tokens) {
            // If operand (number)
            if (!isOperator(token)) {
                stack.push(token);
            }
            // If operator
            else {
                String operand2 = stack.pop();
                String operand1 = stack.pop();
                // Form infix expression with parentheses
                String infix = "(" + operand1 + " " + token + " " + operand2 + ")";

                stack.push(infix);
            }
        }
        // Final infix expression
        System.out.println(stack.pop());
        sc.close();
    }
}

```

![[Pasted image 20260105091714.png]]

```java
import java.util.*;

public class Solution {
    static int precedence(char ch) {
        if (ch == '+' || ch == '-') return 1;
        if (ch == '*' || ch == '/') return 2;
        return 0;
    }
    static boolean isOperator(char ch) {
        return ch == '+' || ch == '-' || ch == '*' || ch == '/';
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String infix = sc.nextLine();   // Read infix expression
        Stack<Character> operators = new Stack<>();
        Stack<String> operands = new Stack<>();
        for (int i = 0; i < infix.length(); i++) {
            char ch = infix.charAt(i);
            if (ch == ' ') continue;
            // Operand
            if (Character.isDigit(ch)) {
                operands.push(String.valueOf(ch));
            }
            // Opening parenthesis
            else if (ch == '(') {
                operators.push(ch);
            }
            // Closing parenthesis
            else if (ch == ')') {
                while (operators.peek() != '(') {
                    char op = operators.pop();
                    String b = operands.pop();
                    String a = operands.pop();
                    operands.push(op + a + b);
                }
                operators.pop(); // remove '('
            }
            // Operator
            else if (isOperator(ch)) {
                while (!operators.isEmpty() &&
                       precedence(operators.peek()) > precedence(ch)) {
                    char op = operators.pop();
                    String b = operands.pop();
                    String a = operands.pop();
                    operands.push(op + a + b);
                }
                operators.push(ch);
            }
        }
        // Process remaining operators
        while (!operators.isEmpty()) {
            char op = operators.pop();
            String b = operands.pop();
            String a = operands.pop();
            operands.push(op + a + b);
        }
        // Output prefix expression
        System.out.println(operands.pop());
        sc.close();
    }
}

```

![[Pasted image 20260105095207.png]]

```java
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        // Read n
        int n = sc.nextInt();
        int[] height = new int[n];
        // Read heights
        for (int i = 0; i < n; i++) {
            height[i] = sc.nextInt();
        }
        int left = 0, right = n - 1;
        int leftMax = 0, rightMax = 0;
        int water = 0;
        // Two-pointer logic
        while (left < right) {
            if (height[left] <= height[right]) {
                if (height[left] >= leftMax) {
                    leftMax = height[left];
                } else {
                    water += leftMax - height[left];
                }
                left++;
            } else {
                if (height[right] >= rightMax) {
                    rightMax = height[right];
                } else {
                    water += rightMax - height[right];
                }
                right--;
            }
        }
        // Output result
        System.out.println(water);
        sc.close();
    }
}

```

![[Pasted image 20260105100045.png]]

```java
import java.util.*;

public class Solution {

    static final long MOD = 1000000007L;
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        long[] arr = new long[n];
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextLong();
        }
        int[] left = new int[n];
        int[] right = new int[n];
        // Primitive stack
        int[] stack = new int[n];
        int top = -1;
        // Previous Less Element (strict)
        for (int i = 0; i < n; i++) {
            while (top != -1 && arr[stack[top]] > arr[i]) {
                top--;
            }
            left[i] = (top == -1) ? i + 1 : i - stack[top];
            stack[++top] = i;
        }
        // Reset stack
        top = -1;
        // Next Less or Equal Element
        for (int i = n - 1; i >= 0; i--) {
            while (top != -1 && arr[stack[top]] >= arr[i]) {
                top--;
            }
            right[i] = (top == -1) ? n - i : stack[top] - i;
            stack[++top] = i;
        }
        long result = 0;
        for (int i = 0; i < n; i++) {
            long contribution = (arr[i] % MOD) * left[i] % MOD * right[i] % MOD;
            result = (result + contribution) % MOD;
        }
        System.out.println(result);
        sc.close();
    }
}

```

![[Pasted image 20260105112133.png]]

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        // Read size of array
        int N = sc.nextInt();
        // Read array elements
        long[] nums = new long[N];
        for (int i = 0; i < N; i++) {
            nums[i] = sc.nextLong();
        }
        long sum = 0;
        // Generate all subarrays
        for (int i = 0; i < N; i++) {
            long min = nums[i];
            long max = nums[i];
            for (int j = i; j < N; j++) {
                min = Math.min(min, nums[j]);
                max = Math.max(max, nums[j]);
                sum += (max - min);
            }
        }
        // Print result
        System.out.println(sum);
    }
}

```

![[Pasted image 20260105112721.png]]

```java
import java.util.*;

public class Solution {

    public static void solve(int i, String s, String f, List<String> svt) {
    //Answer
    
        // Base case: reached end of string
        if (i == s.length()) {
            if (f.length() > 0) {   // ignore empty subsequence
                svt.add(f);
            }
            return;
        }
        // Include current character
        solve(i + 1, s, f + s.charAt(i), svt);
        // Exclude current character
        solve(i + 1, s, f, svt);
    }
    
    //Answer 
    //Template
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.next();
        List<String> svt = new ArrayList<>();
        // Generate all subsequences
        solve(0, s, "", svt);
        // Sort the subsequences lexicographically
        Collections.sort(svt);
        // Output all subsequences
        for (String subseq : svt) {
            System.out.print(subseq + " ");
        }
    }
    //Template
}

```

![[Pasted image 20260105113210.png]]

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Solution {
	//Answer
	
    public static void backtrack(int open, int close, int n, String current, List<String> result) {
        // If the current string is complete
        if (current.length() == 2 * n) {
            result.add(current);
            return;
        }
        // Add '(' if we still can
        if (open < n) {
            backtrack(open + 1, close, n, current + "(", result);
        }
        // Add ')' only if it keeps the sequence valid
        if (close < open) {
            backtrack(open, close + 1, n, current + ")", result);
        }
    }
    public static List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList<>();
        backtrack(0, 0, n, "", result);
        return result;
    }
    
    //Answer
    //Template
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        List<String> combinations = generateParenthesis(n);
        for (int i = 0; i < combinations.size(); i++) {
            if (i > 0) System.out.print(" ");
            System.out.print(combinations.get(i));
        }
        System.out.println();
        sc.close();
    }
    //Template
}

```

![[Pasted image 20260105114045.png]]

```java
import java.util.*;

public class Solution {
	//Answer
    // Helper backtracking function
    public static void backtrack(
            int index,
            List<Integer> candidates,
            int target,
            List<Integer> current,
            List<List<Integer>> result
    ) {
        // If target becomes 0, we found a valid combination
        if (target == 0) {
            result.add(new ArrayList<>(current));
            return;
        }
        // If target goes negative or index out of bounds
        if (target < 0 || index == candidates.size()) {
            return;
        }
        // Include current number (can be reused)
        current.add(candidates.get(index));
        backtrack(index, candidates, target - candidates.get(index), current, result);
        current.remove(current.size() - 1);
        // Exclude current number and move to next index
        backtrack(index + 1, candidates, target, current, result);
    }
    // Function to find all unique combinations that sum to the target
    public static List<List<Integer>> combinationSum(List<Integer> candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(0, candidates, target, new ArrayList<>(), result);
        return result;
    }
    //Answer
    
    //Template
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        // Input the number of elements in the array
        int n = sc.nextInt();
        List<Integer> arr = new ArrayList<>();
        // Input the elements of the array
        for (int i = 0; i < n; i++) {
            arr.add(sc.nextInt());
        }
        // Input the target sum
        int target = sc.nextInt();
        // Sort the array
        Collections.sort(arr);
        // Get all unique combinations
        List<List<Integer>> ans = combinationSum(arr, target);
        // Sort result lexicographically
        ans.sort((a, b) -> {
            for (int i = 0; i < Math.min(a.size(), b.size()); i++) {
                if (!a.get(i).equals(b.get(i))) {
                    return a.get(i) - b.get(i);
                }
            }
            return a.size() - b.size();
        });
        // Print the result
        if (ans.isEmpty()) {
            System.out.println(-1);
        } else {
            for (List<Integer> combination : ans) {
                for (int num : combination) {
                    System.out.print(num + " ");
                }
                System.out.println();
            }
        }
        sc.close();
    }
    //Template
}

```

![[Pasted image 20260105115312.png]]

```java
import java.util.*;

public class Solution {
	//Answer
    // Function to generate all subsets
    public static List<List<Integer>> subsets(List<Integer> arr) {
        List<List<Integer>> result = new ArrayList<>();
        
        // Sort the array to ensure lexicographical order
        Collections.sort(arr);
        
        // Backtracking to generate subsets
        backtrack(arr, 0, new ArrayList<>(), result);
        
        return result;
    }
    
    private static void backtrack(List<Integer> arr, int index,
                                  List<Integer> current,
                                  List<List<Integer>> result) {
        // Add current subset to result
        result.add(new ArrayList<>(current));
        
        for (int i = index; i < arr.size(); i++) {
            current.add(arr.get(i));
            backtrack(arr, i + 1, current, result);
            current.remove(current.size() - 1);
        }
    }
    //Answer
    //Template
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        List<Integer> arr = new ArrayList<>();
        
        for (int i = 0; i < n; i++) {
            arr.add(sc.nextInt());
        }
        
        List<List<Integer>> ans = subsets(arr);
        
        for (List<Integer> subset : ans) {
            for (int num : subset) {
                System.out.print(num + " ");
            }
            System.out.println();
        }
        
        if (ans.isEmpty()) {
            System.out.println(-1);
        }
        
        sc.close();
    }
    //Template
}

```

![[Pasted image 20260105120030.png]]

```java
import java.util.*;

public class Solution {
	//Answer
    public static int getMaximumGold(int[][] grid) {
        int maxGold = 0;
        int m = grid.length;
        int n = grid[0].length;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] > 0) {
                    maxGold = Math.max(maxGold, dfs(grid, i, j));
                }
            }
        }
        return maxGold;
    }
    private static int dfs(int[][] grid, int i, int j) {
        // Boundary or invalid cell
        if (i < 0 || j < 0 || i >= grid.length || j >= grid[0].length || grid[i][j] == 0) {
            return 0;
        }
        int gold = grid[i][j];
        grid[i][j] = 0; // mark visited
        int max = 0;
        max = Math.max(max, dfs(grid, i + 1, j));
        max = Math.max(max, dfs(grid, i - 1, j));
        max = Math.max(max, dfs(grid, i, j + 1));
        max = Math.max(max, dfs(grid, i, j - 1));
        grid[i][j] = gold; // backtrack
        return gold + max;
    }
    //Answer
    //Template
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int m = sc.nextInt();
        int n = sc.nextInt();
        int[][] grid = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                grid[i][j] = sc.nextInt();
            }
        }
        System.out.println(getMaximumGold(grid));
    }
    //Template
}

```

![[Pasted image 20260105121653.png]]

```java
import java.util.Arrays;

public class Solution {
	//Answer
    static int count;
    public static int countArrangement(int n) {
        count = 0;
        boolean[] used = new boolean[n + 1];
        backtrack(1, n, used);
        return count;
    }
    private static void backtrack(int pos, int n, boolean[] used) {
        if (pos > n) {
            count++;
            return;
        }
        for (int num = 1; num <= n; num++) {
            if (!used[num] && (num % pos == 0 || pos % num == 0)) {
                used[num] = true;
                backtrack(pos + 1, n, used);
                used[num] = false; // backtrack
            }
        }
    }
    //Answer
    //Template
    public static void main(String[] args) {
        java.util.Scanner sc = new java.util.Scanner(System.in);
        int n = sc.nextInt();
        System.out.println(countArrangement(n));
        sc.close();
    }
    //Template
}

```

