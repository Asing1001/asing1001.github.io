---
title: 'Beware of the Array(n).fill({}) Pitfall in JavaScript'
date: 2024-02-25 18:05:10
tags: [Arrays, JavaScript, bug]
---

When working with arrays in JavaScript, it's essential to be mindful of how you initialize them, as certain methods can lead to unexpected behavior. One such pitfall involves inadvertently using `Array(n).fill({})` to create an array of objects.

Consider the following code snippet:

```javascript
const n = 5;
const memo = Array(n).fill({});

// Later in the code...
memo[0].value = 10;

console.log(memo);
// [{"value":10},{"value":10},{"value":10},{"value":10},{"value":10}]
```

At first glance, it might seem like `memo` is an array of five separate empty objects. However, this is not the case. The `fill()` method populates the array with references to the same object, so modifying one element affects all others.

In the example above, when we assign a `value` property to `memo[0]`, it inadvertently modifies all objects within the array. This behavior can be particularly problematic in scenarios where each array element should be independent.

To avoid this issue, consider using `Array.from()` or a loop to initialize arrays with unique objects:

```javascript
// Using Array.from()
const memo = Array.from({ length: n }, () => ({}));

// Using a loop
const memo = [];
for (let i = 0; i < n; i++) {
  memo.push({});
}
```

By being aware of this common mistake and choosing appropriate initialization methods, you can prevent unexpected bugs and ensure the integrity of your JavaScript code.
