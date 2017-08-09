# 最小的K个数

描述:输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。

思路:
使用数组 k 个大小的容量，将每次小于集合里面的值替换掉集合里面的最大值。最终就是最小的 K 个数。


```
class Solution {
public:
    vector<int> GetLeastNumbers(vector<int> input, int k) {
        vector<int> result;
        if (k > input.size()) return result;
        for (int i = 0; i < input.size(); ++i) {
            if (result.size() < k) {
                result.push_back(input[i]);
                if (result.size() == k) {
                    sort(result.begin(), result.end());
                }
            } else {
                for (int n = k - 1; n >= 0; --n) {
                    if (input[i] < result[n]) {
                        result[n] = input[i];
                        break;
                    }
                }
            }
        }
        return result;
    }
};
```