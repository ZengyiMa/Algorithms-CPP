# 数字在排序数组中出现的次数

描述:统计一个数字在排序数组中出现的次数

思路: 二分查找 找到第一个K 和 最后一个K 二者位置相减

```
class Solution {
public:
    int GetNumberOfK(vector<int> data ,int k) {
        int s = getKIndex(data, k, true);
        int e = getKIndex(data, k, false);
        if (s == -1) 
            return 0;
        return e - s + 1;
    }

    int getKIndex(vector<int> &d, int k, bool first) {
        int s = 0, e = d.size() - 1;
        while (s <= e) {
            int mid = (s + e) / 2;
            if (d[mid] == k) {
                if (first) {
                    if (mid != s && d[mid - 1] == k) {
                        // 左边
                        e = mid - 1;
                    } else {
                        return mid;
                    }
                } else {
                    if (mid != e && d[mid + 1] == k) {
                        // 右边
                        s = mid + 1;
                    } else {
                        return mid;
                    }
                }
            } else if (d[mid] < k){
                s = mid + 1;
            } else if (d[mid] > k){
                e = mid - 1; 
            }
        }
        return  -1 ;
    }
};
```