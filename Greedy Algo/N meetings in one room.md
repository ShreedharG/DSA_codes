https://www.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/1

```
class Solution {
  public:
    struct meet{
        int start;
        int end;
    };
    
    static bool compare(meet a, meet b){
        return a.end < b.end;
    }
    
    int maxMeetings(vector<int>& start, vector<int>& end){
        int n = start.size();
        vector<meet> meetings(n);
        for(int i=0;i<n;i++){
            meetings[i].start = start[i];
            meetings[i].end = end[i];
        }
        
        sort(meetings.begin(),meetings.end(),compare);
        
        int num_meet = 1;
        int free_time = meetings[0].end;
        for(int i=1;i<n;i++){
            if(free_time < meetings[i].start){
                num_meet++;
                free_time = meetings[i].end;
            }
        }
        return num_meet;
    }
};
```

Return -> [[Greedy Algorithms]]

