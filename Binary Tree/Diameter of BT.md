https://leetcode.com/problems/diameter-of-binary-tree/description/

```
class Solution {
public:
    int dfs_height(int& maxi,TreeNode* root){
        if(root==nullptr) return 0;

        int lh = dfs_height(maxi,root->left);
        int rh = dfs_height(maxi,root->right);

        maxi = max(maxi,lh+rh);
        return (1+max(lh,rh));
    }

    int diameterOfBinaryTree(TreeNode* root) {
       int maxi = 0;
       int height = dfs_height(maxi,root);

       return maxi;
    }
};
```

Return -> [[Binary tree]]

