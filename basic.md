## For loop

### Named for loop

break the outer loop

```java
aa: 
    for (...) {
    bb:
        for (...) {
        ...
        break aa;
        }
    }
```

## Static

* Variable \(class variable\)
* Method
  * The static method can not use non static data member or call non-static method directly.
  * **this** and **super** cannot be used in static context.
* Block \(static initializer block\)

  * Is used to initialize the static data member.

  Executed before main method at the time of classloading

  ```java
  class A2{
  static { System.out.println("static block is invoked");}
  ...
  ```

## This

To distinguish local and instance variable.

Call this\(\) in constructor must be the first statement.

## Inheritance

### Syntax

```java
class sub-class-name extends superclass-name{ }
```

### Type of inheritance

Single, Multilevel, Hierarchical

Multiple, Hybrid \(Diamond\) : one class extends multiple classes. Not supported through class. There would be ambiguity if there are same methods/variables in the extended classes.

## Method overloading

* With different number of arguments
* With different type of arguments
* Can't overload by return type only due to ambiguity.

### Type Promotion

![Type Promotion](C:\Users\LiZhang\GitBook\Library\Import\java\type2.jpg)

## Method Overriding

The overriding method can't be more restrictive than the overridden method.

### Covariant return type

overriding by non-primitive return type

## Instance initializer block

Called after parent constructor is called

```java
class A {
  {
    //initialier block
    a = 10;
      for (int i=0; i...) {}
  }
}
```

## The final Keyword

* Final variable: can only be initialized in constructor. If it's static, it can only be initialized in static initializer block. Once initialized, can't change its value. \(constant\)
  * Blank or uninitialized final variable: used for some variables that are initialized at object creating time and can't be changed anymore.
* Final method: is inherited but can't be overridden. We can't declare constructor be final, because it's never inherited. 
* Final Class
* Final Parameter: can't be changed in a function 

## Polymorphism

Can't be achieved by data members

### instanceof

obj\_var instanceof ClassA. Usually used with down casting.

## Java Abstraction

### Abstract class

Can't be instantiated and must be extended.

If there is one abstract method in the class, the class must be abstract.

```java
abstract class abs_a {
  abstract abs_method(); //no implmentation
}
```

```java
interface A{  
void a();  
void b();  
void c();  
void d();  
}  
//Here, we provide the implementation of c() so the programmer of class M needs not to implement it.
abstract class B implements A{  
public void c(){System.out.println("I am C");}  
}  

class M extends B{  
public void a(){System.out.println("I am a");}  
public void b(){System.out.println("I am b");}  
public void d(){System.out.println("I am d");}  
}  

class Test5{  
public static void main(String args[]){  
A a=new M();  
a.a();  
a.b();  
a.c();  
a.d();  
}}
```

### Interface

Has static constants and abstract methods.

Can have multiple inheritance. Class can implement multiple classes, interface can extends multiple interfaces. \(there is no ambiguity even if multiple interfaces have the same method, since the method is implemented in class\)

```java
class A7 implements Printable,Showable{ }
```

> The java compiler adds public and abstract keywords before the interface method. More, it adds  public, static and final keywords before data members
>
> class **extends** class, class **implements** interface, interface **extends** interface.
>
> After Java8, interface can have default method and static method.

```java
interface Drawable{
  default void msg() {System.out.println("something");}
  static int cube (x) {return x*x*x;}
}
```

### Marker or Tagged Interface

Empty interfaces. Used to provide essential information to JVM. like Serializable, Cloneable, Remote.

### difference between Interface and abstract class



| Abstract class                           | Interface                                |
| :--------------------------------------- | ---------------------------------------- |
| can have abstract and non-abstract method | can only have abstract/default/static methods |
| doesn't support multiple inheritance     | support                                  |
| can have final, non-final, static and non-static variables | only final and static variables          |
| keyword: abstract                        | keyword: interface                       |
|                                          |                                          |
|                                          |                                          |

### default and static method in interface

From java8, interface can have static or default method.

```java
interface Sayable{    
    // default method. Provide a default implmentation. can be overriden     
    default void say(){    
        System.out.println("Hello, this is default method");    
    }    
    // Abstract method    
    void sayMore(String msg);    
    // static method    
    static void sayLouder(String msg){    
        System.out.println(msg);    
    }
}
```





## Package

```java
package a_package;
class AClass{}

import a_package.*;
import a_package.AClass;
AClass a = new a_package.AClass();
```

> The standard of defining package is domain.company.package e.g. com.javatpoint.bean or org.sssit.dao
>
> Rule: There can be only one public class in a java source file and it must be saved by the public class name.

