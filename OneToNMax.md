
# 打印从1到最大的n位数

描述：输入整数n，打印从1到最大的n位数，比如n为4，输出1，2，3一直到最大的4位数，即9999。

思路：
n值可能较大，所以此题为大数问题。大数问题一般可通过字符串或者数组来模拟解决。使用整数数组通过递归实现，即打印i位表示的整数，假设i-1表示的整数可列举，则只需将第i位从0到9遍历，同时与i-1位
表示的整数序列组合即可。复杂度为O(10^n)。

```

void printNumber(char *s)
{
    printf("\n%s", s);
}


void printOneToNRecursive(int pos, char *s)
{
    int length = strlen(s);
    if (pos >= length) {
        printNumber(s);
        return;
    }
    for (int i =  0; i < 10; ++i) {
        s[pos] = '0' + i;
        printOneToNRecursive(pos + 1, s);
    }
}

void printOneToN(int n)
{
   char *s = new char[n + 1];
    memset(s, '0', n + 1);
    s[n] = '\0';
    printOneToNRecursive(0, s);
    delete []s;
}
```

