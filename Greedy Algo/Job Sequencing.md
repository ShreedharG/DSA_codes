https://www.geeksforgeeks.org/problems/job-sequencing-problem-1587115620/1

```
class Solution {
  public:
    struct job{
        int id;
        int dead;
        int pro;
    };
    
    static bool compare(job a, job b){
        return (a.pro > b.pro);
    }
    
    vector<int> jobSequencing(vector<int> &deadline, vector<int> &profit){
        int n = profit.size();
        vector<job> jobs(n);
        int max_slots = INT_MIN;
        
        for(int i=0;i<n;i++){
            jobs[i].id = i+1;
            jobs[i].dead = deadline[i];
            jobs[i].pro = profit[i];
            max_slots = max(max_slots,deadline[i]);
        }        
        max_slots++; // for 1-based indexing
        
        sort(jobs.begin(), jobs.end(), compare);
        
        int max_profit = 0;
        int max_jobs = 0;
        vector<int> arr(max_slots, -1);
        
        for(int i=0;i<n;i++){
            for(int j=jobs[i].dead;j>0;j--){
                if(arr[j]==-1){
                    arr[j] = jobs[i].id;
                    max_jobs++;
                    max_profit+=jobs[i].pro;
                    break;
                }
            }
        }
        return {max_jobs,max_profit};
    }
};
```

Return -> [[Greedy Algorithms]]