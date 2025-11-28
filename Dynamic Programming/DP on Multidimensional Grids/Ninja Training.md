https://www.naukri.com/code360/problems/ninja%E2%80%99s-training_3621003
###### Recursive approach
```
int solve(int day, int n, vector<vector<int>> &points, int last) {
    if(day == n) 
        return 0;  

    int max_sum = 0;
    for(int task = 0; task < 3; task++) {
        if(task == last) continue;
        int current = points[day][task] + solve(day+1, n,points,task);
        max_sum = max(max_sum, current);
    }
    return max_sum;
} 

int ninjaTraining(int n, vector<vector<int>> &points) {
    return solve(0, n, points, -1);
}
```

###### Memoization Approach
```
int solve(int d,int last,vector<vector<int>> &dp,vector<vector<int>> &points){
    int maxi = 0;
    if(d==0){
        for(int i=0;i<3;i++){
            if(i==last) continue;
            maxi = max(maxi,points[0][i]);
        }
        return (dp[0][last] = maxi);
    } 

    if(dp[d][last]!=-1) return dp[d][last];  

    for(int i=0;i<3;i++){
        if(i==last) continue;
        int point = points[d][i] + solve(d-1,i,dp,points);
        maxi = max(maxi,point);
    }
    return (dp[d][last] = maxi);
}  

int ninjaTraining(int n, vector<vector<int>> &points){
    vector<vector<int>> dp(n, vector<int> (4,-1));
    return solve(n-1,3,dp,points);
}
```

###### Bottom-Up Tabulation
```
int ninjaTraining(int n, vector<vector<int>> &points){
    vector<vector<int>> dp(n, vector<int> (4,-1));
    dp[0][0] = max(points[0][1],points[0][2]);
    dp[0][1] = max(points[0][0],points[0][2]);
    dp[0][2] = max(points[0][0],points[0][1]);
    dp[0][3] = max(points[0][0],max(points[0][1],points[0][2]));
  

    for(int day=1;day<n;day++){
        for(int last=0;last<4;last++){
            dp[day][last] = 0;
            for(int tasks=0;tasks<3;tasks++){
                if(tasks!=last){
                    int point = points[day][tasks] + dp[day-1][tasks];
                    dp[day][last] = max(dp[day][last],point);
                } 
            }
        }
    }
    return dp[n-1][3];
}
```

Return to  -> [[DP on 2D,3D Grids]]