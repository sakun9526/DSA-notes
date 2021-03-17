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


### Divide and conquer algorithms

Divide and conquer algorithms has 03 main steps

**01. Divide**

* This step involves breaking problem into smaller sub problems.
* Sub problem should represent a part of the original problem.
* Use recursion to divide the problem into sub problems continuously

**02. Conquer**

* Solves all the sub problems 

**03. Combine**

* After smaller sub problems are solved, this step recursively merges them until it formulates the solution for the original problem


#### Advantages of divide and conquer algorithms

1. Uses recursion instead of for loops

2. Allows us to solve difficult complex problems in simple manner

3. Makes efficient use of memory caches 


<br>

### Merge sort

<img src="Images/merge sort gif.gif" alt="merge sort gif">
<img src="Images/merge sort.JPG" alt="merge sort">

**Code**

```c++

#include <iostream>
using namespace std;


void mergeSort(int[], int, int);
void merge(int[], int, int, int);


int main(){
	int arr[]={8, 7, 6, 5, 4, 3, 2, 1};
	int length=sizeof(arr)/sizeof(arr[0]);
	
	
	cout << "Unsorted Array : ";
	for(int i=0; i<length; i++){
		cout << arr[i] << " ";
	}
	cout << endl << endl;
	
	
	mergeSort(arr, 0, length-1);
	
	
	cout << "Sorted Array : ";
	for(int i=0; i<length; i++){
		cout << arr[i] << " ";
	}
	cout << endl << endl;
	return 0;
}


// mergeSort function
// recursively breaks the array into two halves from the middle until the entire array is broken down into single elements
// and calls the merge function for each and every recursive step
void mergeSort(int arr[], int l, int r){
	// checks whether the array is completely broken down into single elements
	if(l<r){
		int mp=(l+r)/2; // calculates the midpoint
		
		
		// breaks down the array into 2 halves
		// first half contains elements related to indexes l to mp
		// second half contains elements related to indexes mp+1 to r
		mergeSort(arr, l, mp);
		mergeSort(arr, mp+1, r);
		
		
		// merges the two seperated halves while sorting them
		merge(arr, mp, l, r);
	}
}


// merge function
// stores the two havles of the original array in two seperate temporary arrays
// merges the 2 arrays(already sorted) while sorting the final one
// so, the resultant merged array will be a sorted one
void merge(int arr[], int mp, int l, int r){
	// creates 2 temporary arrays of appropriate sizes
	int size1=mp-l+1;
	int size2=r-mp;
	int tempArr1[size1];
	int tempArr2[size2];
	
	
	// assigns the two halves of the original array to the 2 temporary arrays
	for(int i=0, j=l; i<size1; i++, j++){
		tempArr1[i]=arr[j];
	}
	
	
	for(int i=0, j=mp+1; i<size2; i++, j++){
		tempArr2[i]=arr[j];
	}
	
	
	// merges the two arrays while sorting
	// the two arrays are already sorted because this function is called in every recursive step of mergeSort()
	// So, elements are copied until all the elements of one array is completely copied
	int i=0, j=0, k=l;
	while(i<size1 && j<size2){
		if(tempArr1[i]<=tempArr2[j]){
			arr[k]=tempArr1[i];
			i++;
		}else{
			arr[k]=tempArr2[j];
			j++;
		}
		
		k++;
	}
	
	
	// the remaining elements of the other array are copied to the merged array as the final step
	while(i<size1){
		arr[k]=tempArr1[i];
		k++;
		i++;
	}
	
	while(j<size2){
		arr[k]=tempArr2[j];
		k++;
		j++;
	}
}

```
**Pseudocode**

