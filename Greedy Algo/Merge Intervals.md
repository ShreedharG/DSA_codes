https://leetcode.com/problems/merge-intervals/description/

```
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        vector<vector<int>> ans;
        int n = intervals.size();
        sort(intervals.begin(),intervals.end());

        int start = intervals[0][0];
        int end = intervals[0][1];

        for(int i=1;i<n;i++){
            if(intervals[i][0] > end){
                ans.push_back({start,end});
                start = intervals[i][0];
                end = intervals[i][1];
            }
            else
                end = max(end,intervals[i][1]);
        }
        ans.push_back({start,end});
        return ans;
    }
};
```

Return -> [[Greedy Algorithms]]

