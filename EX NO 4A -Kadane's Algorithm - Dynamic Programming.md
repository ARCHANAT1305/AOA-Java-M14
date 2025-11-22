
# EX 4A Kadane's Algorithm - Dynamic Programming. 
## AIM:
To Write a Java program to solve the below problem using Kadane's Algorithm.
A solar company installs solar panels around a circular grid of n buildings. Each building either generates or consumes net energy, represented by integers (+ve for generated, -ve for consumed).

The company wants to find a contiguous sequence of buildings (possibly wrapping around from the end to the beginning) that maximizes the total net energy.

Write a program to compute the maximum net energy that can be collected from any contiguous block of buildings on the circular grid.

Input Format:
First line: Integer n (number of buildings)

Second line: n space-separated integers: net energy for each building

Output Format:
A single integer: Maximum net energy collectable from a contiguous block (wrapping allowed)

Constraints:
1 <= n <= 10^6
## Algorithm
1. Start and read the number of solar panels n and their energy values into an array energy[].
2. Compute the total energy sum of the array and find the maximum subarray sum using Kadane’s algorithm (for non-circular case).
3. Find the minimum subarray sum using a modified Kadane’s algorithm (for circular wrap-around case)
4. Calculate the wrapped sum as total sum - minimum subarray sum and compare it with the normal maximum subarray sum.
5. Return the higher of the two as the maximum circular energy output, print the result, and stop.

## Program:
#### Developed by: ARCHANA T
#### Register Number:212223240013 
```
import java.util.*;

public class SolarEnergyMaximizer {

    public static int maxCircularEnergy(int[] energy)     {
        //Type your code
        int sum=0;
        for(int i:energy)
        {
            sum+=i;
        }
        int maxsum=maxsubarraysum(energy);
        int minsum=minsubarraysum(energy);
        int wrappedDifference=sum-minsum;
        if(maxsum<0)return maxsum;
        return Math.max(maxsum,wrappedDifference);
    }
    
    public static int maxsubarraysum(int[] energy)
    {
        int sum=0,maxsum=energy[0];
        for(int i: energy)
        {
            sum+=i;
            if(sum>maxsum)
            {
                maxsum=sum;
            }
            if(sum<0) sum=0;
        }
        return maxsum;
    }
    
    public static int minsubarraysum(int[] energy)
    {
        int sum=0,minsum=energy[0];
        for(int i:energy)
        {
            sum+=i;
            if(sum<minsum) minsum=sum;
            if(sum>0) sum=0;
        }
        return minsum;
        
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] energy = new int[n];
        for (int i = 0; i < n; i++) {
            energy[i] = sc.nextInt();
        }
        System.out.println(maxCircularEnergy(energy));
    }
}
```

## Output:

<img width="328" height="169" alt="image" src="https://github.com/user-attachments/assets/8ccb3dda-8f59-4b29-a62e-bcfa43a24fdf" />


## Result:
The program successfully Implemented and the output is verified. 