``` markdown

procedure mergesort( var a as array )
   if ( n == 1 ) return a

   var l1 as array = a[0] ... a[n/2]
   var l2 as array = a[n/2+1] ... a[n]

   l1 = mergesort( l1 )
   l2 = mergesort( l2 )

   return merge( l1, l2 )
end procedure

procedure merge( var a as array, var b as array )

   var c as array
   while ( a and b have elements )
      if ( a[0] > b[0] )
         add b[0] to the end of c
         remove b[0] from b
      else
         add a[0] to the end of c
         remove a[0] from a
      end if
   end while
   
   while ( a has elements )
      add a[0] to the end of c
      remove a[0] from a
   end while
   
   while ( b has elements )
      add b[0] to the end of c
      remove b[0] from b
   end while
   
   return c
	
end procedure

```

##### Advantages of merge sort

1. With a good time complexity of O(n log n), merge sort is great !!!

##### Disdavantages of merge sort

1. Poor space complexity of O(n)
2. Lots of overhead in copying data between arrays and making new arrays

<br>

### Quick sort

<img src="Images/quick sort gif.gif" alt="quick sort">

**Code**

``` C++
#include <iostream>
using namespace std;


void quickSort(int[], int, int);
int partition(int[], int, int);
void swap(int*, int*);


int main(){
	int arr[]={8, 7, 6, 5, 4, 3, 2, 1};
	int length=sizeof(arr)/sizeof(arr[0]);
	
	
	cout << "Unsorted Array : ";
	for(int i=0; i<length; i++){
		cout << arr[i] << " ";
	}
	cout << endl << endl;
	
	
	quickSort(arr, 0, length-1);
	
	
	cout << "Sorted Array : ";
	for(int i=0; i<length; i++){
		cout << arr[i] << " ";
	}
	cout << endl << endl;

	return 0;
}


// calls partition() in every recursive step to bring the pivot to it's right position(sorted position)
// divides the array into 2 subarrays around the sorted position of the pivot
// and recursively calls quickSort() for both those sub arrays
void quickSort(int arr[], int l, int r){
	if(l<r){
		int pivot=partition(arr, l, r);
		
		quickSort(arr, l, pivot-1); // quickSort() first half (before pivot)
		quickSort(arr, pivot+1, r); // quickSort() second half (after pivot)
	}
}


// last element of the array or the sub array is taken as the pivot
// brings the privot to the right position of the array(sorts the pivot)
// and returns the correct position(sorted position) of the pivot in the array
int partition(int arr[], int l, int r){
	int pivot=arr[r];
	
	int i=l-1;
	for(int j=l; j<r; j++){
		if(arr[j]<pivot){
			i++;
			swap(&arr[i], &arr[j]);
		}
	}
	
	swap(&arr[i+1], &arr[r]);
	
	return i+1;
}


// swaps two numbers using pointers
void swap(int *num1, int *num2){
	int temp=*num1;
	*num1=*num2;
	*num2=temp;
}

```

**Pseudocode**

``` markdown

function partitionFunc(left, right, pivot)
   leftPointer = left
   rightPointer = right - 1

   while True do
      while A[++leftPointer] < pivot do
         //do-nothing            
      end while
		
      while rightPointer > 0 && A[--rightPointer] > pivot do
         //do-nothing         
      end while
		
      if leftPointer >= rightPointer
         break
      else                
         swap leftPointer,rightPointer
      end if
		
   end while 
	
   swap leftPointer,right
   return leftPointer
	
end function

```

<br>

### Heap sort


<img src="Images/heap sort gif.gif">
<br>
<img src="Images/heap sort.JPG" alt="heap sort">

