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

```