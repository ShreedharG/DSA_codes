https://www.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1

```
class Solution {
  public:
    struct item{
        int value;
        int weight;
        double val_per_weight;
    };
    
    static bool compare(item a, item b){
        return (a.val_per_weight > b.val_per_weight);
    }
    
    double fractionalKnapsack(vector<int>& val,vector<int>& wt,int capacity){
        int n = val.size();
        vector<item> list(n);
        
        for(int i=0;i<n;i++){
            list[i].value = val[i];
            list[i].weight = wt[i];
            list[i].val_per_weight = ((double)val[i]/wt[i]);
        }
        
        sort(list.begin(),list.end(),compare);
        
        double ans = 0;
        for(int i=0;i<n;i++){
            if(list[i].weight <= capacity){
                ans+=(list[i].value);
                capacity-=(list[i].weight);
            }
            else{
                ans+=(list[i].val_per_weight*capacity);
                break;
            }
        }
        return ans;
    }
};
```

Return -> [[Greedy Algorithms]]

