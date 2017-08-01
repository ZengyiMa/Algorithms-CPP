# 顺时针打印矩阵

描述：输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字，例如，如果输入如下矩阵： 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 则依次打印出数字1,2,3,4,8,12,16,15,14,13,9,5,6,7,11,10.。

思路：首先，一圈分为上下左右分别打印，其次，每个内圈都是往前的大小减二，依次输出内圈的矩阵，注意一下不要重复打印和边界的问题


```
class Solution {
public:
    vector<int> printMatrix(vector<vector<int> > matrix) {
         vector<int> result;
        // 列
        int col = matrix[0].size();
        // 行
        int row = matrix.size();
        int start = 0; // 左上角
        for (; col > 0 && row > 0; ++start) {
           int rightBotton = start + row - 1;
           int rightTop = start + col - 1;

            // 上边
            for (int i = start; i <= rightTop; ++i) {
                result.push_back(matrix[start][i]);
            }
            // 右边
            for (int i = start + 1; i <= rightBotton; ++i) {
                result.push_back(matrix[i][rightTop]);
            }
            // 下边
            if (rightBotton != start) {
                for (int i = rightTop - 1; i >= start; --i) {
                result.push_back(matrix[rightBotton][i]);
            	}
            }
            
			
            // 左边
            if (rightTop != start) {
                for (int i = rightBotton - 1; i > start; --i) {
                result.push_back(matrix[i][start]);
            	}
            }
            
            col -= 2;
            row -= 2;
        }
        return result;
    }
};
```