https://leetcode.com/problems/trapping-rain-water/

```
class Solution {
public:
    int trap(vector<int>& height) {
        int n = height.size();  

        vector<int> leftMax(n,0);
        leftMax[0] = height[0];
        for(int i=1;i<n;i++)
            leftMax[i] = max(leftMax[i-1],height[i]);

        vector<int> rightMax(n,0);
        rightMax[n-1] = height[n-1];
        for(int i=n-2;i>=0;i--)
            rightMax[i] = max(rightMax[i+1],height[i]);
  
        int total = 0;
        for(int i=0;i<n;i++){
            if(height[i] < min(leftMax[i],rightMax[i]))
                total += (min(leftMax[i],rightMax[i]) - height[i]);
        }
        return total;        
    }
};
```

Return -> [[Stack and Queue]]