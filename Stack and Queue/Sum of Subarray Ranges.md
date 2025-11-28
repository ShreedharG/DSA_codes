https://leetcode.com/problems/sum-of-subarray-ranges/
###### Brute-force Solution {O(n^2) time complexity}
```
class Solution {
public:
    long long subArrayRanges(vector<int>& nums) {
        int n = nums.size();
        long long total = 0;  

        for(int i=0;i<n;i++){
            int mini = INT_MAX;
            int maxi = INT_MIN;
            for(int j=i;j<n;j++){
                mini = min(mini,nums[j]);
                maxi = max(maxi,nums[j]);
  
                total += 1LL*(maxi-mini);
            }
        }
        return total;
    }
};
```
###### Optimal Solution(By Monotonic Stack)
```
class Solution {
public:
    long long subArrayRanges(vector<int>& nums) {
        int n = nums.size();
        stack<int> myStack;  

        // For finding min_subarrays on right
        vector<int> nse_id(n);
        for(int i=n-1;i>=0;i--){
            while(!myStack.empty() && nums[myStack.top()] >= nums[i])
                myStack.pop();
            nse_id[i] = myStack.empty() ? n : myStack.top();
            myStack.push(i);
        }
  
        while(!myStack.empty()) myStack.pop();

		// For finding min_subarrays on left
        vector<int> pse_id(n);
        for(int i=0;i<n;i++){
            while(!myStack.empty() && nums[myStack.top()] > nums[i])
                myStack.pop();
            pse_id[i] = myStack.empty() ? -1 : myStack.top();
            myStack.push(i);
        }
        
        while(!myStack.empty()) myStack.pop();
        
		// For finding max_subarrays on right
        vector<int> nge_id(n);
        for(int i=n-1;i>=0;i--){
            while(!myStack.empty() && nums[myStack.top()] <= nums[i])
                myStack.pop();
            nge_id[i] = myStack.empty() ? n : myStack.top();
            myStack.push(i);
        }
  
        while(!myStack.empty()) myStack.pop();
        
		// For finding max_subarrays on left
        vector<int> pge_id(n);
        for(int i=0;i<n;i++){
            while(!myStack.empty() && nums[myStack.top()] < nums[i])
                myStack.pop();
            pge_id[i] = myStack.empty() ? -1 : myStack.top();
            myStack.push(i);
        }

        long long total_min = 0;
        long long total_max = 0;
        for(int i=0;i<n;i++){
            total_min += 1LL*(nse_id[i]-i)*(i-pse_id[i])*nums[i];
            total_max += 1LL*(nge_id[i]-i)*(i-pge_id[i])*nums[i];
        }
        
        return (total_max-total_min);
    }
};
```

Return -> [[Stack and Queue]]