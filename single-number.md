Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

Here's a JavaScript solution to find the single element that appears only once in the array:

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    let result = 0;
    for (let i = 0; i < nums.length; i++) {
        result ^= nums[i];
    }
    return result;
};
```

Explanation:
- We initialize a variable `result` to store the XOR of all the elements in the array.
- We iterate through each element in the array using a `for` loop.
- For each element, we perform the XOR operation between `result` and the current element using the `^` operator.
- After the loop ends, `result` will contain the single element that appears only once in the array.

The XOR operation has the following properties:
- XOR of a number with itself is 0.
- XOR of a number with 0 is the number itself.

By XORing all the elements in the array, the duplicate elements will cancel each other out because XORing the same number twice results in 0. The single element that appears only once will be left as the result.

This solution has a linear runtime complexity of O(n) since it iterates through the array once. It also uses only constant extra space of O(1) because it uses a single variable to store the result.
