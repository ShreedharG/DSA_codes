https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/

```
class Solution {
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        vector<vector<int>> ans;
        if(root==nullptr) return ans;

        queue<TreeNode*> q;
        bool left_right_halle = true;
  
        q.push(root);
        while(!q.empty()){
            int n = q.size();
            vector<int> lvl(n);

            for(int i=0;i<n;i++){
                TreeNode* f_node = q.front();
                q.pop();

                if(f_node->left) q.push(f_node->left);
                if(f_node->right) q.push(f_node->right);

                int id = left_right_halle ? i : n-1-i;
                lvl[id] = f_node->val;                
            }
            left_right_halle = !left_right_halle;
            ans.push_back(lvl);
        }
        return ans;
    }
};
```

Return -> [[Traversals]]
