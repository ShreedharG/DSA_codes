https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1

```
class Solution {
  public:
    Node* addOne(Node* head){
        if(head==nullptr) return head;
        
        head = reverseList(head);
        Node* temp = head;
        int carry = 1;
        
        while(temp!=nullptr){
            int sum = temp->data + carry;
            temp->data = sum%10;
            carry = sum/10;
            if(carry!=0 && temp->next==nullptr){
                Node* new_node = new Node(1);
                temp->next = new_node;
                break;
            }
            temp = temp->next;
        }        
        head = reverseList(head);
        return head;
        
    }
};
```

Return -> [[Linked List]]

