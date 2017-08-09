# 判断是否是丑数

描述: 丑数的定义是，只包含质因子 2, 3, 5 的正整数。比如 6, 8 就是丑数，但是 14 不是丑数以为他包含了质因子 7。

思路: m 是 n 的质因子，那么 n 可以被 m 整除，丑数只包含 2, 3, 5 质因子，那么，丑数可以被 2, 3, 5 整除，如果一个数可以被 2 整除，我们连续除以2，被 3 整除，连续除以 3，被5 整除，连续除以 5，最后为 1 那么这个数就是丑数。



```
class Solution {
public:
    /**
     * @param num an integer
     * @return true if num is an ugly number or false
     */
    bool isUgly(int num) {
        // Write your code here
        if (num == 0) return false;
    	while (num % 2 == 0) 
    	    num /= 2;
    	while (num % 3 == 0) 
    	    num /= 3;
    	while (num % 5 == 0) 
    	    num /= 5;
    	return (num == 1) ? true : false; 
    }
};
```

lintcode: http://www.lintcode.com/zh-cn/problem/ugly-number/