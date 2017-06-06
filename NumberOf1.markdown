
# 二进制中1的个数

描述：输入一个整数，输出该数二进制表示中1的个数。其中负数用补码表示。

思路：可以用 1 来不断做左移操作来不断检测当前位数是不是1，如果是 1 就将数字加 1

```
class Solution {
public:
     int  NumberOf1(int n) {
         int count = 0;
         int flag = 1;
         while (flag) {
             if (flag & n) {
                 count++;
             }
             flag = flag << 1;
         }
         return count;
     }
};
```

