[https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/]()

```
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q){
        if(root==nullptr || root==q || root==p)
            return root;        

        if((root->val > q->val) && (root->val > p->val))
            return lowestCommonAncestor(root->left,p,q);
            
        else if((root->val < q->val) && (root->val < p->val))
            return lowestCommonAncestor(root->right,p,q);
            
        else
            return root;
    }
};
```
