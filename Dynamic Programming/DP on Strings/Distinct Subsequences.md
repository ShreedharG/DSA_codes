https://leetcode.com/problems/distinct-subsequences/
###### Recursive
```
class Solution {
public:
    int find_distinct(int ind1,int ind2,string s,string t,int n,int m){
        if(ind2==m) return 1;
        if(ind1==n) return 0;

        int matched = 0;
        if(s[ind1]==t[ind2])
            matched = find_distinct(ind1+1,ind2+1,s,t,n,m);

        int not_matched = find_distinct(ind1+1,ind2,s,t,n,m);
        
        return not_matched + matched;
    }
    int numDistinct(string s, string t) {
        int n = s.size();
        int m = t.size();

        return find_distinct(0,0,s,t,n,m);
    }
};
```
###### Top-down Memoization
```
class Solution {
public:
    int find_distinct(int i1,int i2,string s,string t,int n,int m,vector<vector<int>>& dp){
        if(i2==m) return 1;
        if(i1==n) return 0;
        if(dp[i1][i2]!=-1) return dp[i1][i2];

        int matched = 0;
        if(s[i1]==t[i2])
            matched = find_distinct(i1+1,i2+1,s,t,n,m,dp);

        int not_matched = find_distinct(i1+1,i2,s,t,n,m,dp);

        return (dp[i1][i2] = not_matched + matched);
    }

    int numDistinct(string s, string t){
        int n = s.size();
        int m = t.size();
        vector<vector<int>> dp(n,vector<int>(m+1,-1));

        return find_distinct(0,0,s,t,n,m,dp);
    }
};
```
###### Bottom-up Tabulation
```
class Solution {
public:
    int numDistinct(string s, string t) {
        int n = s.size();
        int m = t.size();
        vector<vector<int>> dp(n+1,vector<int>(m+1,0));
        
        for(int i=0;i<=n;i++) dp[i][0] = 1;
        for(int j=1;j<=m;j++) dp[0][j] = 0;  

        for(int i=1;i<=n;i++){
            for(int j=1;j<=m;j++){
                if(s[i-1]==t[j-1])
                    dp[i][j] = dp[i-1][j-1] + dp[i-1][j];
                else
                    dp[i][j] = dp[i-1][j];
            }
        }
        return dp[n][m];
    }
};
```

Return -> [[DP on Strings]]