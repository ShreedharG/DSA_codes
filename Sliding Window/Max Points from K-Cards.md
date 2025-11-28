https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/

```
class Solution {
public:
    int maxScore(vector<int>& cardPoints, int k) {
        int n = cardPoints.size();
        int totalSum = 0;
        for(auto nums : cardPoints)
            totalSum += nums;
        if(n==k) return totalSum;
  
        int win_size = n-k;
        int left = 0, right = 0;
        int sum = 0;
        int minSum;
  
        for(int i=0;i<win_size;i++) sum += cardPoints[i];
        minSum = sum;

        for(int i=win_size;i<n;i++){
            sum += cardPoints[i]-cardPoints[i-win_size];
            minSum = min(minSum,sum);
        }
  
        return (totalSum - minSum);
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]
