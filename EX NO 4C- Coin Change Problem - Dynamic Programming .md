
# EX 4C Coin Change Problem - Dynamic Programming.
## AIM:
To write a Java program to for given constraints.
You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

## Algorithm
1. Start and read the list of coin denominations and the target amount.
2. Initialize a dynamic programming array dp[] of size amount + 1, filled with a large number, and set dp[0] = 0 (since 0 coins are needed for amount 0).
3. For each amount i from 1 to amount, iterate through each coin value.
4. If the coin value is less than or equal to i, update dp[i] = min(dp[i], dp[i - coin] + 1) to find the minimum coins required.
5. After processing all amounts, if dp[amount] is still large, print -1 (not possible); otherwise, print dp[amount] as the minimum number of coins needed and stop.

## Program:
#### Developed by: ARCHANA T
#### Register Number: 212223240013
```
import java.util.*;

public class Solution {
    public int coinChange(int[] coins, int amount) {
        // DP array to store the minimum number of coins for each amount
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1); // Fill with a large number
        dp[0] = 0; // Base case: 0 coins needed to make amount 0

        // Compute minimum coins for all amounts up to 'amount'
        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (coin <= i) {
                    dp[i] = Math.min(dp[i], dp[i - coin] + 1);
                }
            }
        }

        // If dp[amount] is still large, it means amount cannot be formed
        return dp[amount] > amount ? -1 : dp[amount];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution solution = new Solution();

        String coinsLine = scanner.nextLine(); 
        String amountLine = scanner.nextLine();

        coinsLine = coinsLine.replaceAll("[^0-9,]", ""); 
        String[] coinsStr = coinsLine.split(",");
        int[] coins = new int[coinsStr.length];
        for (int i = 0; i < coinsStr.length; i++) {
            coins[i] = Integer.parseInt(coinsStr[i]);
        }

        int amount = Integer.parseInt(amountLine.replaceAll("[^0-9]", ""));
        int result = solution.coinChange(coins, amount);
        System.out.println(result);

        scanner.close();
    }
}

```

## Output:

<img width="425" height="172" alt="image" src="https://github.com/user-attachments/assets/1880d497-99af-45d8-9c15-f614f66beaff" />


## Result:
The program successfully implemented and the expected output is verified.
