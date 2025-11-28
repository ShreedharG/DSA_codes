https://www.geeksforgeeks.org/problems/flattening-a-linked-list/1

```
class Solution {
  public:
    Node* merge(Node* head1, Node* head2){
        head1->next = nullptr;
        
        Node* dummy = new Node(-1);
        Node* temp = dummy;
        
        while(head1 && head2){
            if(head1->data <= head2->data){
                temp->bottom = head1;
                head1 = head1->bottom;
            }
            else{
                temp->bottom = head2;
                head2 = head2->bottom;
            }
            temp = temp->bottom;
        }
        
        if(head1) temp->bottom = head1;
        if(head2) temp->bottom = head2;
        
        Node* head = dummy->bottom;
        delete dummy;
        
        return head;
    }
    
    Node *flatten(Node *root){
        if(!root || !root->next)
            return root;
        
        root->next = flatten(root->next);
        
        root = merge(root,root->next);
        
        return root;
    }
};
```


Return -> [[Linked List]]

