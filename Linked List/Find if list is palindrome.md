https://leetcode.com/problems/palindrome-linked-list/submissions/1604829101/

```
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        if(head==nullptr || head->next==nullptr)
            return bool(head);

        ListNode* prev = find_middle(head);
        
        ListNode* secondHalf = prev->next;
        prev->next = nullptr;

        secondHalf = reverseLL(secondHalf);
        ListNode* firstHalf = head;

        while(secondHalf!=nullptr && firstHalf!=nullptr){
            if(secondHalf->val!=firstHalf->val)
                return false;

            firstHalf = firstHalf->next;
            secondHalf = secondHalf->next;
        }
        return true;
    }
};
```

Return -> [[Linked List]]

