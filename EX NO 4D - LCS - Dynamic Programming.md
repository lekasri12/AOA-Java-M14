
# EX 4D Longest Common SubSequence - Dynamic Programming.
## DATE: 07.11.2025
## AIM:
To write a Java program to for given constraints.
Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.
A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".
A common subsequence of two strings is a subsequence that is common to both strings.

Input: text1 = "abcde", text2 = "ace" 
Output: 3  
Explanation: The longest common subsequence is "ace" and its length is 3.
Constraints:

1 <= text1.length, text2.length <= 1000
text1 and text2 consist of only lowercase English characters.

## Algorithm
Step 1: Initialize variables

Let m = X.length() and n = Y.length().
Create a 2D array dp[m+1][n+1] to store subproblem results.

Step 2: Set base conditions

For all i and j,
if i == 0 or j == 0, then
dp[i][j] = 0
→ (Because an empty string has no common subsequence)

Step 3: Fill the DP table

Use nested loops:

for i = 1 to m
    for j = 1 to n
        if (X[i-1] == Y[j-1])
            dp[i][j] = dp[i-1][j-1] + 1
        else
            dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1])

Step 4: Extract the result

The value dp[m][n] will contain the length of the LCS.

Step 5: (Optional) Backtrack to get the actual LCS string

Start from dp[m][n] and trace back:

If characters match, include that character.

Else, move in the direction of the larger value (up or left).   

## Program:
```
/*
Developed by: LEKASRI G
RegisterNumber:  212223100025
*/

import java.util.Scanner;

public class Solution {

    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();

        int[][] dp = new int[m + 1][n + 1]; // dp[i][j] = LCS of text1[0..i-1] & text2[0..j-1]

        // Fill dp table
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }

        return dp[m][n];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        String text1 = sc.nextLine().replaceAll("\"", "");
        String text2 = sc.nextLine().replaceAll("\"", "");

        int lcsLength = sol.longestCommonSubsequence(text1, text2);
        System.out.println("Length of Longest Common Subsequence: " + lcsLength);

        sc.close();
    }
}

```

## Output:
<img width="833" height="255" alt="image" src="https://github.com/user-attachments/assets/f08d14f5-2d4e-454b-a4c0-ecbe868c1ad3" />


## Result:
The program successfully implemented and the expected output is verified.
