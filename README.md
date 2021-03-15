# DSA-notes
This repository contains summary notes of Data Structures and Algorithms 

<img src="Images/DSA.jpeg" alt="DSA" height="300px">

## Algorithms

A step by step list of instructions for solving any instance of the problem that might arise

**01. Sorting Algorithms**

* Bubble sort
* Selection sort
* Insertion sort
* Merge sort
* Heap sort

**02. Searching Algorithms**

* Linear search
* Binary search

**03. Analyzing Algorithms**

* Time complexity
	* Worst case
	* Average case
	* Best case

* Space complexity
	* Worst case
	* Average case
	* Best case

## Data Structures

Data structure is a way of organizing the data so that it can be used efficiently.

**01. Arrays**

**02. Linked list**

* Singly linked list
* Doubly linked list
* Circular linked list

**03. Stack**

**04. Queue**

* Normal queue
* Circular queue
* Priority queue

**05. Trees**

* Binary trees
* Sorted binary trees

<img src="Images/start.jpg" alt="Start">

## Algorithms

### Bubble Sort

Bubble sort is an algorithm that compares the adjacent elements and swaps their positions if they are not in the intended order. The order can be ascending or descending.

<img src="Images/bubble sort.JPG" alt="bubble sort">

#### Simplest code for bubble sort

```C++

#include <iostream>
using namespace std;

int main(){
    int arr[8]={8, 7, 6, 5, 4, 3, 2, 1};
    int n=8;

    // number of passes - outer for loop
    for(int i=0; i<n-1; i++){
    	// number of comparisons - inner for loop
        for(int j=0; j<n-1; j++){
            
            if(arr[j]>arr[j+1]){
                
                int temp=arr[j];
                arr[j]=arr[j+1];
                arr[j+1]=temp;
            }
        }
    }
    
    for(int i=0; i<8; i++){
        cout << arr[i] << " ";
    }
    return 0;
}

```

#### Optimized code for bubble sort

Inner loop doesn't compare already sorted values

```c++
#include <iostream>
using namespace std;

int main(){
    int arr[8]={8, 7, 6, 5, 4, 3, 2, 1};
	
    int n=8;
    
    for(int i=0; i<n-1; i++){
       
        for(int j=0; j<n-1-i; j++){
            
            if(arr[j]>arr[j+1]){
                
                int temp=arr[j];
                arr[j]=arr[j+1];
                arr[j+1]=temp;
            }
        }
    }
    
    for(int i=0; i<8; i++){
        cout << arr[i] << " ";
    }
    return 0;
}

```

#### Most optimized bubble sort

Inner for-loop doesn't compare already sorted values and if the rest of the array is already in the sorted form execution of the outer for-loop stops

```c++
#include <iostream>
using namespace std;

int main(){
    
    int arr[8]={8, 7, 6, 5, 4, 3, 2, 1};
    int n=8;
    bool control;

    for(int i=0; i<n-1; i++){
    	
    	control=1;
    	
        for(int j=0; j<n-1-i; j++){
            
            if(arr[j]>arr[j+1]){
            	
            	control=0;
                int temp=arr[j];
                arr[j]=arr[j+1];
                arr[j+1]=temp;
            }
        }
        
        if(control){
            break;
	  }
    }
    
    for(int i=0; i<8; i++){
        cout << arr[i] << " ";
    }
    return 0;
}


```

##### Advantages of bubble sort

1. Requires less memory then other sorting techniques.
2. Easy to code.

##### Disdavantages of bubble sort

1. Slow like a snail, time complexity is O(n2)
2. The algorithm will be slowest when the array is sorted by in reverse


<br>

### Selection sort

Selection sort is an algorithm that selects the smallest element from an unsorted list in each iteration and places that element at the beginning of the unsorted list.

<img src="Images/selection sort.JPG" alt="selection sort">

```c++
int main(){
	int arr[]={8, 7, 6, 5, 4, 3, 2, 1};
	
	int length=sizeof(arr)/sizeof(arr[0]);

	sortArray(arr, length);

	return 0;
}


void sortArray(int arr[], int length){
	// selection sort technique
	int index, temp;
	// index - index of temporary minumum value
	// temp - temp variable used for swapping
	for(int i=0; i<length-1; i++){
		
		index=i;
		
		for(int j=i+1; j<length; j++){
			
			if(arr[index]>arr[j]){				
				index=j;
			}
		}

		temp=arr[i];
		arr[i]=arr[index];
		arr[index]=temp;
	}


```

##### Advantages of selection sort

1. It gives the same time complexity regardless of arrangements of items in the array or data set
1. Since number of operations(swapping, size – 1) are less, so its favorable to use when swapping operations are costly in system

##### Disdavantages of selection sort

1. The time complexity is quiet high i.e. O(n2) thus not good


<br>

### Insertion sort

Insertion sort is a sorting algorithm that places an unsorted element at its suitable place in each iteration.

<img src="Images/insertion sort.JPG" alt="insertion sort">

``` c++
int main(){
	int arr[]={8, 7, 6, 5, 4, 3, 2, 1};
	
	int length=sizeof(arr)/sizeof(arr[0]);
	
	sortArray(arr, length);

	return 0;
}


// insertion sort method
void sortArray(int arr[], int length){
	// insertion sort technique
	int key=0, j=0;
	
	for(int i=1; i<length; i++){
		
		key=arr[i]; // the first element of unsorted part
		j=i-1;
		
		while(j>=0 && arr[j]>key){
			arr[j+1]=arr[j];
			j=j-1;
		}
		
		arr[j+1]=key;
	}
} 


```
##### Advantages of insertion sort

1. Only O(1) space requirements
2. For smaller number of items in array its quicker than merge sort

##### Disdavantages of insertion sort

1. Not so good average time complexity of O(n2)
2. If there are large elements then it gives bad performance because of O(n^2) time complexity

