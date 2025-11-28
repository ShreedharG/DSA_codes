https://leetcode.com/problems/reverse-nodes-in-k-group/

```
class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        ListNode* temp = head;
        
        for(int i=0;i<k;i++){
            if(temp==nullptr)
                return head;
            temp = temp->next;
        }

        ListNode* prev = nullptr;
        ListNode* current = head;

        while(current!=temp){
            ListNode* front = current->next;
            current->next = prev;
            prev = current;
            current = front;
        }

        head->next = reverseKGroup(current,k);
        
        return prev;        
    }
};
```

Return -> [[Linked List]]

