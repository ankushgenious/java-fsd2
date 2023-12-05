# java-fsd4

# practice project : 1

package practice;

public class LinearSearch {

    public static int linearSearch(int[] arr, int target) {
        // Iterate through the array
        for (int i = 0; i < arr.length; i++) {
            // Check if the current element is equal to the target
            if (arr[i] == target) {
                // Return the index if found
                return i;
            }
        }
        // Return -1 if the target is not found
        return -1;
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {5, 2, 9, 1, 5, 6};
        int targetValue = 9;

        // Perform linear search
        int index = linearSearch(array, targetValue);

        // Display the result
        if (index != -1) {
            System.out.println("Element " + targetValue + " found at index " + index);
        } else {
            System.out.println("Element " + targetValue + " not found in the array");
        }
    }
}



# practice project : 2

public class BinarySearch {

    public static int binarySearch(int[] arr, int target) {
        int low = 0;
        int high = arr.length - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            // Check if the target is equal to the middle element
            if (arr[mid] == target) {
                return mid;
            }

            // If the target is less than the middle element, search in the left half
            if (arr[mid] > target) {
                high = mid - 1;
            }

            // If the target is greater than the middle element, search in the right half
            else {
                low = mid + 1;
            }
        }

        // Return -1 if the target is not found
        return -1;
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {1, 2, 5, 6, 9, 12, 15};
        int targetValue = 6;

        // Perform binary search
        int index = binarySearch(array, targetValue);

        // Display the result
        if (index != -1) {
            System.out.println("Element " + targetValue + " found at index " + index);
        } else {
            System.out.println("Element " + targetValue + " not found in the array");
        }
    }
}



# practice project : 3

package Practice;

public class ExponentialSearch {

    // Standard binary search algorithm
    private static int binarySearch(int[] arr, int target, int low, int high) {
        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == target) {
                return mid;
            } else if (arr[mid] > target) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }

        return -1; // Return -1 if the target is not found
    }

    // Exponential search algorithm
    public static int exponentialSearch(int[] arr, int target) {
        int n = arr.length;
        
        // If the target is the first element
        if (arr[0] == target) {
            return 0;
        }

        // Find the range for binary search by doubling the index
        int i = 1;
        while (i < n && arr[i] <= target) {
            i *= 2;
        }

        // Perform binary search in the found range
        return binarySearch(arr, target, i / 2, Math.min(i, n - 1));
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        int targetValue = 6;

        // Perform exponential search
        int index = exponentialSearch(array, targetValue);

        // Display the result
        if (index != -1) {
            System.out.println("Element " + targetValue + " found at index " + index);
        } else {
            System.out.println("Element " + targetValue + " not found in the array");
        }
    }
}

# practice project : 4

package Practice;

public class SelectionSort {

    public static void selectionSort(int[] arr) {
        int n = arr.length;

        // Traverse through all array elements
        for (int i = 0; i < n - 1; i++) {
            // Find the minimum element in the unsorted part of the array
            int minIndex = i;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[minIndex]) {
                    minIndex = j;
                }
            }

            // Swap the found minimum element with the first element
            int temp = arr[minIndex];
            arr[minIndex] = arr[i];
            arr[i] = temp;
        }
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {64, 25, 12, 22, 11};
        
        // Perform selection sort
        selectionSort(array);

        // Display the sorted array
        System.out.println("Sorted array:");
        for (int value : array) {
            System.out.print(value + " ");
        }
    }
}

# practice project : 5

package Practice;

public class BubbleSort {

    public static void bubbleSort(int[] arr) {
        int n = arr.length;

        // Traverse through all array elements
        for (int i = 0; i < n - 1; i++) {
            // Last i elements are already in place, so no need to check them
            for (int j = 0; j < n - i - 1; j++) {
                // Swap if the element found is greater than the next element
                if (arr[j] > arr[j + 1]) {
                    // Swap arr[j] and arr[j+1]
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {64, 34, 25, 12, 22, 11, 90};
        
        // Perform bubble sort
        bubbleSort(array);

        // Display the sorted array
        System.out.println("Sorted array:");
        for (int value : array) {
            System.out.print(value + " ");
        }
    }
}

# practice project : 6

public class InsertionSort {

    public static void insertionSort(int[] arr) {
        int n = arr.length;

        // Traverse through all array elements starting from the second element
        for (int i = 1; i < n; i++) {
            // Get the current element to be compared
            int key = arr[i];

            // Move elements of arr[0..i-1] that are greater than key to one position ahead of their current position
            int j = i - 1;
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }

            // Place the current element at its correct position
            arr[j + 1] = key;
        }
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {12, 11, 13, 5, 6};
        
        // Perform insertion sort
        insertionSort(array);

        // Display the sorted array
        System.out.println("Sorted array:");
        for (int value : array) {
            System.out.print(value + " ");
        }
    }
}


# practice project : 7

public class MergeSort {

    public static void mergeSort(int[] arr) {
        int n = arr.length;

        if (n > 1) {
            // Find the middle index of the array
            int mid = n / 2;

            // Create left and right subarrays
            int[] left = new int[mid];
            int[] right = new int[n - mid];

            // Copy data to left and right subarrays
            System.arraycopy(arr, 0, left, 0, mid);
            System.arraycopy(arr, mid, right, 0, n - mid);

            // Recursively sort the two halves
            mergeSort(left);
            mergeSort(right);

            // Merge the sorted halves
            merge(arr, left, right);
        }
    }

    private static void merge(int[] arr, int[] left, int[] right) {
        int i = 0, j = 0, k = 0;

        // Merge elements back into the main array in sorted order
        while (i < left.length && j < right.length) {
            if (left[i] <= right[j]) {
                arr[k++] = left[i++];
            } else {
                arr[k++] = right[j++];
            }
        }

        // Copy the remaining elements of left and right, if any
        while (i < left.length) {
            arr[k++] = left[i++];
        }

        while (j < right.length) {
            arr[k++] = right[j++];
        }
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {38, 27, 43, 3, 9, 82, 10};
        
        // Perform merge sort
        mergeSort(array);

        // Display the sorted array
        System.out.println("Sorted array:");
        for (int value : array) {
            System.out.print(value + " ");
        }
    }
}



# practice project : 8

public class QuickSort {

    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            // Find the partition index such that elements smaller than the pivot are on the left, and larger on the right
            int partitionIndex = partition(arr, low, high);

            // Recursively sort the sub-arrays
            quickSort(arr, low, partitionIndex - 1);
            quickSort(arr, partitionIndex + 1, high);
        }
    }

    private static int partition(int[] arr, int low, int high) {
        // Choose the rightmost element as the pivot
        int pivot = arr[high];
        int i = low - 1; // Index of smaller element

        // Traverse the array and swap elements smaller than the pivot to the left
        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;
                // Swap arr[i] and arr[j]
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }

        // Swap arr[i+1] and pivot
        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        // Return the partition index
        return i + 1;
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {10, 7, 8, 9, 1, 5};
        int n = array.length;

        // Perform quick sort
        quickSort(array, 0, n - 1);

        // Display the sorted array
        System.out.println("Sorted array:");
        for (int value : array) {
            System.out.print(value + " ");
        }
    }
}
