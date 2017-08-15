# 求1+2+3+...+n

描述:求1+2+3+...+n，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。


思路:使用递归来求值，判断用逻辑与来离开递归

```
class Solution {
public:
    int Sum(int n) {
        int sum = n;
        n && (sum += Sum_Solution(n - 1));
        return sum;
    }
};
```