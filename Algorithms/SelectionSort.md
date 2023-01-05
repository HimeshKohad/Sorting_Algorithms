### ***Selection Sort***

<hr>

The Selection Sort algorithm sorts an array by repeatedly finding the minimum element from the unsorted part and putting it at the beginning.

The algorithm maintains two subarrays in a given array:
- The subarray which is already sorted.
- The remaining subarray which is yet unsorted.

In every iteration of the selection sort, the minimum element from the unsorted subarray is picked and moved to the sorted subarray. 

<hr>

***So how does it work?***

Input -> arr[] = {64, 25, 12, 22, 11}

_First Pass:_
- For the first position in the sorted array, the whole array is traversed from index 0 to 4 sequentially. 
- The first position where 64 is stored presently, after traversing whole array it is clear that 11 is the lowest value.
<br>&nbsp; {**64**, 25, 12, 22, 11}
- Thus, replace 64 with 11. After one iteration 11, which happens to be the least value in the array, tends to appear in the first position of the sorted list.
<br>&nbsp; {**11**, 25, 12, 22, 64}

_Second Pass:_
- For the second position, where 25 is present, again traverse the rest of the array in a sequential manner.
<br>&nbsp; {11, **25**, 12, 22, 64}
- After traversing, we found that 12 is the second lowest value in the array and it should appear at the second place in the array, thus swap these values.
<br>&nbsp; {11, **12**, 25, 22, 64}

_Third Pass:_
- Now, for third place, where 25 is present again traverse the rest of the array and find the third least value present in the array.
<br>&nbsp; {11, 12, **25**, 22, 64}
- While traversing, 22 came out to be the third least value and it should appear at the third place in the array, thus swap 22 with element present at third position.
<br>&nbsp; {11, 12, **22**, 25, 64}

_Fourth Pass:_
- Similarly, for fourth position traverse the rest of the array and find the fourth least element in the array 
- As 25 is the 4th lowest value hence, it will place at the fourth position.
<br>&nbsp; {11, 12, 22, **25**, 64}

_Fifth Pass:_ 
- At last the largest value present in the array automatically get placed at the last position in the array
- The resulted array is the sorted array.
<br>&nbsp; {11, 12, 22, **25**, 64}

<hr>

***Complexity of Selection Sort:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(n^2)|
|Average Case|O(n^2)|
|Worst Case|O(n^2)|

<br>

_Space Complexity:_ O(1) 

<hr>

***Implementation in C++***

```cpp
#include <iostream>
using namespace std;

void selectionSort (int arr[], int n) {

    for (int i = 0; i < n - 1; i++) {
        int min_idx = i;

        for (int j = i + 1; j < n; j++){
            if (arr[j] < arr[min_idx]){
                min_idx = j;
            }
        }
        int temp = arr[min_idx];
        arr[min_idx] = arr[i];
        arr[i] = temp;
    }

    cout << "\nAfter Selection Sort: " << endl;
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
}

int main() {
    int arr[] = {3, 7, 78, 1, 26, 39};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Before Selection Sort" << endl;
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    cout << "\n" ;

    selectionSort(arr, n);

    return 0;
}

```
