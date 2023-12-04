# java-fsd3

# practice project : 1

package Practice;

public class RightRotateArray {

    public static void main(String[] args) {
        // Example array
        int[] array = {1, 2, 3, 4, 5, 6, 7, 8, 9};

                         
        int steps = 5;    // Number of steps to right rotate

       
        System.out.println("Original Array:");
        
        printArray(array);   // Display the original array

        
        rightRotateArray(array, steps);   // Right rotate the array by 5 steps

        
        System.out.println("\nArray after right rotation by " + steps + " steps:");
        
        printArray(array);  //Rotated Array
    }

    
    private static void rightRotateArray(int[] arr, int steps) {
        int length = arr.length;
        
        steps = steps % length; // Handle cases where steps are greater than array length

       
        int[] temp = new int[length];

        
        System.arraycopy(arr, length - steps, temp, 0, steps);  // Copy the last 'steps' elements to temp array

        
        System.arraycopy(arr, 0, arr, steps, length - steps);  // Shift the remaining elements to the right

        
        System.arraycopy(temp, 0, arr, 0, steps);  // Copy the rotated elements back to the original array
    }
    

    
    private static void printArray(int[] arr) {
        for (int value : arr) {
            System.out.print(value + " ");
        }
        System.out.println();
    }
}



# practice project : 2

package Practice;

import java.util.Arrays;

public class OrderStatisticsKthSmallest {

	public static void main(String[] args) {
		int[] arr = {4 , 21 , 23, 18, 10, 24, 35, 14, 5, 9};
		
		int k=4;
		
		int n =arr.length;
		
		System.out.println("Given array: "+ Arrays.toString(arr));
		
		int result = findKtheSmallest(arr,k);
		
		System.out.println(k+"th smallest : "+result);

	}

	private static int findKtheSmallest(int[] arr, int k) {
		
		if(arr==null || arr.length<k) {
			throw new IllegalArgumentException("Invalid input");
		};
		
		
		return quickSelect(arr, 0, arr.length-1,k-1);
	}

	private static int quickSelect(int[] arr, int left, int right, int k) {
		
		// Base case
		if(left==right)
			return arr[left];
		
		// The partition has more than 1 elements
		// so we have to repeat the partitioning process.
		
		int pivotIndex = partition(arr,left,right);
		
		if(pivotIndex==k)
			return arr[pivotIndex];
		
		if(pivotIndex < k)
			return quickSelect(arr,pivotIndex+1,right,k);
		else
			return quickSelect(arr,left,pivotIndex-1,k);
		
	}

	private static int partition(int[] arr, int left, int right) {
		int pivotValue=arr[right];
		int pivotIndex =left; 
		
		
		for(int i=left; i<right; i++) {
			
			if (arr[i] < pivotValue) {
				swap(arr, i , pivotIndex);
				pivotIndex++;
			}
			
		};
		
		swap(arr,pivotIndex, right );
		
		return pivotIndex;		
	}

	private static void swap(int[] arr, int i, int j) {
		int temp = arr[i];
		 arr[i] =  arr[j];
		 arr[j] =  temp;	
		
	}
	
	
	
	

}



# practice project : 3

package Practice;

import java.util.Scanner;

public class SumInRange {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input the size of the array
        System.out.print("Enter the size of the array: ");
        int n = scanner.nextInt();

        // Input the elements of the array
        int[] array = new int[n];
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < n; i++) {
            System.out.print("Element " + i + ": ");
            array[i] = scanner.nextInt();
        }

        // Input the range [L, R]
        System.out.print("Enter the value of L (0 <= L <= R <= n-1): ");
        int L = scanner.nextInt();
        System.out.print("Enter the value of R (0 <= L <= R <= n-1): ");
        int R = scanner.nextInt();

        // Calculate and display the sum of elements in the range [L, R]
        int sum = calculateSumInRange(array, L, R);
        System.out.println("Sum of elements in the range [" + L + ", " + R + "]: " + sum);

        scanner.close();
    }

    // Function to calculate the sum of elements in the range [L, R]
    private static int calculateSumInRange(int[] arr, int L, int R) {
        if (L < 0 || R >= arr.length || L > R) {
            // Check for invalid range
            System.out.println("Invalid range.");
            return -1; // Return a value indicating an error or absence of a result
        }

        int sum = 0;
        for (int i = L; i <= R; i++) {
            sum += arr[i];
        }
        return sum;
    }
}


# practice project : 3

package Practice;

import java.util.Scanner;

public class SumInRange {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input the size of the array
        System.out.print("Enter the size of the array: ");
        int n = scanner.nextInt();

