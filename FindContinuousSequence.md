# 和为S的连续正数序列

描述:输出所有和为S的连续正数序列。序列内按照从小至大的顺序，序列间按照开始数字从小到大的顺序


思路:
* 初始化small=1，big=2;
* small到big序列和小于sum，big++;大于sum，small++;
* 当small增加到(1+sum)/2是停止

```
class Solution {
public:
    vector<vector<int> > FindContinuousSequence(int sum) {
        vector<vector<int>> ret;
        
        int s = 1;
        int e = 2;
        int mid = (1 + sum) / 2;
        while (s < e && e <= mid) {
            int total = 0;
            for (int i = s; i <= e; ++i) {
                total += i;
            }
            if (total == sum) {
                vector<int> seq;
                for (int i = s; i <= e; ++i) {
                    seq.push_back(i);
                }
                ret.push_back(seq);
                s++;
            } else if (total > sum) {
                // 当前数列大，那么 开始位置减少一点
                s++;
            } else if (total < sum) {
                // 太小了提高上限
               	e++;
            }
        }
        return ret;
        
        
        
    }
};
```