## Access Modifiers

* private

  if a constructor is private, you can't create instance from outside of the class.

  > A class can't be private or protected except nested class.

* default \(If you don't use any modifier, it's "default" by default\).

  Can only be accessed within package.

* protected: accessible within package and outside package but only through inheritance.

* public

## Object class in Java

| Method                                   | Description                              |
| ---------------------------------------- | ---------------------------------------- |
| public final Class getClass\(\)          | returns the Class class object of this object. The Class class can further be used to get the metadata of this class. |
| public int hashCode\(\)                  | returns the hashcode number for this object. |
| public boolean equals\(Object obj\)      | compares the given object to this object. |
| protected Object clone\(\) throws CloneNotSupportedException | creates and returns the exact copy \(clone\) of this object. |
| public String toString\(\)               | returns the string representation of this object. |
| public final void notify\(\)             | wakes up single thread, waiting on this object's monitor. |
| public final void notifyAll\(\)          | wakes up all the threads, waiting on this object's monitor. |
| public final void wait\(long timeout\)throws InterruptedException | causes the current thread to wait for the specified milliseconds, until another thread notifies \(invokes notify\(\) or notifyAll\(\) method\). |
| public final void wait\(long timeout,int nanos\)throws InterruptedExceptioncauses | the current thread to wait for the specified milliseconds and nanoseconds, until another thread notifies \(invokes notify\(\) or notifyAll\(\) method\). |
| public final void wait\(\)throws InterruptedException | causes the current thread to wait, until another thread notifies \(invokes notify\(\) or notifyAll\(\) method\). |
| protected void finalize\(\)throws Throwable | is invoked by the garbage collector before object is being garbage collected. |

## Object cloning

implement Cloneable interface and inplement clone method.

## Wrapper class

convert primitive to class or vice-versa

| boolean | Boolean   |
| ------- | --------- |
| char    | Character |
| byte    | Byte      |
| short   | Short     |
| int     | Integer   |
| long    | Long      |
| float   | Float     |
| double  | Double    |
|         |           |

```java
int a = 10;
Integer i = Integer.valueOf(a);
Integer j = a; //autoboxing
int k = i.intValue();
int m = i;
```

## Exceptions

* Checked Exceptions \(checked at compile time\): The classes extend Throwable except RuntimeException and Error.
* unchecked Exceptions: extends RuntimeException
* Error

### keywords

try, catch, finally, throw, throws

```java
try {  } catch (Exception_class_Name ref) {exception handling;} 
catch (...) // one try can have mulitple catch, but only one fanally
finally {}; // always executed except exiting by System.exit() or fatal error causing program to abort.
```

> Rule: At a time only one Exception is occured and at a time only one catch block is executed.
>
> Rule: All catch blocks must be ordered from most specific to most general i.e. catch for ArithmeticException must come before catch for Exception

#### Finally

to execute important code\* such as closing connection, stream etc   
Always executed whether exception is handled. If not handled, the program is terminated after execution of finally block.

#### Throw

```java
throw new ArithmeticException("not valid");
```

Exception propagated: unchecked exception will be passed down along call stack till it's caught. Checked exception will not.

#### Throws \(declare an exception\)

```java
return_type method_name() throws exception_class_name {}//throw new IOException("sss")}
```

​    Which exception should be declared: checked exception only.

​    Now checked exception can also be propagated. It provides information to the callers about the exception.

​    If you are calling method that declares an exception, you must either catch or declare it.

### ExceptionHandling with MethodOverriding in Java

* If the superclass method does not declare an exception

  * If the superclass method does not declare an exception, subclass overridden method cannot declare the checked exception but it can declare unchecked exception.  

* If the superclass method declares an exception

  * If the superclass method declares an exception, subclass overridden method can declare same, subclass exception or no exception but cannot declare parent exception. 

### Custom Exception

```java
class InvalidAgeException extends Exception{  
 InvalidAgeException(String s){  
  super(s);  
 }
```

### multiple catch

```java
public class MultipleExceptionExample{    
    public static void main(String args[]){    
        try{    
            int array[] = newint[10];    
            array[10] = 30/0;    
        }    
        catch(ArithmeticException | ArrayIndexOutOfBoundsException e){  
            System.out.println(e.getMessage());  
        }    
     }    
}
```

> #### Note - Catch block which handles more than one exception type makes the catch parameter implicitly final. In the above example, the catch parameter "e" is final and therefore you cannot assign any value to it.

old:

```java
public class MultipleExceptionExample{    
    public static void main(String args[]){    
        try{    
            int array[] = newint[10];    
            array[10] = 30/0;    
        }    
        catch(ArithmeticException e){  
            System.out.println(e.getMessage());  
        }    
        catch(ArrayIndexOutOfBoundsException e){  
            System.out.println(e.getMessage());  
        }    
        catch(Exception e){  
            System.out.println(e.getMessage());  
        }    
     }    
}  
```

### try-with-resource

The try-with-resources statement ensures that each resource is closed at the end of the statement execution

```java
try(FileOutputStream fileOutputStream = newFileOutputStream("/java7-new-features/src/abc.txt")){      
String msg = "Welcome to javaTpoint!";      
byte byteArray[] = msg.getBytes(); //converting string into byte array      
fileOutputStream.write(byteArray);  
System.out.println("Message written to file successfuly!");      
}catch(Exception exception){  
       System.out.println(exception);  
}      
```



## lambda

```java
(argument-list) -> {body}  
```



old: (functional interface : an interface w/o only one method)

```java
interface Drawable{  
    public void draw();  
}  
public class LambdaExpressionExample {  
    public static void main(String[] args) {  
        int width=10;  
  
        //without lambda, Drawable implementation using anonymous class  
        Drawable d=new Drawable(){  
            public void draw(){System.out.println("Drawing "+width);}  
        };  
        d.draw();  
    }  
}  
```



```java
//lambda w/o parameter
interface Sayable{  
    public String say();  
}  
public class LambdaExpressionExample{  
public static void main(String[] args) {  
    Sayable s=()->{  
        return "I have nothing to say.";  
    };  
    System.out.println(s.say());  
}  
}  
```

```java
//multiple prameters
interface Addable{  
    int add(int a,int b);  
}  
  
public class LambdaExpressionExample{  
    public static void main(String[] args) {  
          
        // Multiple parameters in lambda expression  
        Addable ad1=(a,b)->(a+b);  
        System.out.println(ad1.add(10,20));  
          
        // Multiple parameters with data type in lambda expression  
        Addable ad2=(int a,int b)->(a+b);  
        System.out.println(ad2.add(100,200));  
    }  
}  
```

> In Java lambda expression, if there is only one statement, you may or may not use return keyword. You must use return keyword when lambda expression contains multiple statements.

```java
package lambdaExample;  
  
interface Addable{  
    int add(int a,int b);  
}  
  
public class lambdaExpression {  
    public static void main(String[] args) {  
          
        // Lambda expression without return keyword.  
        Addable ad1=(a,b)->(a+b);  
        System.out.println(ad1.add(10,20));  
          
        // Lambda expression with return keyword.    
        Addable ad2=(int a,int b)->{  
                            return (a+b);   
                            };  
        System.out.println(ad2.add(100,200));  
    }  
}  
```

```java
 Collections.sort(list,(p1,p2)->{  
        return p1.name.compareTo(p2.name);  
        });  
```

```java
        List<Product> list=new ArrayList<Product>();  
        // using lambda to filter data  
        Stream<Product> filtered_data = list.stream().filter(p -> p.price > 20000);  
		
		// using lambda to iterate through collection  
        filtered_data.forEach(  
                product -> System.out.println(product.name+": "+product.price)  
        );  

```

## Method reference

### Reference to a Static Method

ContainingClass::staticMethodName  

```java
interface Sayable{  
    void say();  
}  
public class MethodReference {  
    public static void saySomething(){  
        System.out.println("Hello, this is static method.");  
    }  
    public static void main(String[] args) {  
        // Referring static method  
        Sayable sayable = MethodReference::saySomething;  
        // Calling interface method  
        sayable.say();  
    }  
}  
```

### reference to instance method

```java
interface Sayable{  
    void say();  
}  
publicclass MethodReference {  
    public void saySomething(){  
        System.out.println("Hello, this is non-static method.");  
    }  
    public static void main(String[] args) {  
        MethodReference methodReference = new MethodReference(); // Creating object  
        // Referring non-static method using reference  
            Sayable sayable = methodReference::saySomething;  
        // Calling interface method  
            sayable.say();  
            // Referring non-static method using anonymous object  
            Sayable sayable2 = new MethodReference()::saySomething; // You can use anonymous object also  
            // Calling interface method  
            sayable2.say();  
    }  
}  
```

### reference to a constructor

```java
interface Messageable{  
    Message getMessage(String msg);  
}  
class Message{  
    public Message(String msg){  
        System.out.print(msg);  
    }  
}  
public class ConstructorReference {  
    public static void main(String[] args) {  
        Messageable hello = Message::new;  
        hello.getMessage("Hello");  
    }  
}  
```

## Functional interface

## Stream

