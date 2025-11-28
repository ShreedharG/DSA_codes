https://leetcode.com/problems/largest-rectangle-in-histogram/
###### Brute Force
```
class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        int n = heights.size();
        int maxi = INT_MIN;

        for(int i=0;i<n;i++){
            int mini = heights[i];
            for(int j=i;j<n;j++){
                mini = min(mini,heights[j]);
                maxi = max(maxi,mini*(j-i+1));
            }
        }
        return maxi;
    }
};
```
###### Optimal Approach
```
class Solution {
public:
    int largestRectangleArea(vector<int>& heights){
        int n = heights.size();
        stack<int> myStack;

        vector<int> nse_id(n);
        for(int i=n-1;i>=0;i--){
            while(!myStack.empty() && heights[myStack.top()] >= heights[i])
                myStack.pop();

            nse_id[i] = myStack.empty() ? n : myStack.top();
            myStack.push(i);
        }  

        while(!myStack.empty()) myStack.pop();
  
        vector<int> pse_id(n);
        for(int i=0;i<n;i++){
            while(!myStack.empty() && heights[myStack.top()] >= heights[i])
                myStack.pop();

            pse_id[i] = myStack.empty() ? -1 : myStack.top();
            myStack.push(i);
        }
  
        int maxi = INT_MIN;
        for(int i=0;i<n;i++){
            int width = nse_id[i] - pse_id[i] - 1;
            maxi = max(maxi,width*heights[i]);
        }
        return maxi;
    }
};
```

Return -> [[Stack and Queue]]