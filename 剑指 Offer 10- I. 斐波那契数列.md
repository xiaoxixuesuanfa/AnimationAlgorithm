>目前是在github，可能存在部分图片和动画无法演示的情况，如果加载出错，可以访问 微信公众号原文：为了第一时间接受小夕的原创动漫算法文，可以微信搜索：**小夕学算法** 另外加小夕微信 tiehanhan12342 拉你进算法刷题群，每日一道算法题，提高算法刷题能力！

###  题目
写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项。斐波那契数列的定义如下：
```
F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), 其中 N > 1
```
斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。
```
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof
```
### 面试现场
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwtw9zbpaj30i20b4tbf.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwtw9xjs4j30i20b40tq.jpg)

```Java
class Solution {
    public int fib(int n) {
        if(n == 0)
            return 0;
        if(n == 1)
            return 1;
        return fib(n - 1) + fib(n - 2);
    }
}
```
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwtw9xzc4j30i20b4tby.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwtwa08g4j30i20b40vf.jpg)
### 回到学校
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwu185iowj30i20b4gnz.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwu184b4rj30i20b476z.jpg)

![](https://upload-images.jianshu.io/upload_images/14850956-668ed2b9620a14ef.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwu184c7yj30i20b4tat.jpg)

比如计算fib(6)，从图片中可以看到，f(3)重复计算了3次，f(4)重复计算了2次，可想而知，越往上，那么重复计算的次数会越多。
![](https://upload-images.jianshu.io/upload_images/14850956-488e12299aa26f3a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 记忆法递归
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwu3rdykij30i20b4q5d.jpg)

```
class Solution {
    public int fib(int n) {
        int [] arr = new int[n + 1];
        for (int i = 0; i < arr.length;i++) {
            arr[i] = -1;
        }
        return fibWithArray(n, arr);
    }
    public int fibWithArray(int n,int [] arr) {
        if (n < 2) {
            return n;
        }
        if (arr[n] == -1) {
            arr[n] = (fibWithArray(n-1, arr) + fibWithArray(n-2, arr)) % 1000000007;
        }
        return  arr[n];
    }
}
```
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwu6ac4k3j30i20b476u.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwu6abq0oj30i20b476s.jpg)

小夕：之前我的递归因为存在重复计算的问题，所以我就新开了一个数组，并初始化这个数组都为-1，当这个数组中的值对应是-1呢，那么就执行`arr[n] = (fibWithArray(n-1, arr) + fibWithArray(n-2, arr)) % 1000000007;`，执行完以后arr[n]就不是-1了，那么下次因为不是-1.所以这个`if (arr[n] == -1) `判断条件就不满足，所以就直接返回了`arr[n]`，不会存在重复计算的问题！

举个例子，比如计算f(5) 从之前的图中可以看出来，为了计算f(5) 那么f(3)需要计算两次。

这里小夕我举个例子就一目了然了。**现在用了数组只需要一次**。

#### 记忆法递归例子

![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwslzuorkj30xw0ic3zp.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwslzucdgj30xw0icq46.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwslzu3v9j30xw0icjsa.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwslzuzkjj30xw0ic0ud.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwslzvvimj30xw0icmy3.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwslzuo5tj30xw0ic0to.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwsm00ik4j30xw0icdh6.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwslzyaxgj30xw0icq4a.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwslzyomej30xw0ictan.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwslzzupej30xw0icgmn.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwslzyydgj30xw0icwfj.jpg)

