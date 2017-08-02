# 栈的压入、弹出序列

描述：输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如序列1,2,3,4,5是某栈的压入顺序，序列4，5,3,2,1是该压栈序列对应的一个弹出序列，但4,3,5,1,2就不可能是该压栈序列的弹出序列。（注意：这两个序列的长度是相等的）。

思路： 判断序列 B 是不是序列 A 的弹出顺序，有2个条件：
    1. 栈顶是不是序列 B 的弹出顺序。
    2. 如果不是，那么可以一直入栈序列 B 弹出的数字在序列 A 的位置之前的元素。 
如果没找到，那么就可以证明序列 B 不是序列 A 的弹出顺序。

```
class Solution {
public:
    bool IsPopOrder(vector<int> pushV,vector<int> popV) {
       if (popV.empty() || pushV.empty()) return false;
        stack<int> stack;
       // 首先栈顶是不是出栈的元素，如果是那么直接出栈，如果不是，就一直入栈
       int p = 0;
        for (int i = 0; i < popV.size(); ++i) {
            if (!stack.empty() && stack.top() == popV[i]) stack.pop();
            else {
                bool isFind = false;
               for (; p < pushV.size(); ++p) {
                   if (pushV[p] != popV[i]) {
                       stack.push(pushV[p]);
                   } else {
                       ++p;
                        isFind = true;
                        break;
                   }
               }
               if (!isFind) {
                   return false;
               }
            }
        }
        return true;
    }
};
```