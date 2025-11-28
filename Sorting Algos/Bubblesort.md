[https://www.geeksforgeeks.org/problems/bubble-sort/1]()

```
#include<bits/stdc++.h>
using namespace std;

void ascendingBubbleSort(vector<int> &arr,int n){
    for (int i=n-1;i>=0;i--){
        for(int j=0;j<i;j++){
            if(arr[j]>arr[j+1])
                swap(arr[j],arr[j+1]);
        }
    }
}

void descendingBubbleSort(vector<int> &arr,int n){
    for (int i=n-1;i>=0;i--){
        for(int j=0;j<i;j++){
            if(arr[j]<arr[j+1])
                swap(arr[j],arr[j+1]);
        }
    }
}
```

Return -> [[Sorting Algos]]
