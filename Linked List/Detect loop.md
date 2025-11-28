https://leetcode.com/problems/linked-list-cycle/

```
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if(head==nullptr || head->next==nullptr)
            return false;
            
        ListNode* slow = head;
        ListNode* fast = head;

        while(fast!=nullptr && fast->next!=nullptr){
            slow = slow->next;
            fast = fast->next->next;  

            if(slow==fast)
                return true;
        }
        return false;
    }
};
```


Return -> [[Linked List]]

