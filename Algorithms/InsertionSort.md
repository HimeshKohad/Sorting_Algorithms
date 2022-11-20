***Insertion Sort***

<hr>

Insertion sort is a simple sorting technique. In this algorithm the array is split into sorted and unsorted parts. 
The values from the unsorted part are picked and placed in the correct place in the sorted part.


_Characteristics of Insertion Sort:_
- This algorithm is one of the simplest algorithms with simple implementation.
- Basically, we use insertion sort for small data values as it becomes inefficient for larger data sets.
- Insertion sort is adaptive in nature, i.e. it is appropriate for data sets which are already partially sorted.

<hr>

**So how does it work?**

Input -> arr[] = {12, 11, 13, 5, 6}

_First pass:_
- Initially, the first two elements are compared in Insertion sort.
- Here, 12 is greater than 11 hence they are not in the ascending order and 12 is not at its correct position. Thus, swap 11 and 12.
- {12, 11, 13, 5, 6} -> {11, 12, 13, 5, 6}
- So, for now 11 is stored in a sorted sub-array i.e. {11, 12, 13, 5, 6}

_Second pass:_ 
- Now, move to the next two elements and compare them -> {11, 12, 13, 5, 6}
- Here, 13 is greater than 12, thus both elements seems to be in ascending order, hence, no swapping will occur. 12 also stored in a sorted sub-array along with 11.

_Third pass:_
- Now, two elements are present in the sorted sub-array which are 11 and 12.
- Moving forward to the next two elements which are 13 and 5 -> {11, 12, 13, 5, 6}
- Both 5 and 13 are not present at their correct place so swap them -> {11, 12, 5, 13, 6}
- After swapping, elements 12 and 5 are not sorted, thus swap again -> {11, 5, 12, 13, 6}
- Here, again 11 and 5 are not sorted, hence swap again -> {5, 11, 12, 13, 6}

_Fourth pass:_
- Now, the elements which are present in the sorted sub-array are 5, 11 and 12.
- Moving to the next two elements 13 and 6 -> {5, 11, 12, 13, 6}
- Clearly, they are not sorted, thus perform swap between both -> {5, 11, 12, 6, 13}
- Now, 6 is smaller than 12, hence, swap again -> {5, 11, 6, 12, 13}
- Here, also swapping makes 11 and 6 unsorted hence, swap again -> {5, 6, 11, 12, 13}
- Finally, the array is completely sorted.

<hr>

**Insertion Sort Algorithm:**

To sort an array of size N in ascending order: 

- Iterate from arr[1] to arr[N] over the array. 
- Compare the current element (key) to its predecessor. 
- If the key element is smaller than its predecessor, compare it to the elements before. Move the greater elements one position up to make space for the swapped element.

<hr>

***Complexity of Insertion Sort:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(n)|
|Average Case|O(n^2)|
|Worst Case|O(n^2)|

<br>

_Space Complexity:_ O(1)

<hr>

_**Implementation in C++**_
```cpp
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {

    for (int i = 0; i < n; i++) {
        int curr = arr[i];
        int j = i - 1;

        while (j >= 0 && arr[j] > curr) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = curr;
    }

    cout << "\nAfter Insertion Sort: " << endl;
    for (int i = 0; i < n; i++){
        cout << arr[i] << " ";
    }
}

int main() {

    int arr[] = {33, 44, 76, 9, 14, 3, 96};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Before Insertion Sort: " << endl;
    for (int i = 0; i < n; i++){
        cout << arr[i] << " ";
    }

    insertionSort(arr, n);
    return 0;
}
```
