https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1

**Question: Given an array arr[] of integers, where each element arr[i] represents the number of pages in the i-th book. You also have an integer 'k' representing the number of students. The task is to allocate books to each student such that:

- Each student receives atleast one book.
- Each student is assigned a contiguous sequence of books.
- No book is assigned to more than one student.

The objective is to **minimize the maximum number of pages** assigned to any student. In other words, out of all possible allocations, find the arrangement where the student who receives the most pages still has the **smallest possible maximum**.

**Note:** If it is not possible to allocate books to all students, return **-1**.

```
class Solution {
  public:
    bool isPossible(vector<int> &arr,int n,int pages,int k){
        int num = 1;
        int left = pages;
        
        for(int i=0;i<n;i++){
            if(arr[i]<=left)
                left = left-arr[i];
            else{
                left = pages - arr[i];
                num++;
            }
        }
        return (num <= k);
    }
    
    int findPages(vector<int> &arr, int k){
        int n = arr.size();
        if(k>n) return -1;
        
        int low = *max_element(arr.begin(),arr.end());
        int high = accumulate(arr.begin(),arr.end(),0);
        int ans = -1;
        
        while(low<=high){
            int mid = low + (high-low)/2;
            if(isPossible(arr,n,mid,k)){
                ans = mid;
                high = mid-1;
            }
            else
                low = mid+1;
        }
        return ans;
    }
};
```

Return -> [[Binary search]]

