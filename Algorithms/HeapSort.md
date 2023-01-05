### ***Heap Sort***

<hr>

Heap sort is a comparison-based sorting technique based on Binary Heap data structure. 

It is similar to the [Selection Sort](https://github.com/HimeshKohad/Sorting_Algorithms/blob/main/Algorithms/SelectionSort.md) where we first find the minimum element and place the minimum element at the beginning. 

Repeat the same process for the remaining elements.

<br>

***Characteristics of Heap Sort:***
- Heap sort is an in-place algorithm
- Its typical implementation is not stable, but can be made stable
- Typically 2-3 times slower than well-implemented [Quick Sort](https://github.com/HimeshKohad/Sorting_Algorithms/blob/main/Algorithms/QuickSort.md). The reason for slowness is a lack of locality of reference.

<hr>

***Advantages of Heap Sort:***
- **Efficiency:**  The time required to perform Heap sort increases logarithmically while other algorithms may grow exponentially slower as the number of items to sort increases. 
 This sorting algorithm is very efficient.
 
- **Memory Usage:** Memory usage is minimal because apart from what is necessary to hold the initial list of items to be sorted, it needs no additional memory space to work

- **Simplicity:**  It is simpler to understand than other equally efficient sorting algorithms because it does not use advanced computer science concepts such as recursion

<hr>

***So how does it work?***

Input -> arr[] = {4, 10, 3, 2 1}

**Build Complete Binary Tree:** Build a complete binary tree from the array.

**Transform into max heap:** After that, the task is to construct a tree from that unsorted array and try to convert it into max heap.

- To transform a heap into a max-heap, the parent node should always be greater than or equal to the child nodes
- Here, in this example, as the parent node 4 is smaller than the child node **10**, thus, swap them to build a max-heap.

Transform it into a max heap image widget

- Now, as seen, 4 as a parent is smaller than the child 5, thus swap both of these again and the resulted heap and array should be like this: &nbsp; {10, 5, 3, 4, 1}

**Perform heap sort:** Remove the maximum element in each step (i.e., move it to the end position and remove that) and then consider the remaining elements and transform it into a max heap.

- Delete the root element (10) from the max heap. In order to delete this node, try to swap it with the last node, i.e. (1). After removing the root element, again heapify it to convert it into max heap.
- Resulted heap and array should look like this: &nbsp; {5, 4, 3, 1, 10}

- Repeat the above steps and it will look like the following: &nbsp; {4, 1, 3, 5, 10}

- Now remove the root (i.e. 3) again and perform heapify. It results in: &nbsp; {3, 1, 4, 5, 10}

- Now when the root is removed once again it is sorted. and the sorted array will be like **arr[] = {1, 3, 4, 5, 10}**.

<hr>

***Complexity of Heap Sort:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(n*logn)|
|Average Case|O(n*logn)|
|Worst Case|O(n*logn)|

<br>

_Space Complexity:_ O(1)

<hr>

***Implementation in C++***

```cpp

#include <iostream>
using namespace std;

void heapify(int arr[], int N, int i)
{

	int largest = i;

	int l = 2 * i + 1;

	int r = 2 * i + 2;

	if (l < N && arr[l] > arr[largest])
		largest = l;

	if (r < N && arr[r] > arr[largest])
		largest = r;

	if (largest != i) {
		swap(arr[i], arr[largest]);

		heapify(arr, N, largest);
	}
}

void heapSort(int arr[], int N)
{

	for (int i = N / 2 - 1; i >= 0; i--)
		heapify(arr, N, i);

	for (int i = N - 1; i > 0; i--) {

		swap(arr[0], arr[i]);

		heapify(arr, i, 0);
	}
}

void printArray(int arr[], int N)
{
	for (int i = 0; i < N; ++i)
		cout << arr[i] << " ";
	cout << "\n";
}

int main()
{
	int arr[] = { 12, 11, 13, 5, 6, 7 };
	int N = sizeof(arr) / sizeof(arr[0]);

	heapSort(arr, N);

	cout << "Sorted array is \n";
	printArray(arr, N);
}
```
