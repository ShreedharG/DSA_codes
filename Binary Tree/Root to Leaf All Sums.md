https://leetcode.com/problems/sum-root-to-leaf-numbers/description/?envType=study-plan-v2&envId=top-interview-150

```
class Solution {
public:
    int sumTree(TreeNode* root, int num){
        if(root==nullptr) return 0;
  
        num = num*10 + root->val;
  
        if(!root->left && !root->right) return num;
        
        return sumTree(root->left,num) + sumTree(root->right,num);
    }
  
    int sumNumbers(TreeNode* root) {
        if(root==nullptr)
            return 0;
            
        return sumTree(root,0);
    }
};
```

Return -> [[Binary tree]]

