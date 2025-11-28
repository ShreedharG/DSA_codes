https://leetcode.com/problems/maximal-rectangle/description/

```
class Solution {
public:
    vector<int> find_nse_id(vector<int>& arr,int m){
        vector<int> nse(m);
        stack<int> myStack;
        for(int i=m-1;i>=0;i--){
            while(!myStack.empty() && arr[myStack.top()] >= arr[i])
                myStack.pop();

            nse[i] = myStack.empty() ? m : myStack.top();
            myStack.push(i);
        }
        return nse;
    }

    vector<int> find_pse_id(vector<int>& arr,int m){
        vector<int> pse(m);
        stack<int> myStack;
        for(int i=0;i<m;i++){
            while(!myStack.empty() && arr[myStack.top()] >= arr[i])
                myStack.pop();

            pse[i] = myStack.empty() ? -1 : myStack.top();
            myStack.push(i);
        }
        return pse;
    }

    int largestRectangleArea(vector<int>& arr){
        vector<int> nse_id = find_nse_id(arr,m);
        vector<int> pse_id = find_pse_id(arr,m);
        int max_area = INT_MIN;
  
        for(int i=0;i<m;i++){
            int width = nse_id[i] - pse_id[i] - 1;
            max_area = max(max_area,width*arr[i]);
        }
        return max_area;
    }

    int maximalRectangle(vector<vector<char>>& matrix) {
        int n = matrix.size();
        int m = matrix[0].size();
        vector<vector<int>> dp(n,vector<int>(m,0));

        for(int i=0;i<m;i++) dp[0][i] = matrix[0][i] - '0';
        for(int i=1;i<n;i++){
            for(int j=0;j<m;j++){
                int val = matrix[i][j] - '0';
                if(val)
                    dp[i][j] = 1 + dp[i-1][j];
                else
                    dp[i][j] = 0;
            }
        }

        int ans = 0;
        for(int i=0;i<n;i++)
            ans = max(ans, largestRectangleArea(dp[i]));
        return ans;
    }
};
```

Return -> [[Stack and Queue]]