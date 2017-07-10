## Synchronized Method

```java
//example of java synchronized method  
class Table{  
 synchronized void printTable(int n){//synchronized method  
   for(int i=1;i<=5;i++){  
     System.out.println(n*i);  
     try{  
      Thread.sleep(400);  
     }catch(Exception e){System.out.println(e);}  
   }  
  
 }  
}  
  
class MyThread1 extends Thread{  
Table t;  
MyThread1(Table t){  
this.t=t;  
}  
public void run(){  
t.printTable(5);  
}  
  
}  
class MyThread2 extends Thread{  
Table t;  
MyThread2(Table t){  
this.t=t;  
}  
public void run(){  
t.printTable(100);  
}  
}  
  
public class TestSynchronization2{  
public static void main(String args[]){  
Table obj = new Table();//only one object  
MyThread1 t1=new MyThread1(obj);  
MyThread2 t2=new MyThread2(obj);  
t1.start();  
t2.start();  
}  
}  
```

* By Using Anonymous class

```java
//Program of synchronized method by using annonymous class  
class Table{  
 synchronized void printTable(int n){//synchronized method  
   for(int i=1;i<=5;i++){  
     System.out.println(n*i);  
     try{  
      Thread.sleep(400);  
     }catch(Exception e){System.out.println(e);}  
   }  
  
 }  
}  
  
public class TestSynchronization3{  
public static void main(String args[]){  
final Table obj = new Table();//only one object  
  
Thread t1=new Thread(){  
public void run(){  
obj.printTable(5);  
}  
};  
Thread t2=new Thread(){  
public void run(){  
obj.printTable(100);  
}  
};  
  
t1.start();  
t2.start();  
}  
}  
```

## Synchronize Block

* Synchronized block is used to lock an object for any shared resource.
* Scope of synchronized block is smaller than the method.

```java
synchronized (object reference expression) {   
  //code block   
}  
```

```java
class Table{  
  
 void printTable(int n){  
   synchronized(this){//synchronized block  
```

## Static Synchronization

Make any static method as synchronized, the lock will be on the class not on object. (synchronized threads may interfere each other if they sync on different objects)

```java
class Table{  
  
 synchronized static void printTable(int n){  
```

It's equivalent to sync on the object class:

```java
static void printTable(int n) {  
    synchronized (Table.class) {       // Synchronized block on class A  
        // ...  
    }  
}  
```

## Cooperation (inter-thread communication)

Synchronized threads communicate with each other

* wait()
* notify()
* *notifyAll()

### Difference between wait and sleep?

| wait()                                   | sleep()                                  |
| ---------------------------------------- | ---------------------------------------- |
| wait() method releases the lock          | sleep() method doesn't release the lock. |
| is the method of Object class            | is the method of Thread class            |
| is the non-static method                 | is the static method                     |
| is the non-static method                 | is the static method                     |
| should be notified by notify() or notifyAll() methods | after the specified amount of time, sleep is completed. |

```java
class Customer{  
int amount=10000;  
  
synchronized void withdraw(int amount){  
System.out.println("going to withdraw...");  
  
if(this.amount<amount){  
System.out.println("Less balance; waiting for deposit...");  
try{wait();}catch(Exception e){}  
}  
this.amount-=amount;  
System.out.println("withdraw completed...");  
}  
  
synchronized void deposit(int amount){  
System.out.println("going to deposit...");  
this.amount+=amount;  
System.out.println("deposit completed... ");  
notify();  
}  
}  
  
class Test{  
public static void main(String args[]){  
final Customer c=new Customer();  
new Thread(){  
public void run(){c.withdraw(15000);}  
}.start();  
new Thread(){  
public void run(){c.deposit(10000);}  
}.start();  
  
}}  
```

## Interrupting a thread

If any thread is in sleeping or waiting state (i.e. sleep() or wait() is invoked), calling the interrupt() method on the thread, breaks out the sleeping or waiting state throwing InterruptedException. If the thread is not in the sleeping or waiting state, calling the interrupt() method performs normal behaviour and doesn't interrupt the thread but sets the interrupt flag to true.



- **public void interrupt()**
- **public static boolean interrupted()**
- **public boolean isInterrupted()**

#### Interrupt Then Stop

Propagating the interrupt exception w/o handling. So it will stop working

```java
class TestInterruptingThread1 extends Thread{  
public void run(){  
try{  
Thread.sleep(1000);  
System.out.println("task");  
}catch(InterruptedException e){  
throw new RuntimeException("Thread interrupted..."+e);  
}  
  
}  
  
public static void main(String args[]){  
TestInterruptingThread1 t1=new TestInterruptingThread1();  
t1.start();  
try{  
t1.interrupt();  
}catch(Exception e){System.out.println("Exception handled "+e);}  
  
}  
}  
```

#### Interrupt and continue

Handle the exception, then the method will continue after interrupted. 

```java
class TestInterruptingThread2 extends Thread{  
public void run(){  
try{  
Thread.sleep(1000);  
System.out.println("task");  
}catch(InterruptedException e){  
System.out.println("Exception handled "+e);  
}  
System.out.println("thread is running...");  
}  
  
public static void main(String args[]){  
TestInterruptingThread2 t1=new TestInterruptingThread2();  
t1.start();  
  
t1.interrupt();  
  
}  
}  
```

#### isInterrupted() and interrupted()

The isInterrupted() method returns the interrupted flag either true or false. The static interrupted() method returns the interrupted flag after that it **sets the flag to false** if it is true.

```java
public class TestInterruptingThread4 extends Thread{  
  
public void run(){  
for(int i=1;i<=2;i++){  
if(Thread.interrupted()){  
System.out.println("code for interrupted thread");  
}  
else{  
System.out.println("code for normal thread");  
}  
  
}//end of for loop  
}  
  
public static void main(String args[]){  
  
TestInterruptingThread4 t1=new TestInterruptingThread4();  
TestInterruptingThread4 t2=new TestInterruptingThread4();  
  
t1.start();  
t1.interrupt();  
  
t2.start();  
  
}  
}  
```





## Reentrant Monitor

Thread can reuse the same monitor for different synchronized methods if one method is called from the method. It eliminates the possibility of single thread deadlocking

```java
class Reentrant {  
    public synchronized void m() {  
    n();  
    System.out.println("this is m() method");  
    }  
    public synchronized void n() {  
    System.out.println("this is n() method");  
    }  
}  
```



