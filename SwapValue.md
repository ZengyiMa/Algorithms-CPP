# 不使用额外的变量来交换2个数

描述:不使用额外的变量来交换2个数


思路:
使用加减法也可以交换

```
class Solution {
public:
    void SwapNumber(int a, int b)
    {
		int a = a + b;
        int b = a - b;
        int a = a - b;
    }
};
```