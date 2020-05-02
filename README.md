## 深入掌握算法

#### 面试题

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
- [头条&已知二叉树的路径1->2,1->3需要输出7=(1+2)+(1+3)]
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
    if (node != null) {
      leftNumber.push(node.value)
      total += node.value
      calculateLeft(node.left)
    }
  }
  function calculateRight(node) {
    if (node != null) {
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
- [头条&实现一个调度器，保证同时运行的任务最多有两个](https://juejin.im/post/5d37e392f265da1ba252a226#heading-6)
```js
//JS实现一个带并发限制的异步调度器Scheduler，保证同时运行的任务最多有两个。完善代码中Scheduler类，使得以下程序能正确输出
class Scheduler {
  add(promiseCreator) { ... }
  // ...
}

const timeout = (time) => new Promise(resolve => {
  setTimeout(resolve, time)
})

const scheduler = new Scheduler()
const addTask = (time, order) => {
  scheduler.add(() => timeout(time))
    .then(() => console.log(order))
}

addTask(1000, '1')
addTask(500, '2')
addTask(300, '3')
addTask(400, '4')
// output: 2 3 1 4

// 一开始，1、2两个任务进入队列
// 500ms时，2完成，输出2，任务3进队
// 800ms时，3完成，输出3，任务4进队
// 1000ms时，1完成，输出1
// 1200ms时，4完成，输出4
```
- [阿里&实现一个 normalize 函数，能将输入的特定的字符串转化为特定的结构化数据](https://editor.csdn.net/md/?articleId=105048837)
```
符串仅由小写字母和[,]组成，且字符串不会包含多余的空格。
示例一: 'abc' --> {value: 'abc'}
示例二：'[abc[bcd[def]]]' -> {value: 'abc', children: {value: 'bcd', children: {value: 'def'}}}
```

- [阿里&实现一个事件收发器 Event 类，继承自此类的对象拥有 on,off,once 和 trigger 方法]
```
// 例如
const event = new Event();
function log(val) {console.log(val);};
event.on('foo_event', log);
event.trigger('foo_event', 'abc'); // 打印出 abc
event.off('foo_event', log);
event.trigger('foo_event', 'abc'); // 打印出 undefined
```

- [阿里&实现一个 DOM 事件代理方法 delegate，接收一个 dom 元素，有两个方法，分别是添加 on 和 off]
```
// 例如
delegate(parentElement).on('.childClassname', 'click', callback);
delegate(parentElement).off('.childClassname', 'click', callback);
```
- [完美世界&实现求和函数]
```
f(1) = 1
f(1)(2) = 3
f(1)(2)(3) = 6
f(1)...(m) = 1+...+n
```
- [完美世界&实现 promise A+原理](https://github.com/wuxianqiang/blog/issues/92)
- [完美世界&如何水平垂直居中](https://github.com/wuxianqiang/blog/issues/272)
- [完美世界&flex的属性有哪些]
- [滴滴&谈谈对 Event Loop 理解]
- [滴滴&webpack原理]
- [头条&函数防抖节流]
- [头条&从浏览器输入网址到页面呈现的过程]
- [头条&性能优化]
- [头条&Vue和React的区别]
- [头条&设计模式]
- [美团&DOM diff]
- [知乎&实现 redux 原理](https://github.com/wuxianqiang/blog/issues/165)
