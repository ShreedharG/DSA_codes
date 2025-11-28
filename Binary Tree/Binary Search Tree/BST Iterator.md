[https://leetcode.com/problems/binary-search-tree-iterator/]()

%% BST iterator has three members functions : 1) Initiation , 2) Next element , 3) Check whether the stack is empty #bstiterator  %%

```
class BSTIterator {
    private:
        stack<TreeNode*> my_stack; 
        void insert_nodes(TreeNode* root){
            while(root){
                my_stack.push(root);
                root = root->left;
            }
        }        
    public:
        BSTIterator(TreeNode* root){
            insert_nodes(root);
        }
        
        int next(){
            TreeNode* temp = my_stack.top();
            my_stack.pop();
            insert_nodes(temp->right);

            return temp->val;
        }

        bool hasNext() {
            return (!my_stack.empty());
        }
};
```