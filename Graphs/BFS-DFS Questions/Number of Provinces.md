https://leetcode.com/problems/number-of-provinces/description/
###### BFS Approach
```
class Solution {
public:
    int findCircleNum(vector<vector<int>>& isConnected) {
        int n = isConnected.size();
        vector<bool> vis(n,false);
        int count = 0;
        queue<int> q;
  
        for(int i=0;i<n;i++){
            if(vis[i] == false){
                count++;
                vis[i] = true;
                q.push(i);

                while(!q.empty()){
                    int node = q.front(); q.pop();
  
                    for(int j=0;j<n;j++){
                        if(isConnected[node][j]==1 && !vis[j]){
                            vis[j] = true;
                            q.push(j);
                        }
                    }
                }
            }
        }
        return count;
    }
};
```

###### DFS Approach
```
class Solution {
public:
    void dfs(int node,vector<bool>& vis,vector<vector<int>>& graph,int n){
        vis[node] = true;
        for(int i = 0; i < n; i++){
            if(graph[node][i]==1 && !vis[i])
                dfs(i,vis,graph,n);
        }
    }
  
    int findCircleNum(vector<vector<int>>& isConnected) {
        int n = isConnected.size();
        vector<bool> vis(n,false);
        int ans = 0;

        for(int i=0;i<n;i++){
            if(!vis[i]){
                ans++;
                dfs(i,vis,isConnected,n);
            }
        }
        return ans;
    }
};
```
###### Union Find (DSU Method)
```
class Solution {
public:
    int find(int x, vector<int>& parent){
        if(x == parent[x]) 
	        return x;

        return parent[x] = find(parent[x],parent);
    }

    void dsu_union(int i,int j,vector<int>& parent){
        int p1 = find(i,parent);
        int p2 = find(j,parent);
  
        if(p1 != p2)
            parent[p2] = p1;
    }

    int findCircleNum(vector<vector<int>>& isConnected) {
        int n = isConnected.size();
        vector<int> parent(n);
        for(int i=0;i<n;i++)
            parent[i] = i;

        for(int i = 0; i < n; i++){
            for(int j = i+1; j < n; j++){
                if(isConnected[i][j]==1)
                    dsu_union(i,j,parent);
            }
        }
  
        int count = 0;
        for(int i=0;i<n;i++)
            if(find(i,parent) == i) count++;
  
        return count;
    }
};
```

Return -> [[Based on BFS-DFS Traversals]] , [[MST and Disjoint Set Problems]]

