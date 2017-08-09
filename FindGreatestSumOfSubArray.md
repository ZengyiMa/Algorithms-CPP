# 连续子数组的最大和

描述:输入 {6,-3,-2,7,-15,1,2,2},连续子向量的最大和为8(从第0个开始,到第3个为止)。

思路: 对于一个数A，若是A的左边累计数非负，那么加上A能使得值不小于A，认为累计值对
    整体和是有贡献的。如果前几项累计值负数，则认为有害于总和，需要抛弃然后从 A 开始计数，记录这个过程的最大值。
    
***注意：一开始需要用极小值， 0x80000000***


```
class Solution {
public:
    int FindGreatestSumOfSubArray(vector<int> a) {
        int max = 0x80000000;
        int temp = 0;
    	for (int i = 0; i < a.size(); ++i) {
            if (temp <= 0) {
                temp = a[i];
            } 
            else {
                temp += a[i];
            }
            if (max < temp) max = temp;
        }
        return max;
    }
};
```