        // Input the elements of the array
        int[] array = new int[n];
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < n; i++) {
            System.out.print("Element " + i + ": ");
            array[i] = scanner.nextInt();
        }

        // Input the range [L, R]
        System.out.print("Enter the value of L (0 <= L <= R <= n-1): ");
        int L = scanner.nextInt();
        System.out.print("Enter the value of R (0 <= L <= R <= n-1): ");
        int R = scanner.nextInt();

        // Calculate and display the sum of elements in the range [L, R]
        int sum = calculateSumInRange(array, L, R);
        System.out.println("Sum of elements in the range [" + L + ", " + R + "]: " + sum);

        scanner.close();
    }

    // Function to calculate the sum of elements in the range [L, R]
    private static int calculateSumInRange(int[] arr, int L, int R) {
        if (L < 0 || R >= arr.length || L > R) {
            // Check for invalid range
            System.out.println("Invalid range.");
            return -1; // Return a value indicating an error or absence of a result
        }

        int sum = 0;
        for (int i = L; i <= R; i++) {
            sum += arr[i];
        }
        return sum;
    }
}

# practice project : 4

package Practice;

import java.util.Scanner;

public class MatrixMultiplication {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input the dimensions of the first matrix
        System.out.print("Enter the number of rows for the first matrix: ");
        int rows1 = scanner.nextInt();
        System.out.print("Enter the number of columns for the first matrix: ");
        int cols1 = scanner.nextInt();

        // Input the elements of the first matrix
        int[][] matrix1 = inputMatrix(scanner, rows1, cols1);

        // Input the dimensions of the second matrix
        System.out.print("Enter the number of rows for the second matrix: ");
        int rows2 = scanner.nextInt();
        System.out.print("Enter the number of columns for the second matrix: ");
        int cols2 = scanner.nextInt();

        // Input the elements of the second matrix
        int[][] matrix2 = inputMatrix(scanner, rows2, cols2);

        // Perform matrix multiplication
        int[][] resultMatrix = multiplyMatrices(matrix1, matrix2);

        // Display the result matrix
        System.out.println("\nResultant Matrix after multiplication:");
        printMatrix(resultMatrix);

        scanner.close();
    }

    // Function to input elements of a matrix
    private static int[][] inputMatrix(Scanner scanner, int rows, int cols) {
        System.out.println("Enter the elements of the matrix:");
        int[][] matrix = new int[rows][cols];
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                System.out.print("Element [" + i + "][" + j + "]: ");
                matrix[i][j] = scanner.nextInt();
            }
        }
        return matrix;
    }

    // Function to multiply two matrices
    private static int[][] multiplyMatrices(int[][] matrix1, int[][] matrix2) {
        int rows1 = matrix1.length;
        int cols1 = matrix1[0].length;
        int rows2 = matrix2.length;
        int cols2 = matrix2[0].length;

        // Check if matrices are compatible for multiplication
        if (cols1 != rows2) {
            System.out.println("Matrices are not compatible for multiplication.");
            return null;
        }

        // Create the result matrix
        int[][] resultMatrix = new int[rows1][cols2];

        // Perform matrix multiplication
        for (int i = 0; i < rows1; i++) {
            for (int j = 0; j < cols2; j++) {
                for (int k = 0; k < cols1; k++) {
                    resultMatrix[i][j] += matrix1[i][k] * matrix2[k][j];
                }
            }
        }

        return resultMatrix;
    }

    // Function to print a matrix
    private static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int value : row) {
                System.out.print(value + " ");
            }
            System.out.println();
        }
    }
}

# practice project : 5

class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class LinkedList {
    Node head;

    // Method to insert a new node at the end of the linked list
    void append(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }

        Node last = head;
        while (last.next != null) {
            last = last.next;
        }

        last.next = newNode;
    }

    // Method to delete the first occurrence of a key in the linked list
    void deleteNode(int key) {
        Node current = head;
        Node prev = null;

        // If the key is found at the head
        if (current != null && current.data == key) {
            head = current.next;
            return;
        }

        // Search for the key and keep track of the previous node
        while (current != null && current.data != key) {
            prev = current;
            current = current.next;
        }

        // If the key is not present
        if (current == null) {
            System.out.println("Key not found in the linked list.");
            return;
        }

        // Remove the node with the key
        prev.next = current.next;
    }

    // Method to print the linked list
    void printList() {
        Node current = head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }
}

public class DeleteNodeInLinkedList {
    public static void main(String[] args) {
        LinkedList linkedList = new LinkedList();

        // Insert elements into the linked list
        linkedList.append(1);
        linkedList.append(2);
        linkedList.append(3);
        linkedList.append(4);
        linkedList.append(5);

        System.out.println("Original Linked List:");
        linkedList.printList();

        // Delete the first occurrence of a key (e.g., 3)
        linkedList.deleteNode(3);

        System.out.println("Linked List after deleting the first occurrence of 3:");
        linkedList.printList();
    }
}


# practice project : 6

class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class CircularLinkedList {
    Node head;

