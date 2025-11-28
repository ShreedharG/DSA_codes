https://leetcode.com/problems/non-overlapping-intervals/description/

```
class Solution {
public:
    struct inter_val{
        int start_t;
        int end_t;
    };

    static bool comp_f(inter_val a, inter_val b){
        return (a.end_t < b.end_t);
    }

    int eraseOverlapIntervals(vector<vector<int>>& intervals) {
        int n = intervals.size();
        vector<inter_val> sorted_intervals(n);

        for(int i=0;i<n;i++){
            sorted_intervals[i].start_t = intervals[i][0];
            sorted_intervals[i].end_t = intervals[i][1];
        }

        sort(sorted_intervals.begin(),sorted_intervals.end(),comp_f);

        int end_time = sorted_intervals[0].end_t;
        int possibles = 1;
        for(int i=1;i<n;i++){
            if(sorted_intervals[i].start_t >= end_time){
                possibles++;
                end_time = sorted_intervals[i].end_t;
            }
        }

        return (n-possibles);
    }
};
```

Return -> [[Greedy Algorithms]]
