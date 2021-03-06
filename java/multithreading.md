创建一个新线程的方法有两种：

__Method 1__
声明一个实现Runnable接口的类，实现(*implements*) run方法。然后可以分配类的实例，在创建线程时作为参数传递，并启动。
```
package MyThread;

class RunnableDemo implements Runnable {
	   private Thread t;
	   private String threadName;
	   
	   RunnableDemo( String name) {
	      threadName = name;
	      System.out.println("Creating " +  threadName );
	   }
	   
	   // 1 
	   public void run() { 
	      System.out.println("Running " +  threadName );
	      try {
	         for(int i = 100; i > 0; i--) {
	            System.out.println("Thread: " + threadName + ", " + i);
	            // Let the thread sleep for a while.
	            Thread.sleep(10);
	         }
	      }catch (Exception e) {
	         System.out.println("Thread " +  threadName + " interrupted.");
	      }
	      System.out.println("Thread " +  threadName + " exiting.");
	   }
	   
	   public void start () { 
	      System.out.println("Starting " +  threadName );
	      if (t == null) {
	         t = new Thread (this, threadName);  // 2
	         t.start ();  // 3
	      }
	   }
	}
					
	public class TestThread {

	   public static void main(String args[]) {
	      RunnableDemo R1 = new RunnableDemo( "Thread-1");
	      R1.start();
	      
	      RunnableDemo R2 = new RunnableDemo( "Thread-2");
	      R2.start();
	   }   
	}
```
__Method 2__
声明一个Thread的子类，并覆盖重写(*overrides*)Thread类的run方法。
```
package MyThread;

class ThreadDemo extends Thread {
	   private Thread t;
	   private String threadName;
	   
	   ThreadDemo( String name) {
	      threadName = name;
	      System.out.println("Creating " +  threadName );
	   }
	   
	   public void run() {
	      System.out.println("Running " +  threadName );
	      try {
	         for(int i = 4; i > 0; i--) {
	            System.out.println("Thread: " + threadName + ", " + i);
	            // Let the thread sleep for a while.
	            Thread.sleep(50);
	         }
	      }catch (InterruptedException e) {
	         System.out.println("Thread " +  threadName + " interrupted.");
	      }
	      System.out.println("Thread " +  threadName + " exiting.");
	   }
	   
	   public void start () {
	      System.out.println("Starting " +  threadName );
	      if (t == null) {
	         t = new Thread (this, threadName);
	         t.start ();
	      }
	   }
	}

	public class TestThread2 {

	   public static void main(String args[]) {
	      ThreadDemo T1 = new ThreadDemo( "Thread-1");
	      T1.start();
	      
	      ThreadDemo T2 = new ThreadDemo( "Thread-2");
	      T2.start();
	   }   
	}
  ```

__References__: 
[1]https://docs.oracle.com/javase/7/docs/api/java/lang/Thread.html
[2]https://www.tutorialspoint.com/java/java_multithreading.htm
