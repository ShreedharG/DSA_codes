```
#include<bits/stdc++.h>
using namespace std; 

void ascendingInsertionSort(vector<int> &arr,int n){
    for(int i=1;i<n;i++){
        for(int j=i;j>0;j--){
            if(arr[j]<arr[j-1])
                swap(arr[j],arr[j-1]);
        }
    }
}

void descendingInsertionSort(vector<int> &arr,int n){
    for(int i=1;i<n;i++){
        for(int j=i;j>0;j--){
            if(arr[j]>arr[j-1])
                swap(arr[j],arr[j-1]);
        }
    }
}
```

Return -> [[Sorting Algos]]
