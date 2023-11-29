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




#
