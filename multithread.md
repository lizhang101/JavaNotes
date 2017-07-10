## Advantage

* Non-blocking
* Parallel Processing (faster)
* Independent, it doesn't affect other threads if exception occurs in a single thread



## multiprocessing

* each process has its own address in memory
* heavyweight, communication cost between processes is high
* process switching cost is high (saving/loading registers, memory maps, updating list, etc.)

## Multithreading

* Share the **same address**
* lightweight, low cost in communication

### life cycle

![thread life cycle in java](https://www.javatpoint.com/images/threadstates.jpg)



### How to Create

#### By extending thread class

* Commonly used constructor of thread class
  - Thread()
  - Thread(String name)
  - Thread(Runnable r)
  - Thread(Runnable r,String name)
* Commonly used methods
  * **public void run(): **is used to perform action for a thread.
  * **public void start(): **starts the execution of the thread.JVM calls the run() method on the thread.
  * **public void sleep(long miliseconds): **Causes the currently executing thread to sleep (temporarily cease execution) for the specified number of milliseconds.
  * **public void join(): **waits for a thread to die.
  * **public void join(long miliseconds): **waits for a thread to die for the specified miliseconds.
  * **public int getPriority(): **returns the priority of the thread.
  * **public int setPriority(int priority): **changes the priority of the thread.
  * **public String getName(): **returns the name of the thread.
  * **public void setName(String name): **changes the name of the thread.
  * **public Thread currentThread(): **returns the reference of currently executing thread.
  * **public int getId(): **returns the id of the thread.
  * **public Thread.State getState(): **returns the state of the thread.
  * **public boolean isAlive(): **tests if the thread is alive.
  * **public void yield(): **causes the currently executing thread object to temporarily pause and allow other threads to execute.
  * **public void suspend(): **is used to suspend the thread(depricated).
  * **public void resume(): **is used to resume the suspended thread(depricated).
  * **public void stop(): **is used to stop the thread(depricated).
  * **public boolean isDaemon(): **tests if the thread is a daemon thread.
  * **public void setDaemon(boolean b): **marks the thread as daemon or user thread.
  * **public void interrupt(): **interrupts the thread.
  * **public boolean isInterrupted(): **tests if the thread has been interrupted.
  * **public static boolean interrupted(): **tests if the current thread has been interrupted.

#### By implementing Runnable interface

Runnable interface have only one method named run().

### Thread Scheduler

Only one thread at a time can run in a single process

> Preemptive scheduling and time slicing

### Daemon Thread

Is a service provider. Low priority, life time depends on user threads. Terminated automatically when all user threads die. e.g., gc, finalizer, etc.

### Thread pool

a group of worker threads that are waiting for the job and reuse many times. Better performance -- Save thread creating time.

```java
import java.util.concurrent.ExecutorService;  
import java.util.concurrent.Executors;  
public class TestThreadPool {  
     public static void main(String[] args) {  
        ExecutorService executor = Executors.newFixedThreadPool(5);//creating a pool of 5 threads  
        for (int i = 0; i < 10; i++) {  
            Runnable worker = new WorkerThread("" + i);  
            executor.execute(worker);//calling execute method of ExecutorService  
          }  
        executor.shutdown();  
        while (!executor.isTerminated()) {   }  
  
        System.out.println("Finished all threads");  
    }  
 }  
```

### Thread Group

Group multiple threads in a single object so we can suspend, resume, interrupt group of threads by a single method call.

| No.  | Constructor                              | Description                              |
| ---- | ---------------------------------------- | ---------------------------------------- |
| 1)   | ThreadGroup(String name)                 | creates a thread group with given name.  |
| 2)   | ThreadGroup(ThreadGroup parent, String name) | creates a thread group with given parent group and name. |

| No.  | Method                  | Description                              |
| ---- | ----------------------- | ---------------------------------------- |
| 1)   | int activeCount()       | returns no. of threads running in current group. |
| 2)   | int activeGroupCount()  | returns a no. of active group in this thread group. |
| 3)   | void destroy()          | destroys this thread group and all its sub groups. |
| 4)   | String getName()        | returns the name of this group.          |
| 5)   | ThreadGroup getParent() | returns the parent of this group.        |
| 6)   | void interrupt()        | interrupts all threads of this group.    |
| 7)   | void list()             | prints information of this group to standard console. |

```java
ThreadGroup tg1 = new ThreadGroup("Group A");   
Thread t1 = new Thread(tg1,new MyRunnable(),"one");     
Thread t2 = new Thread(tg1,new MyRunnable(),"two");
Thread t3 = new Thread(tg1,new MyRunnable(),"three");  

Thread.currentThread().getThreadGroup().interrupt();  
```

