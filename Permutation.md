# 字符串的排列

描述:输入一个字符串,按字典序打印出该字符串中字符的所有排列。例如输入字符串abc,则打印出由字符a,b,c所能排列出来的所有字符串abc,acb,bac,bca,cab和cba。 

思路:
* 固定第一个字符，递归取得首位后面的各种字符串组合；
* 再把第一个字符与后面每一个字符交换，并同样递归获得首位后面的字符串组合 

```
class Solution {
public:
    vector<string> Permutation(string str) {
        vector<string> result;
        if (str.size() == 0) return result;
        Permutation(&str, 0, &result);
        sort(result.begin(), result.end());
        return result;
    }
    
    void Permutation(string *str, int s, vector<string> *r) {
        if (s == str->size()) {
            r->push_back(string(*str));
            return;
        } else {
            for (int i = s; i < str->size(); ++i) {
                if (i != s && (*str)[i] == (*str)[s]) {
                    continue;
                }
                char temp = (*str)[i];
                (*str)[i] = (*str)[s];
                (*str)[s] = temp;
                Permutation(str, s + 1, r);
                 temp = (*str)[i];
                (*str)[i] = (*str)[s];
                (*str)[s] = temp;
            }
        }
    }  
};
```