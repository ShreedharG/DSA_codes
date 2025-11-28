[https://leetcode.com/problems/search-in-a-binary-search-tree/description/]()

```
class Solution {
	public:
	    TreeNode* searchBST(TreeNode* root, int val){
	        if(root==nullptr)
	            return root;
	            
	        if(root->val == val)  
	            return root;
	            	
	        else if(val > root->val)
	            return searchBST(root->right,val);
	
	        else
	            return searchBST(root->left,val);
	    }
};
```