``` c++
// Heap Sort in C++
  
  #include <iostream>
  using namespace std;
  
  void heapify(int arr[], int n, int i) {
    // Find largest among root, left child and right child
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;
  
    if (left < n && arr[left] > arr[largest])
      largest = left;
  
    if (right < n && arr[right] > arr[largest])
      largest = right;
  
    // Swap and continue heapifying if root is not largest
    if (largest != i) {
      swap(arr[i], arr[largest]);
      heapify(arr, n, largest);
    }
  }
  
  // main function to do heap sort
  void heapSort(int arr[], int n) {
    // Build max heap
    for (int i = n / 2 - 1; i >= 0; i--)
      heapify(arr, n, i);
  
    // Heap sort
    for (int i = n - 1; i >= 0; i--) {
      swap(arr[0], arr[i]);
  
      // Heapify root element to get highest element at root again
      heapify(arr, i, 0);
    }
  }
  
  // Print an array
  void printArray(int arr[], int n) {
    for (int i = 0; i < n; ++i)
      cout << arr[i] << " ";
    cout << "\n";
  }
  
  // Driver code
  int main() {
    int arr[] = {1, 12, 9, 5, 6, 10};
    int n = sizeof(arr) / sizeof(arr[0]);
    heapSort(arr, n);
  
    cout << "Sorted array is \n";
    printArray(arr, n);
  }

```

<br>

### Linear Search

Linear search is the simplest searching algorithm that searches for an element in a list in sequential order. We start at one end and check every element until the desired element is found.

<img src="Images/linear search gif.gif" alt="linear search">

**Code**

```c++
// Linear Search in C++

#include <iostream>
using namespace std;

int search(int array[], int n, int x) {

  // Going through array sequencially
  for (int i = 0; i < n; i++)
    if (array[i] == x)
      return i;
  return -1;
}

int main() {
  int array[] = {2, 4, 0, 1, 9};
  int x = 1;
  int n = sizeof(array) / sizeof(array[0]);

  int result = search(array, n, x);

  (result == -1) ? cout << "Element not found" : cout << "Element found at index: " << result;
}

```

**Pseudocode**

```markdown
procedure linear_search (list, value)

   for each item in the list
      if match item == value
         return the item's location
      end if
   end for

end procedure

```

<br>

### Binary Search

Binary Search is a searching algorithm for finding an element's position in a sorted array.

#### Iteration method

``` markdown

do until the pointers low and high meet each other.
    mid = (low + high)/2
    if (x == arr[mid])
        return mid
    else if (x > arr[mid]) // x is on the right side
        low = mid + 1
    else                       // x is on the left side
        high = mid - 1

```

#### Recursive method

``` markdown

binarySearch(arr, x, low, high)
    if low > high
        return False 
    else
        mid = (low + high) / 2 
        if x == arr[mid]
            return mid
        else if x < arr[mid]        // x is on the right side
            return binarySearch(arr, x, mid + 1, high)
        else                               // x is on the right side
            return binarySearch(arr, x, low, mid - 1)

```

<br>

## Complexity

TC - Time complexity , SC - Space complexity



| Algorithm         | TC - Worst Case  | TC - Average Case | TC - Best Case  | SC - Worst Case  |
| ----------------- | ---------------- | ----------------- | --------------  | -----------------|
| Bubble sort       | O(n<sup>2</sup>) | O(n<sup>2</sup>)  | O(n)            | O(1)             |
| Selection sort    | O(n<sup>2</sup>) | O(n<sup>2</sup>)  | O(n<sup>2</sup>)| O(1)             | 
| Insertion sort    | O(n<sup>2</sup>) | O(n<sup>2</sup>)  | O(n)            | O(1)             | 
| Merge sort        | O(n log(n))      | O(n log(n))       | O(n log(n))     | O(n)             |
| Quick sort        | O(n<sup>2</sup>) | O(n log(n))       | O(n log(n))     | O(n)             |  
| Heap sort         | O(n log(n))      | O(n log(n))       | O(n log(n))     | O(1)             | 

<br>

## Linked Lists

A linked list data structure includes a series of connected nodes. Here, each node store the data and the address of the next node.

<img src="Images/linked list intro.png" alt="linked list">

#### Why we use Linked List in Data Structure?

There are disadvantages with arrays that cause to use linked lists instead

1. Fixed Size

