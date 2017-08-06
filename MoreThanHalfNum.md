# 数组中出现次数超过一半的数字

描述:数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。例如输入一个长度为9的数组{1,2,3,2,2,2,5,4,2}。由于数字2在数组中出现了5次，超过数组长度的一半，因此输出2。如果不存在则输出0。 

思路:
数组排序后，如果符合条件的数存在，则一定是数组中间那个数，判断中间那个数在数组中的数量即可

```
class Solution {
public:
    int MoreThanHalfNum_Solution(vector<int> n) {
    	if (n.size() == 0) return 0;
        quickSort(n, 0, n.size() - 1);
        int mid = n[n.size() / 2];
        int count = 0;
        for (int i = 0; i < n.size(); ++i) {
            if(mid == n[i]) count++;
        }
        return count > (n.size() / 2) ? mid : 0;
    }
    
    void quickSort(vector<int> &v, int left, int right) {
        if (left < right) {
            int l = left, r = right;
            int p = v[l];
            while (l < r) {
                while(l < r && v[r] > p) r--;
                if (l < r) v[l++] = v[r];
                while (l < r && v[l] < p) l++;
                if (l < r) v[r--] = v[l];
            }
                v[l] = p;
                quickSort(v, left, l - 1);
                quickSort(v, l + 1, right);
        }
    }
    
    
    
};
```