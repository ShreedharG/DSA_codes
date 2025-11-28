https://leetcode.com/problems/binary-tree-level-order-traversal/description/

```
class Solution {
    public:
        vector<vector<int>> levelOrder(TreeNode* root) {
            queue<TreeNode*> q;
            vector<vector<int>> ans;

            if(root==nullptr)
                return ans;
                
            q.push(root);
  
            while(!q.empty()){
                int size = q.size();
                vector<int> level;

                for(int i=0;i<size;i++){
                    TreeNode* temp = q.front();                
                    if(temp->left) q.push(temp->left);
                    if(temp->right) q.push(temp->right);
                    
                    q.pop();
                    level.push_back(temp->val);
                }
                ans.push_back(level);
            }
            return ans;                
        }
};
```

Return -> [[Traversals]]

