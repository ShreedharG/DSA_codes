https://www.geeksforgeeks.org/problems/next-larger-element-1587115620/1
#### Greater Element
```
vector<int> nextLargerElement(vector<int>& arr) {
	vector<int> nge(arr.size(),-1);
	stack<int> myStack;
	
	for(int i=arr.size()-1 ;i>=0 ;i--){
		while(!myStack.empty() && myStack.top() <= arr[i])
			myStack.pop(); 
		nge[i] = myStack.empty() ? -1 : myStack.top();
		myStack.push(arr[i]);
	}
	return nge;
}
```

###### Next Greater Element Index
```
vector<int> nextLargerElement(vector<int>& arr) {
	vector<int> nge_id(arr.size());
	stack<int> myStack;
	
	for(int i=arr.size()-1 ;i>=0 ;i--){
		while(!myStack.empty() && arr[myStack.top()] <= arr[i])
			myStack.pop(); 
			
		nge_id[i] = myStack.empty() ? n : myStack.top();
		myStack.push(i);
	}
	return nge_id;
}
```

https://www.naukri.com/code360/problems/next-greater-element_1112581?leftPanelTabValue=PROBLEM
#### Smaller Element
```
#include <stack>
vector<int> nextSmallerElement(vector<int> &arr, int n){
    vector<int> nse(n,-1);
    stack<int> myStack;

    for(int i=n-1;i>=0;i--){
        while(!myStack.empty() && myStack.top()>=arr[i])
            myStack.pop();
        nse[i] = myStack.empty() ? -1 : myStack.top();
        myStack.push(arr[i]);
    }
    return nse;
}
```

###### Next Smaller Element Index
```
#include <stack>
vector<int> nextSmallerElement(vector<int> &arr, int n){
    vector<int> nse_id(n);
    stack<int> myStack;

    for(int i=n-1;i>=0;i--){
        while(!myStack.empty() && arr[myStack.top()] >= arr[i])
            myStack.pop();
        nse_id[i] = myStack.empty() ? n : myStack.top();
        myStack.push(i);
    }
    return nse_id;
}
```

Return -> [[Stack and Queue]]