#### 递归动画
![斐波那契树之前的递归.gif](http://ww1.sinaimg.cn/large/007s8HJUly1gkwtnwp0k0g30xw0ic0yt.gif)


小夕：所以可以看到，因为有了数组，让计算f(5)的时候，f(4)f(3)f(2)只计算了一次，也就是说计算f(n)的时候，f(1)到f(n-1)只计算了一次，大大的减少了递归的时间。

![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwue49p9zj30i20b4tb8.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwue49wq2j30i20b4n0d.jpg)

### 动态规划解法
小管助教：小夕你的，"记忆化递归"的思考路径是"自顶向下"。而“动态规划”思考问题路径是"自下而上"。实际上，先“真正地”解决了数据规模较小的问题，然后一步一步地解决了数据规模较大的问题。

而斐波那契数列是通过"递归"定义的，通过这个递归关系式，我们可以知道斐波那契数列中任意一个位置的数值。

![](https://upload-images.jianshu.io/upload_images/14850956-b52f2dca85abeed7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
动态规划的关键是要找出来转移方程，什么是状态转移方程？你把 `f(n)` 想做一个状态 `n`，这个状态 `n` 是由状态 `n - 1` 和状态` n - 2` 相加转移而来，这就叫状态转移。

所以很容易从斐波那契数列中得到状态转移方程：`dp[i+1] = dp[i] + dp[i−1] ` 
状态转移方程的初始状态很容易知道是:`dp[0] = 1 dp[1] = 1`,我们要求的第n个斐波那契数列就是`dp[n]`
所以根据转移方程，可以得到如下代码：
```Java
class Solution {
    public int fib(int n) {
        if(n < 2)
            return n;
        int dp[] = new int[n + 1];
        dp[0] = 0;
        dp[1] = 1;
        for(int i=2;i<=n;i++){
            dp[i] = (dp[i-1] + dp[i-2]) % 1000000007;
        }
        return dp[n];
    }
}
```
### 动态规划优化
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwuhb5iszj30i20b4acb.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwujfieu8j30i20b40um.jpg)

小管助教：由于dp数组中我们需要的数只和 `dp[i] dp[i-1] dp[i-2]`有关，所以可以用sum,b,a来分别代表`dp[i] dp[i-1] dp[i-2]`。

- 比如为了计算 dp[3], 需要先计算`dp[2] = dp[1] + dp[0]`。 我们不使用数组，也就是`sum = b + a`。此时 `sum =1 b = 1 a= 0`
- 为了计算dp[3] 需要保留dp[2]也就是sum的计算结果。 
- 于是我们让`a = b = 1` 也就是让a 保留 dp[1]的结果 让`b = sum = 1`也就是让b保留dp[2]的结果
- 所以dp[3] = b + a = 2 

上几个图示例一下。![0.png](http://ww1.sinaimg.cn/large/007s8HJUly1gkwr1qh0wbj30mo0bvwel.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwr1qgdz7j30mo0bvjri.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwr1qgh2ej30mo0bvgls.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwr1qgenlj30mo0bv0sw.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwr1qhrlyj30mo0bv3yo.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwr1qhargj30mo0bvmxd.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwr1qjbhuj30mo0bvaa9.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwr1qjxk8j30mo0bvaa9.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwr1qjtjyj30mo0bvmxe.jpg)

### 动画演示一下

![斐波那契.gif](http://ww1.sinaimg.cn/large/007s8HJUly1gkwrmhp9jfg30mo0bv0tp.gif)

#### 复杂度

由于没使用数组，空间复杂度是O(1)，时间复杂度是O(n)

### Java解法

```Java
class Solution {
    public int fib(int n) {
        int a = 0;
        int b = 1;
        if(n == 0)
            return 0;
        if(n == 1)
            return 1;
        int i = 2;
        int sum=0;
        while(i <= n)
        {
            sum = (a + b) % 1000000007;
            a = b;
            b = sum;
            i++;
        }
        return sum;
    }
}
```
### C++解法

```C++
class Solution {
public:
    int fib(int n) {
        int a = 0;
        int b = 1;
        if(n == 0)
            return 0;
        if(n == 1)
            return 1;
        int i = 2;
        int sum=0;
        while(i <= n)
        {
            sum = (a + b) % 1000000007;
            a = b;
            b = sum;
            i++;
        }
        return sum;
    
    }
};
```

### JS解法

```JS
/**
 * @param {number} n
 * @return {number}
 */
var fib = function(n) {
    var a = 0;
    var b = 1;
    if(n == 0)
        return 0;
    if(n == 1)
        return 1;
    var i = 2;
    var sum=0;
    while(i <= n)
    {
        sum = (a + b) % 1000000007;
        a = b % 1000000007;
        b = sum;
        i++;
    }
    return sum;
};
```
### PY解法
```py
class Solution(object):
    def fib(self, n):
        a = 0;
        b = 1;
        if(n == 0):
            return 0;
        if(n == 1):
            return 1;
        i = 2;
        sum=0;
        while(i <= n):
            sum = (a + b) % 1000000007;
            a = b;
            b = sum;
            i += 1;
        return sum;

```

### PHP解法
```php
class Solution {

    /**
     * @param Integer $n
     * @return Integer
     */
    function fib($n) {
        $a = 0;
        $b = 1;
        if($n == 0)
            return 0;
        if($n == 1)
            return 1;
        $i = 2;
        $sum=0;
        while($i <= $n)
        {
            $sum = ($a + $b) % 1000000007;
            $a = $b;
            $b = $sum;
            $i++;
        }
        return $sum;
    }
}
```
### GO解法
```Go
func fib(N int) int {
    a := 0;
    b := 1;
    if N == 0 {
        return 0;
    }
    if N == 1 {
        return 1;
    }
    sum := 0;
    for i := 2; i <= N; i++ {
        sum = (a + b) % 1000000007;
        a = b;
        b = sum;
    }
    return sum;
}
```




### 最后

![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwum98epsj30i20b4jtn.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwum98do1j30i20b4mz0.jpg)

### 小夕最后有话说


- 动画、漫画、加6种编程语言（Java、C++、PHP、GO、Python、JS)的讲解很费心血，希望大家能帮忙转发到朋友圈和身边的朋友，**这样小夕的文章能让更多的人看见的话，小夕会更有动力更新文章的呀~**。
- 点击阅读原文，查看小夕的leetcode题解，记得点个赞。（**leetcode题解可以手动控制动画，更有助于你理解哦~**）
- 公众号后台回复 **打卡** 查看公众号福利 坚持转发文章到朋友圈，小夕送上100元的红包给你，谢谢铁杆粉丝的支持。
- 加小夕微信 tiehanhan12342 拉你进算法刷题群。

### 微信公众号

![](http://ww1.sinaimg.cn/large/007s8HJUly1gkwzt23ho7j309k09kdfs.jpg)

### 微信
![个人微信](http://ww1.sinaimg.cn/large/007s8HJUly1gkwzsl5bihj30m80godhf.jpg)






