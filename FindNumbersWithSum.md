# 和为S的两个数字

描述:输入一个递增排序的数组和一个数字S，在数组中查找两个数，是的他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。 


思路:
第一个指针指第一位，第二个指针指最后一位，若所指的两数和大于sum，第二个指针前移
否则，第一个指针后移，直到和为sum则停止循环并输出即可！

```
class Solution {
public:
    vector<int> FindNumbersWithSum(vector<int> array,int sum) {
        
        vector<int> ret;
        if (array.size() == 0) return ret;
        int s = 0, e = array.size() - 1;
        while (s <= e) {
            int val = array[s] + array[e];
            if (val == sum) {
                ret.push_back(array[s]);
                ret.push_back(array[e]);
                break;
            } else if (val > sum) {
                e -= 1;
			} else if (val < sum) {
                s += 1;
            }
        }
        return ret;
    }
};
```