# 左旋转字符串

描述:汇编语言中有一种移位指令叫做循环左移（ROL），现在有个简单的任务，就是用字符串模拟这个指令的运算结果。对于一个给定的字符序列S，请你把其循环左移K位后的序列输出。例如，字符序列S=”abcXYZdef”,要求输出循环左移3位后的结果，即“XYZdefabc”。 


思路:
“abcdef”旋转3位
前3位逆序，后3位逆序，整体再逆序。
“cbafed”-> “defabc”

```
class Solution {
public:
    string LeftRotateString(string str, int n) {
        
        if (str.length() < n) return str;
        
        reverseStr(str, 0, n - 1);
        reverseStr(str, n, str.length() - 1);
		reverseStr(str, 0, str.length() - 1);
        return str;
    }
    void reverseStr(string &str, int s, int e) {
        while (s <= e) {
            char temp = str[s];
            str[s++] = str[e];
            str[e--] = temp;
        }
    }
};
```