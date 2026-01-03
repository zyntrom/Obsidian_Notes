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