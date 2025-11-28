[https://www.geeksforgeeks.org/problems/kth-largest-element-in-bst/1]()

Similar to the [[Kth smallest]] problem, we reverse the #inOrder traversal by first traversing the right nodes and then recursively moving to root and then right half.

```
class Solution {
  public:
    void fetch_k(Node* root,int k,int* i,int* kth_l){
        if(root==nullptr || *i>k)
            return;
        
        fetch_k(root->right,k,i,kth_l);
        
        (*i)++;
        if(*i==k){
            *kth_l = root->data;
            return;
        }
        
        fetch_k(root->left,k,i,kth_l);
    }
    int kthLargest(Node *root, int k){
        int i=0;
        int kth_largest;
        fetch_k(root,k,&i,&kth_largest);
        
        return kth_largest;
    }
};
```

