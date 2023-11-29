# java-fsd2

# practice project 1

package Practice;

	class Thread1 implements Runnable{
		Thread t; //REFERENCE CLASS
		
		Thread1(){
			
			t = new Thread(this,"T2");
			System.out.println("Thread Running"+t);
			t.start();
		}
		
		public void run() {
			for(int i =1;i<6;i++) {
				
				try {
				System.out.println(i);
				Thread.sleep(2000); // sleeps for two second
			
					}
				catch(InterruptedException e){
					System.out.println("ThreadInterrupted");
				}
			}
		}
		}
	public class MyThread{
			
		
		public static void main(String args[]) {
			
			new Thread1();
		}
		
	

}




# Practice Project 2


package Practice;


class MyThread2{

private static Object LOCK = new Object();

public static void main(String[] args) 
throws InterruptedException {

	java.lang.Thread.sleep(1000);

 System.out.println("Thread '" +java.lang.Thread.currentThread().getName() +
   "' is woken after sleeping for 1 second");

 synchronized (LOCK) 
 {
     LOCK.wait(1000);
    
     System.out.println("Object '" + LOCK + "' is woken after" +
       " waiting for 1 second");
 }
}
}





# practice project 3


package Practice;

import java.io.*;
import java.util.*;
 
// A Class used to send a message
class Sender {
    public void send(String msg)
    {
        System.out.println("Sending\t" + msg);
        try {
        	java.lang.Thread.sleep(1000);
        }
        catch (Exception e) {
            System.out.println("Thread  interrupted.");
        }
        System.out.println("\n" + msg + "Sent");
    }
}
 
// Class for send a message using Threads
class ThreadedSend extends Thread {
    private String msg;
    Sender sender;
 
    // Receives a message object and a string
    // message to be sent
    ThreadedSend(String m, Sender obj)
    {
        msg = m;
        sender = obj;
    }
 
    public void run()
    {
        // Only one thread can send a message
        // at a time.
        synchronized (sender)
        {
            // synchronizing the send object
            sender.send(msg);
        }
    }
}
 
// Driver class
class Synchronization {
    public static void main(String args[])
    {
        Sender send = new Sender();
        ThreadedSend S1 = new ThreadedSend(" Hi ", send);
        ThreadedSend S2 = new ThreadedSend(" Bye ", send);
 
        // Start two threads of ThreadedSend type
        S1.start();
        S2.start();
        
       
       
 
        // wait for threads to end
        try {
            S1.join();
            S2.join();
        }
        catch (Exception e) {
            System.out.println("Interrupted");
        }
    }
}




# practice project 4


package Practice;


class ThrowExcep {
 static void help()
 {
     try {
         throw new NullPointerException("error_unknown");
     }
     catch (NullPointerException e) {
         System.out.println("Caught inside help().");
         
         // rethrowing the exception
         throw e;
     }
 }

 public static void main(String args[])
 {
     try {
         help();
     }
     catch (NullPointerException e) {
         System.out.println(
             "Caught in main error name given below:");
         System.out.println(e);
     }
 }
}


# practice project 5

//THROW 


package Practice;

class Test
{
  static void avg()
  {
    try
    {
      throw new ArithmeticException("demo");
    }
    catch(ArithmeticException e)
    {
      System.out.println("Exception caught");
    }
 }

 public static void main(String args[])
 {
    avg();
 }
}


//THROWS KEYWORD



package Practice;

class Test
{
  static void check() throws ArithmeticException
  {  
    System.out.println("Inside check function");
    throw new ArithmeticException("demo");
  }

  public static void main(String args[])
  {
    try
    {
      check();
    }
    catch(ArithmeticException e)
    {
      System.out.println("caught" + e);
    }
  }
}



//FINALLY BLOCK EXCEPTION

package Practice;

class Test

{
  public static void main(String[] args)
  {
    int a[] = new int[2];
    System.out.println("out of try");
    try
    {
      System.out.println("Access invalid element"+ a[3]);
      /* the above statement will throw ArrayIndexOutOfBoundException */
    }
    finally
    {
      System.out.println("finally is always executed.");
    }
  }
}



# Practice project 6


package Practice;

import java.util.InputMismatchException;
import java.util.Scanner;

public class ExceptionHandelling {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        try {
            // Get input from the user
            System.out.print("Enter numerator: ");
            int numerator = scanner.nextInt();

            System.out.print("Enter denominator: ");
            int denominator = scanner.nextInt();

            // Perform division
            double result = divide(numerator, denominator);

