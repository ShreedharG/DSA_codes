https://leetcode.com/problems/merge-k-sorted-lists/

```
class Solution {
public:
    struct compare {
        bool operator()(ListNode* a, ListNode* b) {
            return a->val > b->val;  
        }
    };
  
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        priority_queue<ListNode*,vector<ListNode*>,compare> minHeap;

        for(auto list : lists){
            if(list != nullptr)
                minHeap.push(list);
        }

        ListNode* dummy = new ListNode(-1);
        ListNode* tail = dummy;
  
        while(!minHeap.empty()){
            ListNode* node = minHeap.top();
            minHeap.pop();
  
            tail->next = node;
            tail = node;
  
            if(node->next) minHeap.push(node->next);
        }
        return dummy->next;
    }
};
```

Return -> [[Heaps]]

