You are given an array of strings products and a string searchWord.

Design a system that suggests at most three product names from products after each character of searchWord is typed. Suggested products should have common prefix with searchWord. If there are more than three products with a common prefix return the three lexicographically minimums products.

Return a list of lists of the suggested products after each character of searchWord is typed.

Here's the JavaScript code to solve the problem:

```javascript
/**
 * @param {string[]} products
 * @param {string} searchWord
 * @return {string[][]}
 */
var suggestedProducts = function(products, searchWord) {
    // Sort the products array lexicographically
    products.sort();
    
    const result = [];
    let left = 0;
    let right = products.length - 1;
    
    for (let i = 0; i < searchWord.length; i++) {
        const prefix = searchWord.slice(0, i + 1);
        
        // Find the first product with the current prefix
        while (left <= right && !products[left].startsWith(prefix)) {
            left++;
        }
        
        // Find the last product with the current prefix
        while (left <= right && !products[right].startsWith(prefix)) {
            right--;
        }
        
        // Add the suggested products to the result array
        const suggestedProducts = products.slice(left, Math.min(left + 3, right + 1));
        result.push(suggestedProducts);
    }
    
    return result;
};
```

Explanation:

1. We start by sorting the `products` array lexicographically. This will help us find the suggested products efficiently.

2. We initialize an empty array `result` to store the suggested products for each prefix of `searchWord`.

3. We use two pointers, `left` and `right`, to keep track of the range of products that have the current prefix.

4. We iterate over each character of `searchWord` using a loop from index 0 to `searchWord.length - 1`.

5. For each iteration:
   - We extract the current prefix by slicing `searchWord` from index 0 to `i + 1`.
   - We move the `left` pointer to the right until we find the first product that starts with the current prefix.
   - We move the `right` pointer to the left until we find the last product that starts with the current prefix.
   - We extract the suggested products by slicing the `products` array from `left` to `Math.min(left + 3, right + 1)`. This ensures that we get at most three suggested products.
   - We add the suggested products to the `result` array.

6. Finally, we return the `result` array containing the suggested products for each prefix of `searchWord`.

The time complexity of this solution is O(N log N + M), where N is the number of products and M is the length of `searchWord`. The sorting step takes O(N log N) time, and the loop iterates M times. In each iteration, the while loops take O(N) time in the worst case, but since we are moving the pointers `left` and `right`, the total time complexity is O(M + N).

The space complexity is O(N) to store the sorted `products` array and the `result` array.