    // Method to insert a new node into a sorted circular linked list
    void insertSorted(int newData) {
        Node newNode = new Node(newData);

        // If the list is empty, insert the new node and make it circular
        if (head == null) {
            head = newNode;
            head.next = head;
            return;
        }

        // If the new node's data is less than the head's data, insert at the beginning
        if (newData < head.data) {
            newNode.next = head;
            Node last = getLastNode();
            last.next = newNode;
            head = newNode;
            return;
        }

        // Find the node after which the new node should be inserted
        Node current = head;
        while (current.next != head && current.next.data < newData) {
            current = current.next;
        }

        // Insert the new node
        newNode.next = current.next;
        current.next = newNode;
    }

    // Method to get the last node of the circular linked list
    private Node getLastNode() {
        Node last = head;
        while (last.next != head) {
            last = last.next;
        }
        return last;
    }

    // Method to print the circular linked list
    void printList() {
        if (head == null) {
            System.out.println("Circular linked list is empty.");
            return;
        }

        Node current = head;
        do {
            System.out.print(current.data + " ");
            current = current.next;
        } while (current != head);

        System.out.println();
    }
}

public class InsertSortedCircularLinkedList {
    public static void main(String[] args) {
        CircularLinkedList circularList = new CircularLinkedList();

        // Insert elements into the sorted circular linked list
        circularList.insertSorted(3);
        circularList.insertSorted(5);
        circularList.insertSorted(8);
        circularList.insertSorted(10);

        System.out.println("Original Sorted Circular Linked List:");
        circularList.printList();

        // Insert a new element (e.g., 7) into the sorted circular linked list
        circularList.insertSorted(7);

        System.out.println("Sorted Circular Linked List after inserting 7:");
        circularList.printList();
    }
}



# practice project : 7

class Node {
    int data;
    Node next;
    Node prev;

    public Node(int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

class DoublyLinkedList {
    Node head;

    // Method to insert a new node at the end of the doubly linked list
    void append(int data) {
        Node newNode = new Node(data);

        if (head == null) {
            head = newNode;
            return;
        }

        Node last = head;
        while (last.next != null) {
            last = last.next;
        }

        last.next = newNode;
        newNode.prev = last;
    }

    // Method to traverse the doubly linked list in forward direction
    void traverseForward() {
        if (head == null) {
            System.out.println("Doubly linked list is empty.");
            return;
        }

        Node current = head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }

    // Method to traverse the doubly linked list in backward direction
    void traverseBackward() {
        if (head == null) {
            System.out.println("Doubly linked list is empty.");
            return;
        }

        Node last = head;
        while (last.next != null) {
            last = last.next;
        }

        while (last != null) {
            System.out.print(last.data + " ");
            last = last.prev;
        }
        System.out.println();
    }
}

public class DoublyLinkedListTraversal {
    public static void main(String[] args) {
        DoublyLinkedList doublyList = new DoublyLinkedList();

        // Insert elements into the doubly linked list
        doublyList.append(1);
        doublyList.append(2);
        doublyList.append(3);
        doublyList.append(4);
        doublyList.append(5);

        System.out.println("Doubly Linked List in Forward Direction:");
        doublyList.traverseForward();

        System.out.println("Doubly Linked List in Backward Direction:");
        doublyList.traverseBackward();
    }
}


# practice project 8

import java.util.Stack;

public class StackExample {

    public static void main(String[] args) {
        // Create a stack
        Stack<Integer> stack = new Stack<>();

        // Insert elements into the stack (push)
        System.out.println("Pushing elements onto the stack:");
        stack.push(10);
        stack.push(20);
        stack.push(30);
        stack.push(40);

        // Display the stack
        displayStack(stack);

        // Remove elements from the stack (pop)
        System.out.println("\nPopping elements from the stack:");
        int poppedElement = stack.pop();
        System.out.println("Popped Element: " + poppedElement);

        // Display the stack after popping
        displayStack(stack);
    }

    // Method to display the elements of the stack
    private static void displayStack(Stack<Integer> stack) {
        if (stack.isEmpty()) {
            System.out.println("Stack is empty.");
            return;
        }

        System.out.println("Stack Elements (Top to Bottom): " + stack);
    }
}

# practice project 9

import java.util.Stack;

public class StackExample {

    public static void main(String[] args) {
        // Create a stack
        Stack<Integer> stack = new Stack<>();

        // Insert elements into the stack (push)
        System.out.println("Pushing elements onto the stack:");
        stack.push(10);
        stack.push(20);
        stack.push(30);
        stack.push(40);

        // Display the stack
        displayStack(stack);

        // Remove elements from the stack (pop)
        System.out.println("\nPopping elements from the stack:");
        int poppedElement = stack.pop();
        System.out.println("Popped Element: " + poppedElement);

        // Display the stack after popping
        displayStack(stack);
    }

    // Method to display the elements of the stack
    private static void displayStack(Stack<Integer> stack) {
        if (stack.isEmpty()) {
            System.out.println("Stack is empty.");
            return;
        }

        System.out.println("Stack Elements (Top to Bottom): " + stack);
    }
}




