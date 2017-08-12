# 第一个只出现一次的字符

描述:在一个字符串(1<=字符串长度<=10000，全部由字母组成)中找到第一个只出现一次的字符,并返回它的位置

思路: 

* 先将整型数组转换成String数组，然后将String数组排序，最后将排好序的字符串数组拼接出来。关键就是制定排序规则。
* 排序规则如下：
* 若ab > ba 则 a > b，
* 若ab < ba 则 a < b，
* 若ab = ba 则 a = b；
* 解释说明：
* 比如 "3" < "31"但是 "331" > "313"，所以要将二者拼接起来进行比较
    
***使用的库函数：to_string（数字转换成字符串），sort（排序函数）***

```
class Solution {
public:
    static bool cmp(int a, int b) {
        string s1 = "";
        string s2 = "";
        s1 += to_string(a);
        s1 += to_string(b);
        s2 += to_string(b);
        s2 += to_string(a);
        return s1 < s2;
    }
    string PrintMinNumber(vector<int> numbers) {
        
        sort(numbers.begin(), numbers.end(), cmp);
        
        string ret = "";
        for (int i = 0; i < numbers.size(); ++i) {
            ret += to_string(numbers[i]);
        }
        return ret;
    }
};
```