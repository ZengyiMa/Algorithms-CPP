
# 调整数组顺序使奇数位于偶数前面

描述：题目:输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数位于数组的前半部分，所有偶数位予数组的后半部分。

思路：双指针，一个从左往右遍历找偶数，一个从右往左找奇数，2个指针找到对应的值之后，交互左右的值，即可。
思路：

```
class Solution {
public:
    void reOrderArray(vector<int> &array) {
        int left = 0;
        int right = array.size() - 1;
        
        while (left < right) {
            // 找偶数
            while (left < right && array[left] % 2 !=0)left++;
            // 找奇数
            while (left < right && array[right] % 2 == 0)right--;
            if (left < right) {
                int tmp = array[right];
                array[right] = array[left];
                array[left] = tmp;
            }
               
        }
    }
};
```

