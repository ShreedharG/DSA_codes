https://leetcode.com/problems/reorder-list/

```
class Solution {
public:
    void reorderList(ListNode* head) {
        if(!head || !head->next || !head->next->next)
            return;

        ListNode* slow = head;
        ListNode* fast = head;
        while(fast->next && fast->next->next){
            slow = slow->next;
            fast = fast->next->next;
        }
  
        ListNode* curr = slow->next;
        slow->next = nullptr;
  
        ListNode* prev = nullptr;
        while(curr){
            ListNode* front = curr->next;
            curr->next = prev;
            prev = curr;
            curr = front;
        }
  
        ListNode* dummy = new ListNode(-1);
        ListNode* temp = dummy;
        bool first = true;

        while(head && prev){
            if(first){
                temp->next = head;
                head = head->next;
            }
            else{
                temp->next = prev;
                prev = prev->next;
            }
            first = !first;
            temp = temp->next;
        }
  
        if(prev) temp->next = prev;
        if(head) temp->next = head;
  
        head = dummy->next;
    }
};
```

Return -> [[Linked List]]