            // Display the result
            System.out.println("Result of division: " + result);

        } catch (InputMismatchException e) {
            // Handle non-numeric input
            System.out.println("Invalid input. Please enter numeric values.");

        } catch (ArithmeticException e) {
            // Handle division by zero
            System.out.println("Error: Division by zero is not allowed.");

        } finally {
            // Close the scanner to prevent resource leak
            scanner.close();
        }
    }

    // Method to perform division
    private static double divide(int numerator, int denominator) {
        if (denominator == 0) {
            // Throw an ArithmeticException if the denominator is zero
            throw new ArithmeticException("Division by zero is not allowed.");
        }
        return (double) numerator / denominator;
    }
}


# practice project 7

package Practice;

import java.nio.file.*;
import java.io.*;
import java.util.List;
import java.util.Scanner;

public class FileCRUDOperation {

    public static void main(String[] args) {
        // Specify the file path
        String filePath = "example.txt";

        // Create a file
        createFile(filePath);

        // Read from the file
        readFile(filePath);

        // Update the file
        updateFile(filePath);

        // Read from the updated file
        readFile(filePath);

        // Delete the file
        deleteFile(filePath);
    }

    // Create a new file
    private static void createFile(String filePath) {
        try {
            Files.createFile(Paths.get(filePath));
            System.out.println("File created: " + filePath);
        } catch (IOException e) {
            System.out.println("Error creating file: " + e.getMessage());
        }
    }

    // Read content from a file
    private static void readFile(String filePath) {
        try {
            List<String> lines = Files.readAllLines(Paths.get(filePath));
            System.out.println("File content:");
            for (String line : lines) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.out.println("Error reading file: " + e.getMessage());
        }
    }

    // Update content in a file
    private static void updateFile(String filePath) {
        try {
            // Get user input for the new content
            Scanner scanner = new Scanner(System.in);
            System.out.print("Enter new content: ");
            String newContent = scanner.nextLine();

            // Write the new content to the file
            Files.write(Paths.get(filePath), newContent.getBytes(), StandardOpenOption.APPEND);
            System.out.println("File updated successfully.");

        } catch (IOException e) {
            System.out.println("Error updating file: " + e.getMessage());
        }
    }

    // Delete a file
    private static void deleteFile(String filePath) {
        try {
            Files.delete(Paths.get(filePath));
            System.out.println("File deleted: " + filePath);
        } catch (IOException e) {
            System.out.println("Error deleting file: " + e.getMessage());
        }
    }
}


# practice project 8

package Practice;

public class Test
 { 
    
    static String Employee_name; 
    static float Employee_salary; 
  
    static void set(String n, float p) { 
        Employee_name  = n; 
        Employee_salary  = p; 
    } 
  
    static void get() { 
        System.out.println("Employee name is: " +Employee_name ); 
        System.out.println("Employee CTC is: " + Employee_salary); 
    } 
  
    public static void main(String args[]) { 
        Test.set("Rathod Avinash", 10000.0f); 
        Test.get(); 
    } 
} 

//Abstraction

abstract class GFG{ 
	  //abstract methods declaration 
	  abstract void add(); 
	  abstract void mul(); 
	  abstract void div(); 
	} 

//Encapsulation using private modifier  

//Employee class contains private data called employee id and employee name 
class Employee { 
  private int empid; 
    private String ename; 
} 


//inheritance

class A{ 
	  //parent class methods 
	  void method1(){} 
	  void method2(){} 
	} 
	  
	//derived class or child class or base class 
	class B extends A{  //Inherits parent class methods 
	  //child class methods 
	  void method3(){} 
	  void method4(){} 
	}


	
	
	//polymorphism

	  
	// This class will contain 
	// 3 methods with same name, 
	// yet the program will 
	// compile & run successfully 
	
	 class Sum { 
		  
	    // Overloaded sum(). 
	    // This sum takes two int parameters 
	    public int sum(int x, int y) 
	    { 
	        return (x + y); 
	    } 
	  
	    // Overloaded sum(). 
	    // This sum takes three int parameters 
	    public int sum(int x, int y, int z) 
	    { 
	        return (x + y + z); 
	    } 
	  
	    // Overloaded sum(). 
	    // This sum takes two double parameters 
	    public double sum(double x, double y) 
	    { 
	        return (x + y); 
	    } 
	  
	    // Driver code 
	    public static void main(String args[]) 
	    { 
	        Sum s = new Sum(); 
	        System.out.println(s.sum(10, 20)); 
	        System.out.println(s.sum(10, 20, 30)); 
	        System.out.println(s.sum(10.5, 20.5)); 
	    } 
	} 


# practice project 9


package Practice;

import java.io.*; 

//Interfaces Declared 
interface Parent1 { 
 void fun(); 
} 

//Interfaces Declared 
interface Parent2 { 
 void fun(); 
} 

//Inheritance using Interfaces 
class test implements Parent1, Parent2 { 
 public void fun() 
 { 
     System.out.println("fun function"); 
 } 
} 

//Driver Class 
class test1 { 
 // main function 
 public static void main(String[] args) 
 { 
     test t = new test(); 
     t.fun(); 
 } 
}
