[https://leetcode.com/problems/validate-binary-search-tree/description/]()

```
class Solution{
    public:
        bool check(TreeNode* root,long long min_val,long long max_val){
            if(root==nullptr)
                return true;

            if(root->val >= max_val || root->val <= min_val)
                return false;
                
            return (check(root->left,min_val,root->val) &&
                    check(root->right,root->val,max_val));
        }

        bool isValidBST(TreeNode* root){
            return check(root,LLONG_MIN, LLONG_MAX);
        }
};
```