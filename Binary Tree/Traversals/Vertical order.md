https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/

```
class Solution {
public:
    vector<vector<int>> verticalTraversal(TreeNode* root) {
        vector<vector<int>> ans;
        map<int, map<int, multiset<int>>> graphical_nodes;
        queue<pair<TreeNode*, pair<int,int>>> q;
        
        if(root==NULL)
            return ans;

        q.push({root,{0,0}});

        while(!q.empty()){
            pair<TreeNode*, pair<int,int>> temp = q.front();
            q.pop();
            
            TreeNode* front_node = temp.first;
            int hd = temp.second.first;
            int lvl = temp.second.second;
            
            graphical_nodes[hd][lvl].insert(front_node->val); 

            if(front_node->left)
                q.push({front_node->left,{hd-1,lvl+1}});
            if(front_node->right)
                q.push({front_node->right,{hd+1,lvl+1}});            
        }
        
        for(auto& i : graphical_nodes){
            vector<int> column;
            for(auto& j : i.second){
                for(auto k : j.second){
                    column.push_back(k);
                }
            }
            ans.push_back(column);
        }
        return ans;
    }
};
```

[[Traversals]]