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