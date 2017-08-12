# 第一个只出现一次的字符

描述:在一个字符串(1<=字符串长度<=10000，全部由字母组成)中找到第一个只出现一次的字符,并返回它的位置

思路: 先在hash表中统计各字母出现次数，第二次扫描直接访问hash表获得次数

```
class Solution {
public:
    int FirstNotRepeatingChar(string str) {
        unordered_map<char, int> map;
        if (str.length() == 0) return -1;
        for (int i = 0; i < str.length(); ++i) {
            if (map.find(str[i]) != map.end()) {
                map[str[i]] += 1; 
            } else {
                map[str[i]] = 1;
            }
        }
        for (int i = 0; i < str.length(); ++i) {
            if (map.find(str[i]) != map.end()) {
                if (map[str[i]] == 1) {
                    return i;
                }
            }
        }
        return 0;
    }
};
```