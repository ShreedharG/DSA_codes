https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1&selectedLang=python3

```
class Solution {
  public:
    void generate_paths(int row,int col,string& path,vector<vector<int>>& visited,vector<string>& ans,vector<vector<int>>& maze,int n){
        if(row<0 || col<0 || row>=n || col>=n || maze[row][col]==0 || visited[row][col]==1) 
            return;
        
        if(row==n-1 && col==n-1){
            ans.push_back(path);
            return;
        }
        
        visited[row][col] = 1;
        
        if(row<=n-2){
            path += 'D';
            generate_paths(row+1,col,path,visited,ans,maze,n);
            path.pop_back();
        }
        if(col<=n-2){
            path +='R';
            generate_paths(row,col+1,path,visited,ans,maze,n);
            path.pop_back();
        }
        
        if(row>0){
            path += 'U';
            generate_paths(row-1,col,path,visited,ans,maze,n);
            path.pop_back();            
        }
        
        if(col>0){
            path += 'L';
            generate_paths(row,col-1,path,visited,ans,maze,n);
            path.pop_back();            
        }
        visited[row][col] = 0;
    }
    vector<string> ratInMaze(vector<vector<int>>& maze){
        int n = maze.size();
        string path;
        vector<vector<int>> visited(n, vector<int>(n, 0));
        vector<string> ans;
        
        if(maze[0][0]==1)
            generate_paths(0,0,path,visited,ans,maze,n);
        
        set<string> unique_paths(ans.begin(),ans.end());
        vector<string> final_ans(unique_paths.begin(), unique_paths.end());
            
        return final_ans;
    }
};
```

Return -> [[Recursion + Backtracking]]
