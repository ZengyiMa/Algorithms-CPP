# 扑克牌顺子

描述:大王小王可以为任何数，当0


思路:
* 判断数的间隔是否小于王的数量。小于返回true，大于返回false
* 有相等的牌则直接返回false

```
class Solution {
public:
    bool IsContinuous(vector<int> n) {
        if (n.size() == 0) return false; 
        sort(n.begin(), n.end());
        int zeroCount = 0;
        int space = 0;

        // 统计0 的个数
       	for (int i = 0; i < n.size() - 1; ++i) {
            if (n[i] == 0) {
                zeroCount ++;
            } else {
                if (n[i] == n[i + 1]) {
                    return false;
                } else {
                    int tmp = n[i + 1] - n[i];
                    if (tmp > 1) {
                        space += (tmp - 1);
                    }
                }
            }
        }
        
        if (zeroCount < space) {
            return false;
        }
        return true;
    }
};
```