### ***Divide and Conquer***

<hr>

***Let's learn what is a Divide and Conquer Algorithm?***

So, the divide and conquer technique can be divided into 3 parts:
- _Divide:_ This involves dividing a problem into smaller sub-problems.
- _Conquer:_ Solve the sub-problems by recursive calling until solved.
- _Combine:_ Combine all the sub-problems to get a solution to the whole problem.

<br>

***The following sorting algorithms follow a divide and conquer approach:***
- [Quick Sort:](https://github.com/HimeshKohad/Sorting_Algos/edit/main/Algorithms/QuickSort.md) 
The algorithm picks a pivot element and rearranges the array elements so that all elements smaller than the picked pivot element move to the left side of the pivot, and all greater elements move to the right side. 
Finally, the algorithm recursively sorts the subarrays on the left and right of the pivot element. 

- [Merge Sort:](https://github.com/HimeshKohad/Sorting_Algos/blob/main/Algorithms/MergeSort.md) 
The algorithm divides the array into two halves, recursively sorts them, and finally merges the two sorted halves.

<hr>

***What does not qualify as a Divide and Conquer Algorithm?***

Binary Search is a searching algorithm. In each step, the algorithm compares the input element x with the value of the middle element in the array. 
If the values match, return the index of the middle. Otherwise, if x is less than the middle element, then the algorithm recurs for the left side of the middle element, else recurs for the right side of the middle element. 
Contrary to popular belief, this is not an example of Divide and Conquer because there is only one sub-problem in each step (Divide and conquer requires that there must be two or more sub-problems) and hence this is a case of Decrease and Conquer.

<hr>

***Time Complexity of Divide and Conquer Algorithms:***

 
    T(n) = aT(n/b) + f(n),

    where,
         n = size of input <br> 
         a = number of subproblems in the recursion <br> 
         n/b = size of each subproblem. All subproblems are assumed to have the same size. <br>
         f(n) = cost of the work done outside the recursive call, which includes the cost of dividing the problem and cost of merging the solutions
        
<hr>

***Advantages of Divide and Conquer Algorithm:***

- The difficult problem can be solved easily.
- It divides the entire problem into subproblems thus it can be solved parallelly ensuring multiprocessing
- Efficiently uses cache memory without occupying much space
- Reduces time complexity of the problem

<br>

***Disadvantages of Divide and Conquer Algorithm:***

- It involves recursion which is sometimes slow
- Efficiency depends on the implementation of logic
- It may crash the system if the recursion is performed rigorously
