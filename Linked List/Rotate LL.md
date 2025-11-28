https://leetcode.com/problems/rotate-list/

```
class Solution {
public:
    int find_len(ListNode* head){
        if(head==nullptr)
            return 0;
        return (1+find_len(head->next));
    }
    
    ListNode* rotateRight(ListNode* head, int k) {
        if(head==nullptr || k==0) return head;

        int n = find_len(head);
        if(k==n) return head;

        k = k%n;
        ListNode* temp = head;
        ListNode* prev = head;
        for(int i=0; i < (n-k); i++){
            prev = temp;
            temp = temp->next;
        }
        
        prev->next = nullptr;
        ListNode* trv = temp;
        for(; trv->next != nullptr; trv = trv->next){}
        trv->next = head;
        
        return temp;  
    }
};
```

Return -> [[Linked List]]

