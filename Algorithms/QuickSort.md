***Quick Sort***

<hr>

Like [Merge Sort](https://github.com/HimeshKohad/Sorting_Algos/blob/main/Algorithms/MergeSort.md), Quick Sort is a [_'Divide and Conquer'_](https://github.com/HimeshKohad/Sorting_Algos/blob/main/Algorithms/DivideAndConquer.md) Algorithm. 
It picks an element as a pivot and partitions the array around the picked pivot.
There are multiple versions of quickSort that pick pivot in different ways:

- Always pick the first element as a pivot.
- Always pick the last element as a pivot.
- Pick a random element as a pivot.
- Pick median as a pivot.

The key process in quickSort is a partition(). 
The target of partitions is, given an array and an element x of an array as the pivot, put x at its correct position in a sorted array and put all smaller elements (smaller than x) before x, and put all greater elements (greater than x) after x. 
All this should be done in linear time.

<hr>

***Partition Algorithm:***

There can be many ways to do partition, following pseudo-code adopts the method given in the CLRS book. 
The logic is simple, we start from the leftmost element and keep track of the index of smaller (or equal to) elements as i. 
While traversing, if we find a smaller element, we swap the current element with arr[i]. 
Otherwise, we ignore the current element. 

***Pseudo Code for recursive QuickSort function:***

```cpp
// low  –> Starting index,  high  –> Ending index 

quickSort(arr[], low, high) {

    if (low < high) {

        // pi is partitioning index, arr[pi] is now at right place 

        pi = partition(arr, low, high);

        quickSort(arr, low, pi – 1);  // Before pi

        quickSort(arr, pi + 1, high); // After pi

    }

}
```

<br>

***Pseudo code for partition():*** 

```cpp
// This function takes last element as pivot, places the pivot element at its correct position in sorted array, 
// and places all smaller (smaller than pivot) to left of pivot and all greater elements to right of pivot 

partition (arr[], low, high)
{
    // pivot (Element to be placed at right position)
    pivot = arr[high];  

    i = (low – 1)  // Index of smaller element and indicates the 
    // right position of pivot found so far

    for (j = low; j <= high- 1; j++){

        // If current element is smaller than the pivot
        if (arr[j] < pivot){
            i++;    // increment index of smaller element
            swap arr[i] and arr[j]
        }
    }
    swap arr[i + 1] and arr[high])
    return (i + 1)
}
```

<hr>

***Complexity of Quick Sort:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(n*logn)|
|Average Case|O(n*logn)|
|Worst Case|O(n^2)|

<br>

_Space Complexity:_ O(n*logn)


<hr>

***Implementation in C++***

```cpp
#include <iostream>
using namespace std;

class Solution
{
public:
    void QuickSort(int arr[], int low, int high)
    {
        if (low < high)
        {

            int pivot = partition(arr, low, high);
            QuickSort(arr, low, pivot - 1);
            QuickSort(arr, pivot + 1, high);
        }
    }

    int partition(int arr[], int low, int high)
    {
        int pivot = arr[low];
        int i = low;
        int j = high;

        while (i < j)
        {

            while (arr[i] <= pivot && i <= high - 1)
            {
                i++;
            }

            while (arr[j] > pivot && j >= low)
            {
                j--;
            }

            if (i < j)
                swap(arr[i], arr[j]);
        }

        swap(arr[j], arr[low]);

        return j;
    }
};

void printArray(int arr[], int n)
{
    for (int i = 0; i < n; i++)
    {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main()
{

    int arr[] = {4, 6, 2, 5, 7, 8, 1, 3};
    int n = sizeof(arr) / sizeof(arr[0]);

    Solution obj;

    cout << "Before Quick Sort: " << endl;

    printArray(arr, n);

    obj.QuickSort(arr, 0, n - 1);

    cout << "After Quick Sort: " << endl;

    printArray(arr, n);
    return 0;
}
```
