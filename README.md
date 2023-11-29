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


