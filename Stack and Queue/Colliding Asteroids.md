https://leetcode.com/problems/asteroid-collision/

```
class Solution {
public:
    vector<int> asteroidCollision(vector<int>& asteroids) {
        int n = asteroids.size();
        vector<int> ans;

        for(int i=0;i<n;i++){
            if(asteroids[i]>0)
                ans.push_back(asteroids[i]);
            else{
                while(ans.size()>0 && ans.back()>0 && ans.back()<abs(asteroids[i]))
                    ans.pop_back();
                if(ans.size()>0 && ans.back()>0 && ans.back()==abs(asteroids[i]))
                    ans.pop_back();
                else if(ans.size()==0 || ans.back()<0)
                    ans.push_back(asteroids[i]);
            }
        }
        return ans;
    }
};
```

Return -> [[Stack and Queue]]