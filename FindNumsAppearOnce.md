# 数组中只出现一次的数字

描述:一个整型数组里除了两个数字之外，其他的数字都出现了两次。请写程序找出这两个只出现一次的数字。

思路: 亦或的会把相同的数字变为0，则剩下的是只出现一次的。通过判断 1 的位置，我们可以得到这2个数

```
class Solution {
public:
    void FindNumsAppearOnce(vector<int> data,int* num1,int *num2) {
        *num1 = 0;
        *num2 = 0;
        if (data.size() == 0) return;

        int eor = 0;
        for (int i = 0; i < data.size(); ++i) {
            eor ^= data[i];
        }

        int bitIndex = bit1Index(eor);

        for (int i = 0; i < data.size(); ++i) {
            if (isBit1(data[i], bitIndex)) {
                *num1 ^= data[i];
            } else {
                *num2 ^= data[i];
            }
        }
    }

    int bit1Index(int num) {
        int index = 0;
        // 判断结束条件，因为负数右移会补 1
        while ((num & 1) == 0 && index < sizeof(int) * 8) {
            num = num >> 1;
            index++;
        }
        return index;
    }

    bool isBit1(int num, int index) {
        if (num >> index & 1) {
            return true;
        } else {
            return false;
        }
    }

};
```