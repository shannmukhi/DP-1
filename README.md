# DP-1

## Problem1 (https://leetcode.com/problems/coin-change/)
You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

Example 1:

Input: coins = [1, 2, 5], amount = 11
Output: 3 
Explanation: 11 = 5 + 5 + 1
Example 2:

Input: coins = [2], amount = 3
Output: -1
Note:
You may assume that you have an infinite number of each kind of coin.
class coinchange { 

static long getNumberOfWays(long N, long[] Coins) 
	{ 
   long[] ways = new long[(int)N + 1]; 
		ways[0] = 1; 
		for (int i = 0; i < Coins.length; i++) { 
for (int j = 0; j < ways.length; j++)
 { 
				if (Coins[i] <= j)
 { 
	ways[j] += ways[(int)(j - Coins[i])]; 
} 
} 
} 
return ways[(int)N]; 
} 
	static void printArray(long[] coins) 
	{ 
		for (long i : coins) 
			System.out.println(i); 
	} 
	public static void main(String args[]) 
	{ 
		long Coins[] = { 1, 5, 10 }; 
		System.out.println("The Coins Array:"); 
		printArray(Coins); 
		System.out.println("Solution:"); 
		System.out.println(getNumberOfWays(12, Coins)); 
	} 
} 
## Problem2 (https://leetcode.com/problems/house-robber/)
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

Example 1:

Input: [1,2,3,1]

Output: 4

Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).


             Total amount you can rob = 1 + 3 = 4.
Example 2:

Input: [2,7,9,3,1]

Output: 12

Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).


             Total amount you can rob = 2 + 9 + 1 = 12.
              import java.io.*; 
//Program:
class  maxstolen
{ 
	static int maxLoot(int hval[], int n) 
	{ 
		if (n == 0) 
		return 0; 
		if (n == 1) 
			return hval[0]; 
		if (n == 2) 
			return Math.max(hval[0], hval[1]); 
int[] dp = new int[n]; 
dp[0] = hval[0]; 
dp[1] = Math.max(hval[0], hval[1]); 
for (int i = 2; i<n; i++) 
			dp[i] = Math.max(hval[i]+dp[i-2], dp[i-1]); 
		return dp[n-1]; 
	} 
	// Driver program 
	public static void main (String[] args) 
	{ 
		int hval[] = {6, 7, 1, 3, 8, 2, 4}; 
		int n = hval.length; 
		System.out.println("Maximum loot value : " + maxLoot(hval, n)); 
	} 
} 

