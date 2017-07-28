
# 数值的整数次方

描述：给定一个double类型的浮点数base和int类型的整数exponent。求base的exponent次方。

思路：

```
class Solution {
public:
    double Power(double base, int exponent) {
    
        bool flag = false;
        if (exponent < 0) {
             flag = true;
            exponent *= -1;
        }
        
        if (exponent == 0) return 1;
        if (exponent == 1) return base;
        
        double result = Power(base, exponent >> 1 );
        result *= result;
        if (exponent & 1) {
            result *= base;
        }
        
        if (flag) {
           result = 1 / result;
        }
        
        return result;
    }
};
```

