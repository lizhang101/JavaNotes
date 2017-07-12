## Assertion

```java
assert value>18;
assert value>18 : "Not Valid"
```

> Use java **-ea** to run with assertion enabled. 
>
> java -ea AssertionExample

> According to Sun Specification, assertion should not be used to check arguments in the public methods because it should result in appropriate runtime exception e.g. IllegalArgumentException, NullPointerException etc.

## Var args 

```java
class VarargsExample2{  
   
 static void display(String... values){  
  System.out.println("display method invoked ");  
  for(String s:values){  
   System.out.println(s);  
  }  
 }  
}  
```

## Static import

The import allows the java programmer to access classes of a package without package qualification whereas the static import feature allows to access the static members of a class without the class qualification. The import provides accessibility to classes and interface whereas static import provides accessibility to **static members of the class**.

```java
import static java.lang.System.*;
...
out.println("Hello");//Now no need of System.out 

```

> overusing of it may make the program unreadable and unmaintainable

## Enum

```java
enum Day{ SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY}  
Day day=Day.MONDAY;
switch(day){  
case SUNDAY:   
 System.out.println("sunday");  
 break;  
```

```java
//Initialize specific values to the enum constants 
enum Season{   
WINTER(5), SPRING(10), SUMMER(15), FALL(20);   
  
private int value;
//private constructor, so you can't use new to create an object of enum
private Season(int value){  
this.value=value;  
}
} 
```

> enum can have abstract method

## Generics

Before generics, we can store any type of objects in collection i.e. non-generic. Now generics, forces the java programmer to store specific type of objects.

### Advantages:

1. Type-safety
2. type casting is not required
3. compile-time checking

```java
import java.util.*;  
class TestGenerics2{  
public static void main(String args[]){  
Map<Integer,String> map=new HashMap<Integer,String>();  
map.put(1,"vijay");  
map.put(4,"umesh");  
map.put(2,"ankit");  
  
//Now use Map.Entry for Set and Iterator  
Set<Map.Entry<Integer,String>> set=map.entrySet();  
  
Iterator<Map.Entry<Integer,String>> itr=set.iterator();  
while(itr.hasNext()){  
Map.Entry e=itr.next();//no need to typecast  
System.out.println(e.getKey()+" "+e.getValue());  
}  
  
}}
```

### generic class

**Creating generic class:**

```java
class MyGen<T>{  
T obj;  
void add(T obj){this.obj=obj;}  
T get(){return obj;}  
}
```

**Type Parameters**

The type parameters naming conventions are important to learn generics thoroughly. The commonly type parameters are as follows:

1. T - Type
2. E - Element
3. K - Key
4. N - Number
5. V - Value

**generic method**

```java
public class TestGenerics4{  
  
   public static < E > void printArray(E[] elements) {  
        for ( E element : elements){          
            System.out.println(element );  
         }  
         System.out.println();  
    }  
    public static void main( String args[] ) {  
        Integer[] intArray = { 10, 20, 30, 40, 50 };  
        Character[] charArray = { 'J', 'A', 'V', 'A', 'T','P','O','I','N','T' };  
  
        System.out.println( "Printing Integer Array" );  
        printArray( intArray  );   
  
       System.out.println( "Printing Character Array" );  
        printArray( charArray );   
    }   
}  
```

**Wildcard in Java generics**

<? extends Number>, it means any child class of Number

```java
import java.util.*;  
abstract class Shape{  
abstract void draw();  
}  
class Rectangle extends Shape{  
void draw(){System.out.println("drawing rectangle");}  
}  
class Circle extends Shape{  
void draw(){System.out.println("drawing circle");}  
}  
  
  
class GenericTest{  
//creating a method that accepts only child class of Shape  
public static void drawShapes(List<? extends Shape> lists){  
for(Shape s:lists){  
s.draw();//calling method of Shape class by child class instance  
}  
}  
public static void main(String args[]){  
List<Rectangle> list1=new ArrayList<Rectangle>();  
list1.add(new Rectangle());  
  
List<Circle> list2=new ArrayList<Circle>();  
list2.add(new Circle());  
list2.add(new Circle());  
  
drawShapes(list1);  
drawShapes(list2);  
}}  
```

```fence
output:
drawing rectangle
drawing circle
drawing circle
```

### Type interface for generic instance creation

```java7
Ex. List<Integer> list = new List<>(); // Here, we just used diamond  
```



