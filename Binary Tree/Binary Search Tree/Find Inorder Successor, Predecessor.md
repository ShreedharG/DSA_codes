https://www.geeksforgeeks.org/problems/predecessor-and-successor/1

```
class Solution {
  public:
    vector<Node*> findPreSuc(Node* root, int key){
        if(root==NULL) return {NULL,NULL};
        
        Node* pre = NULL; Node* succ = NULL;
        
        Node* curr = root;
        while(curr){
            if(curr->data == key){
                if(curr->left){
                    Node* temp = curr->left;
                    while(temp->right)
                        temp = temp->right;
                    
                    pre = temp;
                }
                if(curr->right){
                    Node* temp = curr->right;
                    while(temp->left)
                        temp = temp->left;
                    
                    succ = temp;
                }
                break;
            }
            else if(curr->data < key){
                pre = curr;
                curr = curr->right;
            }
            else {
                succ = curr;
                curr = curr->left;
            }
        }
        
        return {pre,succ};
    }
};
```

Return -> [[Binary search tree]]

