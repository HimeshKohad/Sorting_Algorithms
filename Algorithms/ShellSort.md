***Shell Sort***

<hr>

The Shell sorting algorithm is derived from [Insertion Sort](https://github.com/HimeshKohad/Sorting_Algorithms/blob/main/Algorithms/InsertionSort.md).

In [Insertion Sort](https://github.com/HimeshKohad/Sorting_Algorithms/blob/main/Algorithms/InsertionSort.md), sometimes, we need to shift large blocks to insert them into the correct position. 
Using Shell Sort, we can avoid large number of shifting. The sorting is done in a particular interval. After every pass, the interval is reduced to make a smaller interval.

Shell sort is a sorting algorithm that is an extension of insertion sort. Shell sort has an improved average time complexity as compared to [Insertion Sort](https://github.com/HimeshKohad/Sorting_Algorithms/blob/main/Algorithms/InsertionSort.md).
As similar to insertion sort, it is a comparison-based and in-place sorting algorithm. Shell sort is efficient for medium-sized data sets.

In [Insertion Sort](https://github.com/HimeshKohad/Sorting_Algorithms/blob/main/Algorithms/InsertionSort.md), at a time, elements can be moved ahead by one position only. 
To move an element to a far-away position, many movements are required that increase the algorithm's execution time. 
But shell sort overcomes this drawback of insertion sort. 
It allows the movement and swapping of far-away elements as well.

This algorithm first sorts the elements that are far away from each other, then it subsequently reduces the gap between them. 
This gap is called as interval. 
This interval can be calculated by using the Knuth's formula given below -

```cpp
hh = h * 3 + 1
where, 'h' is the interval having initial value of 1.
```

<hr>

***Algorithm:***

```cpp
ShellSort(a, n)    // a -> given array, n -> size of the given array

for (interval = n/2; interval > 0; interval /= 2)
for (i = interval; i < n; i += 1) 
  temp a[i]
for (j = i; j >= interval && a[j - interval] > temp; j -= interval)
  a[j] = a[j - interval];
  a[j] = temp;
End ShellSort
```


<hr>

***Working of Shell Sort:***

Now, let's see the working of the shell sort Algorithm.

To understand the working of the shell sort algorithm, let's take an unsorted array.

Let the elements of the array be: [33, 31, 40, 8, 12, 17, 25, 42]

We will use the original sequence of shell sort, i.e., N/2, N/4,....,1 as the intervals.

In the first loop, n is equal to 8 (size of the array), so the elements are lying at the interval of 4 (n/2 = 4). 
Elements will be compared and swapped if they are not in order.

Here, in the first loop, the element at the 0th position will be compared with the element at 4th position. 
If the 0th element is greater, it will be swapped with the element at 4th position. 
Otherwise, it remains the same. This process will continue for the remaining elements.

At the interval of 4, the sublists are {33, 12}, {31, 17}, {40, 25}, {8, 42}.

![image](https://user-images.githubusercontent.com/107066424/210620673-2b059df8-38de-47e8-a8de-a0e000ad0755.png)

Now, we have to compare the values in every sub-list. 
After comparing, we have to swap them if required in the original array. 
After comparing and swapping, the updated array will look as follows - [12, 17, 25, 8, 33, 31, 40, 42]

In the second loop, elements are lying at the interval of 2 (n/4 = 2), where n = 8.

Now, we are taking the interval of 2 to sort the rest of the array. 
With an interval of 2, two sublists will be generated - {12, 25, 33, 40}, and {17, 8, 31, 42}.

![image](https://user-images.githubusercontent.com/107066424/210620740-a3d08cb1-63bf-49f7-adb1-3cfb57d65292.png)

Now, we again have to compare the values in every sub-list. 
After comparing, we have to swap them if required in the original array. 
After comparing and swapping, the updated array will look as follows - [12, 8, 25, 17, 33, 31, 40, 42]

In the third loop, elements are lying at the interval of 1 (n/8 = 1), where n = 8. 
At last, we use the interval of value 1 to sort the rest of the array elements. 
In this step, shell sort uses insertion sort to sort the array elements.

![image](https://user-images.githubusercontent.com/107066424/210620483-8b1ae9d8-b92e-4618-bd95-0c6d6941eb80.png)

Now, the array is sorted in ascending order.

<hr>

_**Complexity of Shell Sort:**_

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(n*logn)|
|Average Case|O(n*logn)|
|Worst Case|O(n^2)|

<br>

_Space Complexity:_ O(1)

<hr>

***Implementation in C++:***

```cpp

#include <iostream>
using namespace std;

int shellSort(int arr[], int n)
{
	for (int gap = n/2; gap > 0; gap /= 2)
	{

		for (int i = gap; i < n; i += 1)
		{
			int temp = arr[i];

			int j;		
			for (j = i; j >= gap && arr[j - gap] > temp; j -= gap)
				arr[j] = arr[j - gap];
			
			arr[j] = temp;
		}
	}
	return 0;
}

void printArray(int arr[], int n)
{
	for (int i=0; i<n; i++)
		cout << arr[i] << " ";
}

int main()
{
	int arr[] = {12, 34, 54, 2, 3}, i;
	int n = sizeof(arr)/sizeof(arr[0]);

	cout << "Array before sorting: \n";
	printArray(arr, n);

	shellSort(arr, n);

	cout << "\nArray after sorting: \n";
	printArray(arr, n);

	return 0;
}
```

<hr>
_**Applications:**_

The applications of Shell Sort include:
* ShellSort performs more operations and has a higher cache miss ratio than [Quick Sort](https://github.com/HimeshKohad/Sorting_Algorithms/blob/main/Algorithms/QuickSort.md).
* Shell sort can also be used as a sub-algorithm of the introspective sort to sort short subarrays and avoid slowdowns when the recursion depth exceeds a certain threshold. 
* However, some versions of the qsort function in the C standard library geared at embedded devices utilize it instead of quicksort because it requires less code and does not use the call stack. The uClibc library, for example, uses Shell sort. The Linux kernel has a Shell Sort implementation for similar reasons.
