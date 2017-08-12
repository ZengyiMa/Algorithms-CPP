# 数组中的逆序对

描述:在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。

思路: 先把数组分割成子数组，先统计出子数组内部的逆序对的数目，然后再统计出两个相邻子数组之间的逆序对的数目。在统计逆序对的过程中，还需要对数组进行排序。如果对排序算法很熟悉，我们不难发现这个过程实际上就是归并排序

```
class Solution {
public:
    int InversePairs(vector<int> data) {
        return mergeSort(data, 0, data.size()-1);
    }
    
    int mergeSort(vector<int>& a, int s, int e) {
        if (s >= e) return 0;
        int mid = (s + e) / 2;
        int count = 0;
        // 排左边
        count += mergeSort(a, s, mid) ;
        // 排右边
        count += mergeSort(a, mid + 1, e);
        
        vector<int> tmp;
        int i = s, j = mid + 1;
        while (i <= mid && j <= e) {
            if (a[i] <= a[j]) {
                tmp.push_back(a[i]);
                i++;
            } else if (a[i] > a[j]){
                count += mid - i + 1;
                 tmp.push_back(a[j]);
                j++;
            }
        }
        
        while (i <= mid) {
            tmp.push_back(a[i++]);
        }
        
        while (j <= e) {
            tmp.push_back(a[j++]);
        }
        
        for (i = 0; i < tmp.size(); ++i) {
            a[s + i] = tmp[i];
        }
        return count;
    }
};
```