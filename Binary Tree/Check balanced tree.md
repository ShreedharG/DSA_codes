https://leetcode.com/problems/balanced-binary-tree/
#### We have 2 approaches to solve:

- ###### Height difference: Calculates both left and right subtrees height. If difference is greater than 1 than returns false for unbalanced otherwise goes on to check balance for both left and right subtree.

```
class Solution {
public:
    int height(TreeNode* root){
        if(root==nullptr)  
            return 0;
        
        return 1+max(height(root->left), height(root->right));
    }

    bool isBalanced(TreeNode* root) {
        if(root==nullptr)
            return true;
        
        int subtree_dif = abs(height(root->left) - height(root->right));
        bool h_bal = (subtree_dif<=1 ? true : false);

        return (h_bal && isBalanced(root->left) && isBalanced(root->right));
    }
};
```

- ###### Shorter O(n) recursive trick: Returns the height of the tree if balanced otherwise returns -1

```
class Solution {
public:
    int dfs_height(TreeNode* root){
        if(root==nullptr)
            return 0; 

        int left_height = dfs_height(root->left);
        int right_height = dfs_height(root->right);  

        if(left_height == -1 || right_height == -1) return -1;
        if(abs(left_height - right_height)>1) return -1;

        return (1+max(left_height,right_height));
    }

    bool isBalanced(TreeNode* root) {
        return (dfs_height(root)!=-1);        
    }
};
```

Return -> [[Binary tree]]

