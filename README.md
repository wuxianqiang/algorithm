## 深入掌握算法

#### 算法

- [滴滴&合并两个有序数组](https://leetcode-cn.com/problems/merge-sorted-array/solution/tu-jie-he-bing-liang-ge-you-xu-shu-zu-by-user7746o/)

```js
function solution (num1, num2) {
  let m = num1.length;
  let n = num2.length;
  let p1 = m - 1;
  let p2 = n - 1;
  let p = m + n - 1;
  while (p1 >= 0 && p2 >= 0) {
    num1[p--] = (num1[p1] < num2[p2] ? num2[p2--] : num1[p1--])
  }
  return num1
}
```
- [滴滴&翻转二叉树](https://leetcode-cn.com/problems/invert-binary-tree/solution/fan-zhuan-er-cha-shu-by-leetcode/)
```js
function reverse(node) {
  if (node != null) {
    let temp = node.left;
    node.left = node.right;
    node.right = temp;
    reverse(node.left);
    reverse(node.right);
  }
}
```
- [头条&合并二叉树](https://leetcode-cn.com/problems/merge-two-binary-trees/solution/he-bing-er-cha-shu-by-leetcode/)
```js
function mergeTrees(t1, t2) {
  if (t1 == null)
    return t2;
  if (t2 == null)
    return t1;
  t1.value += t2.value;
  t1.left = mergeTrees(t1.left, t2.left);
  t1.right = mergeTrees(t1.right, t2.right);
  return t1;
}
```
