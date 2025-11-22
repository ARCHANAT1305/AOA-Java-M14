
# EX 4E Longest Increasing Subsequence - Dynamic Programming.
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return the length of the longest strictly increasing subsequence.
Example 1:
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
## Algorithm
1. Start and read the number of elements n and the array nums[].
2. Initialize an array dp[] of size n, where each element starts as 1, representing the minimum length of a subsequence ending at that index.
3. For each element nums[i], check all previous elements nums[j] (j < i); if nums[i] > nums[j], update dp[i] = max(dp[i], dp[j] + 1).
4. After filling the dp array, find the maximum value in dp[], which represents the longest increasing subsequence length.
5. Print the maximum subsequence length and stop.

## Program:
#### Developed by: ARCHANA T
#### Register Number: 212223240013
```
import java.util.*;

public class LongestIncreasingSubsequence {

    public static int lengthOfLIS(int[] nums) {
        int n = nums.length;
        if (n == 0) return 0;

        int[] dp = new int[n];
        Arrays.fill(dp, 1);  
        for (int i = 1; i < n; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
        }
        int maxLen = 0;
        for (int len : dp) {
            maxLen = Math.max(maxLen, len);
        }

        return maxLen;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        int result = lengthOfLIS(nums);
        System.out.println("Length of Longest Increasing Subsequence: " + result);

        scanner.close();
    }
}
```

## Output:

<img width="858" height="178" alt="image" src="https://github.com/user-attachments/assets/fcb4824a-1801-4e8d-9a54-2171506c5617" />


## Result:
The program successfully implemented and the expected output is verified.
