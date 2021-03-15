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



