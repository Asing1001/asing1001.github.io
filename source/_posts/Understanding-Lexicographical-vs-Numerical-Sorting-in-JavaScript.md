---
title: Lexicographical vs Numerical Sorting in JavaScript Array.prototype.sort()
date: 2024-05-25 14:30:00
tags: [JavaScript, Sorting, Arrays, Programming]
---

### Default behavior - Lexicographical Sorting

**By default, the `sort()` method sorts the elements of an array as strings.** This means the elements are compared based on their Unicode code point values, leading to lexicographical order, which is not always the intended numerical order. **This default behavior can cause bugs when sorting numbers.**

#### Example:

```javascript
const nums = [-1, -2, -3, -4, 0, 1, 2, 3, 4];
nums.sort();
console.log(nums); // Output: [-1, -2, -3, -4, 0, 1, 2, 3, 4]
```

In this example, the `sort()` method treats the numbers as strings and sorts them based on the Unicode values, resulting in an order that looks correct but isn't numerically accurate. This can lead to unexpected behavior and bugs in your code.

### Numerical Sorting

To sort the numbers correctly in ascending order, you need to provide a comparison function to the `sort()` method. The comparison function should subtract one number from the other, ensuring numerical comparison.

#### Example:

```javascript
const nums = [-1, -2, -3, -4, 0, 1, 2, 3, 4];
nums.sort((a, b) => a - b);
console.log(nums); // Output: [-4, -3, -2, -1, 0, 1, 2, 3, 4]
```

In this corrected example, the comparison function `(a, b) => a - b` ensures that the array is sorted numerically in ascending order.

### Conclusion

When sorting numbers in JavaScript, always use a comparison function with the `sort()` method to ensure the elements are sorted numerically. This small adjustment prevents unexpected results and ensures your array is in the correct order, avoiding potential bugs caused by default lexicographical sorting.
