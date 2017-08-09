# 第 n 大的丑数

描述: 设计一个算法，找出只含素因子2，3，5 的第 n 大的数。
符合条件的数如：1, 2, 3, 4, 5, 6, 8, 9, 10, 12...

思路: 我们可以创建一个数组，里面的数字是排好序的丑数，每一个丑数都是前面的丑数乘以2、3或者5得到的。



```
class Solution {
public:
    /*
     * @param n an integer
     * @return the nth prime number as description.
     */
    int nthUglyNumber(int n) {
        // write your code here
        vector<int> ret(n);
        ret[0] = 1;
        int t2 = 0, t3 = 0, t5 = 0;
        for (int i = 1; i < n; ++i) {
            ret[i] = min(ret[t2] * 2, min(ret[t3] * 3, ret[t5] * 5));
            if (ret[i] == ret[t2] * 2) t2++;
            if (ret[i] == ret[t3] * 3) t3++;
            if (ret[i] == ret[t5] * 5) t5++;
        }
        return ret[n - 1];
    }
};
```

lintcode: http://www.lintcode.com/zh-cn/problem/ugly-number-ii/