* The size of the array is fixed and needs to be pre-defined
	* Example – int a[10]; or int a[ ] = {1, 2, 3, 4, 5}
	* We can’t declare an array without declaring the size

2. Memory wastage (Not Optimised)

* If you declare an array of size 10 and just assign values to first two elements
* The memory is allocated to all of them even though, we may not end up using them.

3. Need for Contiguous Memory

* Arrays need Contiguous memory, which some times is bad.
	* Example – Consider there are only three memories of size 10, 10 and 400
	* We need to store an array of size 15
	* In this case, the array will use memory location is size 400 and not combine memory A and B of size 10 and 10 respectively.
	* Thus wasting a lot of memory

4. Inserting in Array is expensive

* Let us say you have an array a[] = {10, 20, 40, 60, 80} and we need to add 50 in a same sorted format.
* Then, we have to move all elements after 40 to one additional position
* Also, same goes for deletion if we want to delete 20. Then all elements after it have to be moved to one position in the opposite direction.

#### Advantages of linked lists

* Insertion and Deletions are easier and efficient.
* Efficient memory allocation i.e no need to pre-allocate memory..
* Many complex applications can be easily carried out with linked lists.
* During run time they grow and shrink.

#### Disdavantages of linked lists

* Uses more memory than arrays because of the storage used by their pointers.
* Reversing traversing a linked list is a complicated task.
* Linked lists only allow sequential access.

<br>

### Singly linked list

In a Singly linked list node, it only contains the address of the next node and not the previous node, so we can only traverse in one direction only. 

##### Structure of linked list

``` markdown

struct node
{
  int data;
  struct node *next;
};

```
<br>


**Create linked list Pseudocode**

``` markdown

Begin procedure append (Node *&head)
	
	Node *temp = new Node
	print "input value to append"
	Input(temp -> val)
	temp -> next = null

	if (head == null) then
		head = temp 
	else
		Node *current = head 

		while(current -> next <> null)
			current = (current -> next)
		end while

		current -> next = temp
	end if 

End procedure append


```

<br>

**Insert elements at the beginning in linked list**

Steps

* Allocate memory for new node
* Store data
* Change next of new node to point to head
* Change head to point to recently created node

``` markdown

Begin procedure addFront (Node *&head)

	Node *temp = new Node
	print "Input a value"
	input (temp -> val)
	temp -> next = null
	temp -> next = head 
	head = temp 

End procedure addFront


```

<br>

**Insert elements at the end in linked list**

Steps

* Allocate memory for new node
* Store data
* Traverse to last node
* Change next of last node to recently created node

``` markdown
Begin procedure addEnd (Node *&head)

	Node *temp = new Node 
	print "input a value"
	input (temp -> val)
	temp -> next = null 

	if(head == null) then
		head = temp
	else 
		Node *current = head 

	while(current -> next <> null)
		current = current -> next 
	end while
    
    current -> next = temp 
    end if 

End procedure addEnd

```

<br>

**Insert elements after particular node in linked list**

``` markdown

Begin procedure addNode (node *&head, int loc)

	node *temp = new node
	print "input a value"
	input (temp -> val)
	temp -> next = null 

	if(loc == 0) then 
		temp -> next = head 
		head = temp 

	else 
		node *current = head 

		for(int i=loc, i>1, i--)
			current = current -> next 
		endfor

		if(current -> next == null) then
			current -> next = temp 
		else 
			temp -> next = current -> next 
			current -> next = temp 
		endif 
	endif 

End procedure addNode 


```

<br>

**Delete elements from front**

``` markdown

Begin procedure deleteFront(node *&head)
	node *temp = head 
	head = head -> next 
	delete temp 

End procedure deleteFront

```

<br>

**Delete elements from end**

