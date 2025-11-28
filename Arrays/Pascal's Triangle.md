https://leetcode.com/problems/pascals-triangle/?envType=problem-list-v2&envId=array

###### Generate Traingle
```
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> ans;
        ans.push_back({1});

        for(int i=1;i<numRows;i++){
            vector<int> prevRow = ans[i-1];
            vector<int> row(i+1,1);
            
            for(int j = 1; j < i; j++)
                row[j] = prevRow[j-1] + prevRow[j];

            ans.push_back(row);
        }
        return ans;
    }
};
```

###### Return Row of Give Row Index
```
class Solution {
public:
    vector<int> getRow(int rowIndex) {
        if(rowIndex == 0) return {1};
        
        vector<int> prevRow = {1};
        for(int i = 1; i <= rowIndex; i++){
            vector<int> row(i+1,1);
            for(int j = 1; j < i; j++)
                row[j] = prevRow[j-1] + prevRow[j];
  
            prevRow = row;
        }
        return prevRow;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

