https://leetcode.com/problems/lemonade-change/

```
class Solution {
public:
    bool lemonadeChange(vector<int>& bills) {
        int num_five = 0;
        int num_ten = 0;
        int n = bills.size();  

        for(int i=0;i<n;i++){
            if(bills[i]==5)
                num_five++;
            else if(bills[i]==10){
                num_ten++;
                if(num_five>=1)
                    num_five--;
                else
                    return false;
            }
            else if(bills[i]==20){
                if(num_ten && num_five){
                    num_five--;
                    num_ten--;
                }
                else if(num_five >= 3)
                    num_five -= 3;
                else
                    return false;
            }
        }
        return true;        
    }
};
```

Return -> [[Greedy Algorithms]]

