https://leetcode.com/problems/binary-tree-right-side-view/

```
class Solution {
public:
    vector<int> rightSideView(TreeNode* root){
        queue<TreeNode*> q;
        vector<int> ans;

        if(root==nullptr)
            return ans;

        q.push(root);

        while(!q.empty()){
            int size = q.size();  

            for(int i=0;i<size;i++){
                TreeNode* temp = q.front();
                if(temp->right) q.push(temp->right);
                if(temp->left) q.push(temp->left);

                q.pop();
                if(i==0)
                    ans.push_back(temp->val);
            }
        }        
        return ans;
    }
};
```

Return -> [[Views]]

