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
- [头条&求二叉树所有根接单到叶子路径组成的数字之和]
```js
// 先序遍历
function getPathSum(root) {
  let total = 0
  function next(node) {
    if (node != null) {
      total += node.value
      next(node.left)
      node(node.right)
    }
  }
  next(node)
  return total
}
```
- [头条&1->2,1->3输出7=(1+2)+(1+3)]
```js
class TreeNode {
  constructor () {
    this.value = undefined;
    this.left = null;
    this.right = null;
  }
}

const node = new TreeNode()
node.value = 1;
node.left = new TreeNode()
node.left.value = 2
node.right = new TreeNode();
node.right.value = 3


function getPathSum(node) {
  let leftNumber = []
  let rightNumber = []
  let total = 0
  function calculateLeft(node) {
    if (node != undefined) {
      leftNumber.push(node.value)
      total += node.value
      calculateLeft(node.left)
    }
  }
  function calculateRight(node) {
    if (node != undefined) {
      rightNumber.push(node.value)
      total += node.value
      calculateRight(node.right)
    }
  }
  calculateLeft(node)
  calculateRight(node)
  let result = `${total}=(${leftNumber.join('+')})+(${rightNumber.join('+')})`
  return result
}

getPathSum(node) // return 7=(1+2) + (1+3)
```

- [头条&比较版本号](https://leetcode-cn.com/problems/compare-version-numbers/solution/bi-jiao-ban-ben-hao-by-leetcode/)

```js
function compareVersion(version1, version2) {
  let nums1 = version1.split('.')
  let nums2 = version2.split('.')
  let n1 = nums1.length
  let n2 = nums2.length
  let max = Math.max(n1, n2)
  for (let i = 0; i < max; i++) {
    let i1 = i < n1 ? nums1[i] : 0
    let i2 = i < n2 ? nums2[i] : 0
    if (i1 != i2) {
      return i1 > i2 ? 1 : -1
    }
  }
  return 0
}
```