``` markdown
Begin procedure deleteEnd(node *&head)

	node *temp = null
	int count = 1 
	node *current = head, *previous = null 

	if(head <> null) then 

	   while(current -> next <> null)
	   	previous = current 
	   	current = current -> next 
	   	count ++
	   end while

	   if(count == 1) then 
	   	temp = head 
	   	head = null 
	   	delete temp 

	   else 
	   	temp = current 
	   	previous -> next = null 
	   	delete temp 

	   endif

	endif

End procedure deleteEnd

```

<br>

**Delete element after particular node**

```markdown

Begin procedure deleteNode(node *&head, int loc)

	node *temp = null 

	if(loc == 0) then 
		temp = head 
		head = head -> next 
		delete temp 
	else 
		node *current = head 

		for(int i = loc , i > 1 , i--)
			current = current -> next 
		endfor

		if(current->next->next == null) then
			temp = current -> next 
			current -> next = null 
			delete temp 
		else 
			temp = current -> next
			current -> next = current->next->next
			delete temp 
		endif
	endif

End procedure deleteNode


```

<br>

### Doubly linked list

<img src="Images/doubly linked list intro.png" alt="circular">

<br>

### Circular linked list

<img src="Images/circular linked list intro.png" alt="circular">

<br>

## Stack 

Stack is one of the basic linear Data structure, that we use for storing our data. Data in a stack is stored in a serialized manner. One important thing about using a Stack is that the data first entered in the stack will be at the last of the stack. This is one of the reason why we also called Stack a LIFO Data Structure, i.e; Last in First Out.

<img src="Images/stack intro.png" alt="stack">

<br>

#### Basic terminology of stack 

* Top – This refers to the topmost element of the stack, or in other words the element last entered in the stack.
* Push () – This is one of the operation that we can perform on stack, for inserting data in this data structure.
* Pop () – This operation deals with deleting the data from the stack. It deletes the top-most data from the stack.
* Peek () – This operation helps us in looking at the topmost element of the data without removing it from the stack.


#### Advantages of stack 

* Manages the data in a Last In First Out(LIFO) method which is not possible with Linked list and array.
* A stack is used when a variable is not used outside that function.
* It allows you to control how memory is allocated and deallocated.
* Not easily corrupted
* Variables cannot be resized.

#### Disdavantages of stack 

* Stack memory is very limited.
* Random access is not possible.


<br>

**Initialize stack using array**

``` markdown

structure stack:
    maxsize : integer
    top : integer
    items : array of item 

Begin procedure initialize(stk : stack, size : integer):

    stk.items ← new array of size items, initially empty
    stk.maxsize ← size
    stk.top ← 0

End procedure initialize


```
<br>

**Push operation using array**

``` markdown

Begin procedure push(stk : stack, x : item):
    if stk.top = stk.maxsize:
        report overflow error
    else:
        stk.items[stk.top] ← x
        stk.top ← stk.top + 1
    endif

End procedure push

```
<br>

**Pop operation using array**

```markdown

Begin procedure pop(stk : stack):
    if stk.top = 0:
        report underflow error    
    else:    
        stk.top ← stk.top − 1
        r ← stk.items[stk.top]
        return r   
    endif
End procedure pop

```

<br>
<hr>

**Initialize using linked list**

``` markdown

structure frame:
    data : item
    next : frame or nil

structure stack:
    head : frame or nil
    size : integer

Begin procedure initialize(stk : stack):
    stk.head ← nil
    stk.size ← 0
End procedure initialize

```

<br>

**Push operation using linked list**

``` markdown

Begin procedure push(stk : stack, x : item):
    
    newhead ← new frame
    newhead.data ← x
    newhead.next ← stk.head
    stk.head ← newhead
    stk.size ← stk.size + 1

End procedure push

```

<br>

**Pop operation using linked list**

```markdown

Begin procedure pop(stk : stack):
    
    if stk.head = nil:
        report underflow error
    else 
	    r ← stk.head.data
	    stk.head ← stk.head.next
	    stk.size ← stk.size - 1
	    return r
	endif

End procedure pop 
```