Bubble sort is one of the simplest and most beginner friendly sorting techniques.
In this algorithm we repeatedly swap the adjacent elements if they are in the wrong order.
This algorithm is not suitable for large data sets as its average and worst-case time complexity is quite high.

So how does it work?
Input -> arr[] = {4, 1, 3, 2 ,5}

First pass: 
- Bubble sort starts with the first two elements of the input array.
- {**4, 1** ,3, 2, 5} -> {**1, 4**, 3, 2, 5} --> Here, we compare the first two elements and swap them as 4 > 1.
- {1, **4, 3**, 2, 5} -> {1, **3, 4**, 2, 5} --> Here, we compare the next two elements and swap them as 4 > 3.
- {1, 3, **4, 2**, 5} -> {1, 3, **2, 4**, 5} --> Since, 4 > 2, the algorithm swaps them.
- Now, since 4 < 5, our algorithm does not swap them.


Second pass:
- Now, on second iteration,
- {**1, 3**, 2, 4, 5} -> {**1, 3**, 2, 4, 5}
- {1, **3, 2**, 4, 5} -> {1, **2, 3**, 4, 5} --> Swap since 3 > 2.
- {1, 2, **3, 4**, 5} -> {1, 2, **3, 4**, 5}
- {1, 2, 3, **4, 5**} -> {1, 2, 3, **4, 5**}

Now we can see that the whole array is sorted, but our algorithm does not know that so it moves for the third pass.

Third pass:
- Next iterations would look something like this:
- {**1, 2**, 3, 4, 5} -> {**1, 2**, 3, 4, 5}
- {1, **2, 3**, 4, 5} -> {1, **2, 3**, 4, 5}
- {1, 2, **3, 4**, 5} -> {1, 2, **3, 4**, 5}
- {1, 2, 3, **4, 5**} -> {1, 2, 3, **4, 5**}

Time complexity: O(n^2)
Space complexity: O(1)


```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {

    for (int i = 0; i < n - 1; i++){
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
            }
        }
    }

    cout << "\nAfter Bubble Sort: " << endl;
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

}

int main() {

    int arr[] = {33, 24, 56, 78, 13, 9, 4};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Before Bubble Sort: " << endl;
    for (int i = 0; i < n; i++){
        cout << arr[i] << " ";
    }

    bubbleSort(arr, n);
}
```
