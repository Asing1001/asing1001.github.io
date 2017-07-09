---
title: LeetCode - Average of Levels in Binary Tree
date: 2017-07-09 11:19:09
tags: [LeetCode, Algorithm, Binary tree]
---

一時興起參加了 LeetCode 的 [Weekly Contest #40](https://leetcode.com/contest/leetcode-weekly-contest-40/)，用Javascript只解出了第一題[計算二元樹每層平均值](https://leetcode.com/contest/leetcode-weekly-contest-40/problems/average-of-levels-in-binary-tree/)，思維是用兩個陣列，一個存每層的平均，一個存每層的總數量，最後相除得到每層的平均，實作如下：

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */

var averageOfLevels = function(root) {
    var sumArr = [];
    var countArr = [];
    var sum = function(node, level) {
        if (!node) return
        if (!sumArr[level]) sumArr[level] = 0;
        sumArr[level] += node.val;
        if (!countArr[level]) countArr[level] = 0;
        countArr[level]++;
        sum(node.left, level + 1);
        sum(node.right, level + 1);
    }

    sum(root, 0);
    var meanArr = sumArr.map((sum, level) => sum / levelCountArr[level]);
    return meanArr;
};
```
