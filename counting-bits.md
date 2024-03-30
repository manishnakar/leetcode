Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

Here's the JavaScript code to solve the problem:

```javascript
/**
 * @param {number} n
 * @return {number[]}
 */
var countBits = function(n) {
    const ans = new Array(n + 1).fill(0);
    
    for (let i = 1; i <= n; i++) {
        ans[i] = ans[i >> 1] + (i & 1);
    }
    
    return ans;
};
```

Explanation:

1. We create an array `ans` of length `n + 1` and initialize all elements to 0. This array will store the count of 1's in the binary representation of each number from 0 to n.

2. We start a loop from `i = 1` to `i = n` (inclusive). For each iteration:
   - We calculate the count of 1's for the current number `i` using the following formula:
     ```
     ans[i] = ans[i >> 1] + (i & 1)
     ```
     - `i >> 1` performs a right shift by 1 bit, effectively dividing `i` by 2. This gives us the count of 1's for the number `i / 2`.
     - `i & 1` performs a bitwise AND operation with 1, which checks if the least significant bit of `i` is 1 or 0. If it is 1, we add 1 to the count; otherwise, we add 0.
   - By adding the count of 1's for `i / 2` (stored in `ans[i >> 1]`) and the least significant bit of `i`, we get the count of 1's for the current number `i`.

3. Finally, we return the `ans` array containing the count of 1's for each number from 0 to n.

The time complexity of this solution is O(n), as we iterate from 1 to n. The space complexity is also O(n) to store the `ans` array.

Here are a few examples:

```javascript
console.log(countBits(2)); // Output: [0, 1, 1]
console.log(countBits(5)); // Output: [0, 1, 1, 2, 1, 2]
```

In the first example, the binary representations of numbers 0, 1, and 2 are "0", "1", and "10", respectively. The corresponding counts of 1's are 0, 1, and 1.

In the second example, the binary representations of numbers 0 to 5 are "0", "1", "10", "11", "100", and "101". The corresponding counts of 1's are 0, 1, 1, 2, 1, and 2.
