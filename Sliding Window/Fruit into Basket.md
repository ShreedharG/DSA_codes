https://leetcode.com/problems/fruit-into-baskets/

```
class Solution {
public:
    int totalFruit(vector<int>& fruits) {
        int n = fruits.size();
        int maxLen = 0;
  
        for(int i=0;i<n;i++){
	        set<int> s;
            for(int j=i;j<n;j++){
                s.insert(fruits[j]);
                if(s.size() > 2){
                    break;               
                maxLen = max(maxLen, j-i+1);                
            }
        }
        return maxLen;        
    }
};
```

###### Sliding Window Optimal
```
class Solution {
public:
    int totalFruit(vector<int>& fruits) {
        int n = fruits.size();
        map<int,int> myMap;
        int maxLen = 0;
        int left = 0;

        for(int right=0; right < n; right++){
            myMap[fruits[right]]++;

            if(myMap.size() > 2){
                myMap[fruits[left]]--;
                if(myMap[fruits[left]] == 0)
                    myMap.erase(fruits[left]);

                left++;
            }
            maxLen = max(maxLen, right-left+1);
        }
        return maxLen;        
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]

