
# EX 4B Frog Jump - Dynamic Programming.
## AIM:
To write a Java program to for given constraints.
A Frog Jump 1 or 2 steps at a time.
Problem Statement:

A frog is at the bottom of the stairs with n steps. It can jump either 1 or 2 steps at a time. Write a program to find the number of distinct ways the frog can reach the top (n-th step).

Input Format:

A single integer n (1 ≤ n ≤ 45) – number of steps.
 Output Format:

A single integer – number of distinct ways to reach step n.

## Algorithm
1. Start and read the number of steps n the frog needs to jump.
2. If n is 0 or 1, return 1 since there’s only one way to stay or jump one step.
3. Initialize two variables first and second to represent ways to reach the previous two steps.
4. Use a loop from 2 to n, updating current = first + second to calculate total ways dynamically.
5. After completing the loop, print current as the total number of ways the frog can reach the top and stop.   

## Program:
#### Developed by: ARCHANA T
#### Register Number: 212223240013
```
import java.util.Scanner;

public class FrogJump {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        scanner.close();
        System.out.println(countWays(n));
    }
    public static int countWays(int n) {
        if (n == 0) return 1; 
        if (n == 1) return 1;  
        int first = 1;  
        int second = 1; 
        int current = 0;
        for (int i = 2; i <= n; i++) {
            current = first + second;  
            first = second;
            second = current;
        }
        return current;
    }
}

```

## Output:

<img width="410" height="165" alt="image" src="https://github.com/user-attachments/assets/87418284-ebcf-41b0-bbb7-426d73fb260b" />


## Result:
The program successfully implemented and the expected output is verified.
