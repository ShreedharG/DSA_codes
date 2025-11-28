https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/
#### We have 2 approaches to solve the problem -
- ###### Finding full paths and comparing : Find the paths of both the nodes. Iterate over both the paths and return the previous node to point of mismatch. Space complexity is increased : stores both the nodes path.

```
class Solution {
public:
    bool dfs_path(TreeNode* root, TreeNode* target, vector<TreeNode*> &path){
        if(root==nullptr)
            return false;
            
        path.push_back(root);
        
        if(root==target)
            return true;
            
        if(dfs_path(root->left,target,path) ||
           dfs_path(root->right,target,path))
            return true;

        path.pop_back();
        return false;        
    }  

    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q){
        if(root==nullptr || root==p || root==q) //Edge case 
            return root;

        vector<TreeNode*> p_path;
        vector<TreeNode*> q_path;
        
        dfs_path(root, p, p_path); // Paths of both the nodes
        dfs_path(root, q, q_path);

        int i = 0;
        while(i<p_path.size() && i<q_path.size() && p_path[i]==q_path[i])
            i++; 

        return p_path[i-1];  // Returns the previous to point of mismatch
    }
};
```

- ###### Recursive method of comparing left and subtrees : If the current node possesses both nodes in either of the branches ie LCA will be the node where the paths to `p` and `q` **diverge** for the first time. Space complexity is only for stack.

```
class Solution {
public:
    TreeNode* LCA(TreeNode* root, TreeNode* p, TreeNode* q){
        if(root==nullptr || root==p || root==q) // Edge case
            return root;

        TreeNode* left = LCA(root->left,p,q); // Finds in left subtree
        TreeNode* right = LCA(root->right,p,q);  // Finds in right subtree

		// Point of divergence
        if(left && right)
            return root;
            
        // Returns left subtree -> both nodes in left subtree
        // Returns right subtree -> both nodes in right subtree
        // Returns null -> both nodes aren't present
        return (left ? left : right);
    }
};
```

Return -> [[Binary tree]]

