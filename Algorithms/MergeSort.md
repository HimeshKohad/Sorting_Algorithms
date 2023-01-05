### ***Merge Sort***

<hr>

The Merge Sort algorithm is based on the [_'Divide and Conquer'_](https://github.com/HimeshKohad/Sorting_Algos/blob/main/Algorithms/DivideAndConquer.md) approach.
In this algorithm, the array is initially divided in two equal halves and then combined together in a sorted manner.

<hr>

**So how does it work?**

Input -> arr[] = {12, 31, 25, 8, 32, 17, 40, 42}

According to the merge sort algorithm, first divide the array into two equal halves.
Merge sort keeps dividing the array into equal parts until it cannot be divided further.

<hr> 

**_Dividing_**


As there are 8 elements in our input array, so it is divided into two arrays of size 4.

_After dividing the two arrays would be:_  &nbsp;  &nbsp;   {12, 31, 25, 8}  &nbsp;  &nbsp;   {32, 17, 40, 42}

Now, again divide these two arrays into halves. As they are of size 4, so divide them into new arrays of size 2.

_After dividing the arrays would look like:_  &nbsp;  &nbsp;  {12, 31}  &nbsp;  &nbsp;   {25, 8}  &nbsp;  &nbsp;   {32, 17}  &nbsp;  &nbsp;   {40, 42}

Now, again divide these arrays to get the atomic value that cannot be further divided.

_Now the elements would be completely seperated:_  &nbsp;  &nbsp;   {12}  &nbsp;  &nbsp;   {31}  &nbsp;  &nbsp;   {25}  &nbsp;  &nbsp;   {8}  &nbsp;  &nbsp;   {32}  &nbsp;  &nbsp;   {17}  &nbsp;  &nbsp;   {40}  &nbsp;  &nbsp;   {42}

<hr>


***Merging***


Now, we need to combine them in the same way they were seperated.
In combining, first compare the element of each array and then combine them into another array in sorted order.
So, first compare 12 and 31, both are in sorted positions. Then compare 25 and 8, and in the list of two values, put 8 first followed by 25. Then compare 32 and 17, sort them and put 17 first followed by 32. After that, compare 40 and 42, and place them sequentially.

_Merge Step 1:_  &nbsp;  &nbsp;   {12, 31}  &nbsp;  &nbsp;   {8, 25}  &nbsp;  &nbsp;   {17, 32}  &nbsp;  &nbsp;   {40, 42}

In the next iteration of combining, now compare the arrays with two data values and merge them into an array of found values in sorted order.

_Merge Step 2:_  &nbsp;  &nbsp;   {8, 12, 25, 31}  &nbsp;  &nbsp;   {17, 32, 40, 42}

Now, there is a final merging of the arrays. After the final merging of above arrays, the array will look like -

_Merge Final Step:_  &nbsp;  &nbsp;   {8, 12, 17, 25, 31, 32, 40, 42}

Now, the array is completely sorted.

<hr>

***Complexity of Merge Sort:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(n*logn)|
|Average Case|O(n*logn)|
|Worst Case|O(n*logn)|

<br>

_Space Complexity:_ O(n)

<hr>

_**Implementation in C++**_
```cpp
#include <iostream>
using namespace std;

class Solution
{
public:
    void merge(int arr[], int l, int mid, int r)
    {
        int i = l;        // starting index of left half of arr
        int j = mid + 1;  // starting index of right half of arr
        int f = l;        // index used to transfer elements in temporary array
        int temp[100000]; // temporary array

        // storing elements in the temporary array in a sorted manner//

        while (i <= mid && j <= r)
        {
            if (arr[i] < arr[j])
            {
                temp[f] = arr[i];
                i++;
            }
            else
            {
                temp[f] = arr[j];
                j++;
            }
            f++;
        }

        // if elements on the left half are still left //

        if (i > mid)
        {
            while (j <= r)
            {
                temp[f] = arr[j];
                f++;
                j++;
            }
        }
        else
        {
            //  if elements on the right half are still left //
            while (i <= mid)
            {
                temp[f] = arr[i];
                f++;
                i++;
            }
        }

        // transfering all elements from temporary to arr //
        for (int f = l; f <= r; f++)
        {
            arr[f] = temp[f];
        }
    }

    void mergeSort(int arr[], int l, int r)
    {
        if (l < r)
        {
            int mid = (l + r) / 2;
            mergeSort(arr, l, mid);     // left half
            mergeSort(arr, mid + 1, r); // right half
            merge(arr, l, mid, r);      // merging sorted halves
        }
    }
};

int main()
{

    int arr[] = {9, 4, 7, 6, 3, 1, 5};
    int n = 7;

    Solution obj;
    cout << "Before Sorting Array: " << endl;
    for (int i = 0; i < n; i++)
    {
        cout << arr[i] << " ";
    }

    cout << endl;

    obj.mergeSort(arr, 0, n - 1);

    cout << "After Sorting Array: " << endl;
    for (int i = 0; i < n; i++)
    {
        cout << arr[i] << " ";
    }

    return 0;
}
```
