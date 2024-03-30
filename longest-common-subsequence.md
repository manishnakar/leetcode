Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".
A common subsequence of two strings is a subsequence that is common to both strings.

Here's the JavaScript code to find the length of the longest common subsequence (LCS) between two strings:

```javascript
function longestCommonSubsequence(text1, text2) {
  const m = text1.length;
  const n = text2.length;
  const dp = Array(m + 1).fill().map(() => Array(n + 1).fill(0));

  for (let i = 1; i <= m; i++) {
    for (let j = 1; j <= n; j++) {
      if (text1[i - 1] === text2[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1] + 1;
      } else {
        dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
      }
    }
  }

  return dp[m][n];
}

// Example usage
const text1 = "abcde";
const text2 = "ace";
console.log(longestCommonSubsequence(text1, text2)); // Output: 3
```

Explanation:

1. We define a function called `longestCommonSubsequence` that takes two strings `text1` and `text2` as input.

2. We initialize variables `m` and `n` to store the lengths of `text1` and `text2`, respectively.

3. We create a 2D array `dp` of size `(m + 1) x (n + 1)` and initialize all elements to 0. This array will store the lengths of the LCS for different subproblems.

4. We use nested loops to iterate over the characters of `text1` and `text2`. The outer loop iterates from `1` to `m`, and the inner loop iterates from `1` to `n`.

5. Inside the loops, we check if the characters at the current positions (`i - 1` in `text1` and `j - 1` in `text2`) are equal. If they are equal, we increment the length of the LCS by 1 and store it in `dp[i][j]`. If they are not equal, we take the maximum value between the LCS length without including the current character from `text1` (`dp[i - 1][j]`) and the LCS length without including the current character from `text2` (`dp[i][j - 1]`).

6. After the loops complete, the length of the LCS between `text1` and `text2` will be stored in `dp[m][n]`, which we return as the result.

7. Finally, we provide an example usage of the `longestCommonSubsequence` function by calling it with the strings "abcde" and "ace". The output will be 3, indicating that the length of the longest common subsequence between these two strings is 3 (which is "ace").

The time complexity of this solution is O(mn), where m and n are the lengths of `text1` and `text2`, respectively. The space complexity is also O(mn) to store the `dp` array.
