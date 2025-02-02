# sorting algos 

### - 1 <u> Bubble sort </u>

 - concept -  repeatedly compares adjacent ele and swaps if in wrong order <br>
 - TC - BEST - O(n) WORST - O(n^2) <br>
 - SC -O(1) <br>
 - used in small or nearly sorted array

 ```java
 public static void bubblesort(int arr[]){
    for(int i = 0 ; i < arr.length-1; i++){
        for(int j = 0 ; j < arr.length-i-1; j++){
            if(arr[j]>arr[j+1]){
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }}}
}
```
### - 2 <u> Selection sort </u>

 - concept -  Finds the minimum (or maximum) element in the array and swaps it with the first unsorted element.<br>
 - TC - 𝑂
(𝑛^2)
(always, as it doesn’t optimize for sorted data).
 - SC -O(1) <br>
 - simple but ineffecient for large arrays.
 
 ```java
 public static void selectionsort(int[] arr){
    int n = arr.length;
    for(int i =0 ; i<n-1 ; i++>){
        int minval = i;
        for(int j=i+1; j<n; j++){
            if(arr[j]<arr[minval]){
                minval =j;
            }
        }
        int temp  = arr[minval];
        arr[minval] = arr[i];
        arr[i] = temp ;
    }
 }
 ```
### - 3 <u> Insertion sort </u>

 - concept -Builds the sorted array one element at a time by comparing and inserting elements into the correct position.<br>
 - TC - Best: 
O(n) (if the array is already sorted)
Worst: 
O(n^2)
 - SC -O(1) <br>
 - Efficient for small datasets or arrays that are nearly sorted.

 
 ```java
 public static void selectionsort(int[] arr){
    
    for(int i= 1; i<arr.length ; i++){
        int j= i-1;
        int key = arr[i];
        while(j>=0 && arr[j]>key){
            arr[j+1] = arr[j] ;
            j--;
        }
        arr[j+1] = key;
    }
 }
 ```
### - 4 <u> Merge sort </u>

 - concept -Divides the array into halves, recursively sorts them, and merges the sorted halves.<br>
 - TC -
O(nlogn) (always, regardless of input)
 - SC -
O(n) (due to temporary arrays during merging)<br>
 - Large datasets, stable sort, external sorting (e.g., sorting linked lists).
- it is a recursive algorithm.
 
 ```java
import java.util.*;

class Solution {
    private static void merge(int[] arr, int low, int mid, int high) {
        ArrayList<Integer> temp = new ArrayList<>(); // temporary array
        int left = low;      // starting index of left half of arr
        int right = mid + 1;   // starting index of right half of arr

        //storing elements in the temporary array in a sorted manner//

        while (left <= mid && right <= high) {
            if (arr[left] <= arr[right]) {
                temp.add(arr[left]);
                left++;
            } else {
                temp.add(arr[right]);
                right++;
            }
        }

        // if elements on the left half are still left //

        while (left <= mid) {
            temp.add(arr[left]);
            left++;
        }

        //  if elements on the right half are still left //
        while (right <= high) {
            temp.add(arr[right]);
            right++;
        }

        // transfering all elements from temporary to arr //
        for (int i = low; i <= high; i++) {
            arr[i] = temp.get(i - low);
        }
    }

    public static void mergeSort(int[] arr, int low, int high) {
        if (low >= high) return;
        int mid = (low + high) / 2 ;
        mergeSort(arr, low, mid);  // left half
        mergeSort(arr, mid + 1, high); // right half
        merge(arr, low, mid, high);  // merging sorted halves
    }
}
public class tUf {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        int n = 7;
        int arr[] = { 9, 4, 7, 6, 3, 1, 5 };
        System.out.println("Before sorting array: ");
        for (int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
        Solution.mergeSort(arr, 0, n - 1); // solution.mergeSort is refereing to Solution class
        System.out.println("After sorting array: ");
        for (int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
    }

}
 ```

 ### - 5 <u> Quick sort </u>

 - concept -Builds the sorted array one element at a time by comparing and inserting elements into the correct position.<br>
 - TC - Best/Average: 
O(nlogn)  Worst: 
O(n 
2
 ) (if pivot selection is poor)
 - SC - 
O(logn) (for recursive stack) and wrost is O(n^2)  ///// Auxiliary space is O(1) only <br>
 - Optimizations: Use randomized pivot or median-of-three pivot selection.
<br>Use Case: General-purpose sorting, in-place sorting.
 
 ```java
 public class Main {
    public static void quick(int[] a, int f, int l) {
        int i = f, pivot = f;
        int j = l;
        int temp;
        if (f < l) {
            while (i < j) {
                while (i < j && a[i] <= a[pivot]) i++;
                while (a[j] > a[pivot]) j--;
                if (i < j) {
                    temp = a[i];
                    a[i] = a[j];
                    a[j] = temp;
                }
            }
            temp = a[j];
            a[j] = a[pivot];
            a[pivot] = temp;

            quick(a, f, j - 1);
            quick(a, j + 1, l);
        }
    }

    public static int[] sortArray(int[] nums) {
        quick(nums, 0, nums.length - 1);
        return nums;            <--------------------
    }                                               |
                                                    |
    public static void main(String[] args) {        ^
                                                    |
        int[] nums = {4, 2, 7, 3, 9, 5};            |
                                                    |
        int[] sortedArray = sortArray(nums); >-------
                                                    
        System.out.print("Sorted array: "); 
        for (int num : sortedArray) {
            System.out.print(num + " ");
        }
    }
}

 ```




### - 5 <u> Bucket Sort </u>
 - Concept: Divides the array into multiple buckets, distributes elements into these buckets, sorts each bucket, and concatenates the results.
 - TC:
Best: O(n + k) (if the input is uniformly distributed)
Worst: O(n²) (if all elements fall into one bucket)
- SC: O(n + k) (for additional buckets and auxiliary space)
- Use Case: Efficient for sorting a large number of elements with values uniformly distributed over a known range.
```java

import java.util.*;

public class BucketSort {

    public static void bucketSort(float[] arr) {
        int n = arr.length;
        if (n <= 0) return;

        // Step 1: Create n empty buckets
        ArrayList<Float>[] buckets = new ArrayList[n];
        for (int i = 0; i < n; i++) {
            buckets[i] = new ArrayList<>();
        }

        // Step 2: Distribute elements into buckets
        for (float num : arr) {
            int index = (int) (num * n); // Determine bucket index
            buckets[index].add(num);
        }

        // Step 3: Sort each bucket
        for (ArrayList<Float> bucket : buckets) {
            Collections.sort(bucket);
        }

        // Step 4: Concatenate sorted buckets
        int index = 0;
        for (ArrayList<Float> bucket : buckets) {
            for (float num : bucket) {
                arr[index++] = num;
            }
        }
    }

    public static void main(String[] args) {
        float[] arr = {0.42f, 0.32f, 0.23f, 0.52f, 0.13f};
        System.out.println("Before sorting:");
        for (float num : arr) {
            System.out.print(num + " ");
        }

        bucketSort(arr);

        System.out.println("\nAfter sorting:");
        for (float num : arr) {
            System.out.print(num + " ");
        }
    }
}
```