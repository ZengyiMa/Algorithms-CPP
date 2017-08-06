#快速排序

描述: 
快速排序

思路:
1. 先从数列中取出一个数作为基准数。
2. 分区过程，将比这个数大的数全放到它的右边，小于或等于它的数全放到它的左边。
3. 再对左右区间重复第二步，直到各区间只有一个数。

```
  void quickSort(vector<int> &a, int left, int right) {
        if (left < right) {
            int val = a[left];
            int l = left;
            int r = right;
            while (l < r) {
                while (l < r && a[r] > val) r--;
                if (l < r) a[l++] = a[r];
                while (l < r && a[l] < val) l++;
                if (l < r) a[r--] = a[l];
            }
                a[l] = val;
                quickSort(a, left, l - 1);
                quickSort(a, l + 1, right);
        }
    }
```