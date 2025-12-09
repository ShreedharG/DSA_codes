https://leetcode.com/problems/average-of-levels-in-binary-tree/?envType=study-plan-v2&envId=top-interview-150

```
class Solution {
public:
    vector<double> averageOfLevels(TreeNode* root) {
        vector<double> ans;
        queue<TreeNode*> q;
  
        q.push(root);
        while(!q.empty()){
            int sz = q.size();
            double sum = 0;
            for(int i = 0; i < sz; i++){
                auto temp = q.front();
                q.pop();
  
                sum += 1.0*temp->val;
                if(temp->left) q.push(temp->left);
                if(temp->right) q.push(temp->right);
            }
            ans.push_back(sum/sz);
        }
  
        return ans;
    }
};
```

Return -> [[Binary tree]]

