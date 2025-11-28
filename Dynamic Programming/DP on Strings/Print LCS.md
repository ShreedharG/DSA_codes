https://www.naukri.com/code360/problems/print-longest-common-subsequence_8416383?leftPanelTabValue=PROBLEM

```
string findLCS(int n, int m,string &s1, string &s2){
    vector<vector<int>> dp(n+1,vector<int>(m+1,0)); 

    for(int i=1;i<=n;i++){
        for(int j=1;j<=m;j++){
            if(s1[i-1]==s2[j-1])
                dp[i][j] = 1+dp[i-1][j-1];
            else
                dp[i][j] = max(dp[i-1][j],dp[i][j-1]);
        }
    }
    int max_length = dp[n][m];
    string ans = "";
    for(int it=0;it<max_length;it++)
        ans += '@';

    int index = max_length-1;
    int i=n;
    int j=m;

    while(i>0 && j>0){
        if(s1[i-1]==s2[j-1]){
            ans[index] = s1[i-1];
            index--;
            i--;
            j--;
        }
        else if(dp[i-1][j] > dp[i][j-1])
            i = i-1; 
        else
            j = j-1;
    }
    return ans;
}
```

Return -> [[DP on Strings]]
