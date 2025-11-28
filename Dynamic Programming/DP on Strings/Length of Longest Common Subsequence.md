https://leetcode.com/problems/longest-common-subsequence/
###### Top-down Memoization
```
class Solution {
public:
    int LCS(int ind1,int ind2,string t1,string t2,vector<vector<int>>& dp){
        if(ind1<0 || ind2<0) return 0;
        if(dp[ind1][ind2]!=-1) return dp[ind1][ind2];

        if(t1[ind1]==t2[ind2])
            dp[ind1][ind2] = 1+LCS(ind1-1,ind2-1,t1,t2,dp);
        else
            dp[ind1][ind2] = max(LCS(ind1,ind2-1,t1,t2,dp),
                                 LCS(ind1-1,ind2,t1,t2,dp));

        return dp[ind1][ind2];
    }

    int longestCommonSubsequence(string text1, string text2) {
        int s1 = text1.size();
        int s2 = text2.size();
        vector<vector<int>> dp(s1,vector<int>(s2,-1));

        return LCS(s1-1,s2-1,text1,text2,dp);        
    }
};
```

###### Bottom-up Tabulation
```
class Solution {
public:
    int longestCommonSubsequence(string text1, string text2){
        int s1 = text1.size();
        int s2 = text2.size();
        vector<vector<int>> dp(s1+1,vector<int>(s2+1,0));
  
        for(int i=1;i<=s1;i++){
            for(int j=1;j<=s2;j++){
                if(text1[i-1]==text2[j-1])
                    dp[i][j] = 1+dp[i-1][j-1];
                else
                    dp[i][j] = max(dp[i-1][j],dp[i][j-1]);
            }
        }
        return dp[s1][s2];
    }
};
```

Return -> [[DP on Strings]]