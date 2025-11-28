https://www.geeksforgeeks.org/problems/-minimum-number-of-coins4426/1

```
class Solution {
  public:
    vector<int> minPartition(int N){
        vector<int> coins = {2000,500,200,100,50,20,10,5,2,1};
        vector<int> required;
        
        for(int coin:coins){
            if(N>=coin){
                int count = N/coin;
                required.insert(required.end(),count,coin);
                N%=coin;
            }
            if(N==0)
                return required;
        }
    }
};
```

Return -> [[Greedy Algorithms]]

