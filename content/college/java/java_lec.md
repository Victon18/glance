# 3 Sept
```java
public class courseProgram{
    public static void main (String[] args){
        Course c1 = new Course(10,"Java","Astik",5,10);
        Course c2 = new Course(20,"Python","Pratik",4,30);
        Course c3 = new Course(30,"Ruby","Kalpana",2,40); Course arr[] = {c1,c2,c3}
        int average = findAng(arr,"Astik");
        System.out.println("Average"+average)
    }
    public static int findAvgofQquizbyadmin(Course ar[],String admin){
        int avg = 0;
        int count = 0;
        int sum = 0;
        for (Course v:ar){
            if (v.getCourseAdmin().equals(admin)){
                sum = sum+v.getQuiz();
                count++;
            }
        }
        avg = sum/count;
        return avg;
    }
}
```
```java
Course[] list = sortCourseByHandsOn(arr,23);
for(Coure v:list){
System.out.println("Average"+average)
}
 public static Course[] sortCourseByHandsOn(course ar[], int x){
    Course ar2[] = new Course [ar.length];
    for(int i = 0;i<arr.length;i++){
        if (ar[i].getHandson()<x){
            ar2[i] = ar[i];
        }
    }
    Arrays.sort(ar2);
    return ar2;
 }
```
```java
public class void main(String[] args){
    int[] list = {4,5,6,7,8};
    System.out.println("Print1");
    for (int i = 0; i<list.length;i++){
        System.out.println("Print2");
    }
}
```
# 6 sep
```java
// palindrome strig
//enter a string and print string by converting all vowels to capital
//enter a string and checkk if the second last char is happy or not
```
# 9 sept
String objects are immutable
it means the content of objects are not possible to change during the execution of program
if any method tries to change the content new object on the memory is created.
If we want to create a mutable string object then we can create object of String Buffer or Srirng Builder class
String Buffer is thread safe but string builder is not thread safe.
```java
public static void main(String[] args){
    String s = new String("gla");
    StringBuffer s1 = new StringBuffer(s);
    s1.append("@mathura");
    s1.replace(4,11,"noida");
    s1.reverse();
    s1.tostring();
    System.out.println(s1);
    System.out.println(s1.isBlank());
    System.out.println(s1.isEmpty());
    String s = new Stirng("go to the hell billboy");
    StirngTokenizer st=new StringTokenizer(s);
   // while(st.hasMoreElements()){
    while(st.hasMoreTokens()){
        //System.out.println(st.nextToken());
        System.out.println(st.nextElement());
    }

}
```
# 16 sep - Inheritance

```java
public class MainClass{
    public static void main (String[] args){
        Person p1 = new Person ("Mohan",45);
        Person p2 = new Person ("Mohan",45);
        System.out.println("No of objects: "+ p2.count);
        // for static  System.out.println("No of objects: "+ Person.count);
        p1.talking();
    }
}
public class Person {
    private String name; //instance variable
    private int age;
    static int count=0; //class variable

    public Person(String name,int age){
        super();
        this.name;
        this.age;
        count ++;
    }
    public void
}
```
----
```java
package java_2dc;

public class MainClass{
    public static void main(String[] args){
        Test t1 = new Test();
        system.out.println(Test.y);
    }
}
```
# 17 sep
Inheritance -> reuseability + extension + Modification
```Java
class Rectangle{
    int length;
    int breadth;
    public void area (){
        int area = length * breadth;
        System.out.println("Area: "+ area);
    }
}
Class Cuboid extends Rectangle{
    int height;
    public void volume(){
        int volume = length*breadth*height
        System.out.println("Volume: "+ volume);
    }
}
Class Main{
    public static void main (String[] args){
        Cuboid c1 =  new Cuboid();
        c1.length = 10;
        c1.breadth = 30;
        c1.height = 13;
        c1.area();
        c1.volume();
    }
}
```
----
class Data
- sum of digits
class Mydata extends data
- average
- lcm
class Main
- make obj
- call functions
```java
class Driver{
    public static void main (String[] args){
        Mydata c1 =  new Mydata();
        c1.num1 = 3;
        c1.num2 = 4;
        c1.sumOfdigits();
        c1.average();
       c1.lcm();
    }
}
class Data{
    int num1;
    int sum = 0;
    public void sumOfdigits () {
  		int rem;
  		int n = num1;
    		while (n > 0) {
    			rem = num1 % 10;
    			sum = sum+rem;
    			n = n / 10;
    		}
      System.out.println("Sum: "+ sum);
    }
}
class Mydata extends Data{
    int num2;
    public void average(){
        int sum = num1+num2;
        int avg = sum/2;
        System.out.println("average: "+ avg);
    }
  public void lcm (){
        int ans = (num1 > num2) ? num1 : num2;
        while (true) {
            if (ans % num1 == 0 && ans % num2 == 0)
                break;
            ans++;
        }
        System.out.println("LCM: " + ans);
    }
}
```
---
class Data1
- string as inputs
- count vowels
class data2 extends data1
- string as input
- replace vowels in capitals inside both strings
- print unique chars in string
class Main
- make obj
- call functions
```java
```
# 23 sep
Polymorphism
---
Polymorphism is a concept of implimenting different ways to get different output
Polymorphism is the most important component of object oriented development
It is of 2 types
    - complile time polymorphism
    - run time polymorphism
Compile time polymorphism is method overloading
Run time polymorphism is method overidding
Method overloading a class can have more than one methods with same name and with different arguments
Method overloading is compile time
Method overridding parent class and child class have the same method with same name and with same aurguments

```java
class addition{
    public void add(int a, int b){
        System.out.println("add: "+(a+b))
    }
    public void add(int a, int b, int c){
        System.out.println("add: "+(a+b+c))
    }
    public void add(double a, double  b){
        System.out.println("add: "+(a+b))
    }

}
class Main{
    public static void main(String args[]){
        addition a1 = new addition();
        a1.add(1,2,7);
        a1.add(1.2,2.6);
        a1.add(1,2);
    }
}
```
3formal argument args defined during creation of function
actual argument args passed during calling of function
they have to be in same type and same number hence compile time

widdeing or implicit conversion is automatically converting int to float but no vice versa because of range
narrowing or explicit conversion is not automatic hence use type casting

```java
class Parent {
    public void doTask(){
        System.out.println("M child will complete task");
    }
}
class Child extends Parent {
    public void display(){
        System.out.println("I am child of my parent ");
    }
    public void doTask(){
        System.out.println("I am busy in my java class");
    }
}
class Main{
    public static void main(){
        Child c1 = new Child();
        c1.doTask();
        c1.display();
    }
}
```
Access modifiers with increasing criteria
private -> default -> protected -> public
widening can only convert from lower to higher priority form child to parent
```java
super.dotask();
```
# 24 sept

Abstract class
---
class can have 0 or any number of abstract method
If an abstract class have number of abstract method these method muct be override in its child class
abstract class must be inherited by another class
impossible to create object of abstract class
we can create abstract mehtod by not having body of the method
we must make abstract method in child as well
```java
abstract class Animal{
    public void walking(){
        System.out.print("All animals can walk")
    }
    public abstract void eating(){

    }
}
class Cow extends Animal{
    public void eating(){
        System.out.print("Cow is eating grass")
    }
    public void display(){
        System.out.print("Cow is our mother")
    }
}
class Main(){
    public static void main{
    Cow c1 = new Cow();
    c1.display();
    c1.walking();
    }
}
```
abstract class Data
- private String st
- Constructor
- public void reverse()
- public abstract void commonchar()
- public abstract void caseChange()
class Mydata extends data
- private string s2
- constructor
- caseChange
- commonchar`
```java
abstract class Data{
    private String s1;
    public Strings(String s1){
        this.s1;
    }

    public void reverse(){

    }
    public abstract void commonChar(){

    }
    public abstract void caseChange(){

    }
}
class Mydata extends Data{
    private String s2;
    public Strings(String s2){
        this.s2;
    }
    public abstract void commonChar(){
        System.out.println("this is commonChar");
    }
    public abstract void caseChange(){
        System.out.println("this is commonChar");
    }
}
class Main{
    public static void main(Strings args[]){
    Mydata c1 = new Mydata();
    c1.reverse();
    c1.commonChar();
    c1.caseChange();
    }
}
```
# 27 sept
### exception handling
- Error is abnormal condition in the program which force the program to terminate without computing when it occurs
- Error are of two types
- Compile and runtime error


throwable are of two types
Error and exception
Exception happens only at run time
Exceotion is a super class whereas specific type of exception are child class
Exception are of two types
Checked and Unchecked

Checked Exception
These exception occur at run time but at compile time compiler gives warning to handel and declare these exceptions
Checked exception includes IO exception and SQL exception
Unchecked Exception
about these exceptions compiler does not know anything
Unchecked exception includes ArrayIndexOutOfBounds exception and Arithematic exception

```java
try{
//code to generate error
}
catch{
//code to handel exception
}
finally{
//code to be executed in both condition
}
```

Throw -> to generate explicit exception
Throws -> to declare exception

```java
class ExceptionTest{
    public void test(int a,int b){
        try{
            int arr[] = {a,b,c};
            System.out.println(arr[4]);//ArrayIndexOutOfBounds
            int z = a/b;//arithematic errro
            System.out.print("Result: "+z);
        }
        catch(ArithematicException e){
            System.out.println("Problem: "+e.getMessage());
        }
        catch(Exception e){
            System.out.println("Problem another exception");
        }
    }
}
class Main{
    public static void main(String[] args){
        ExceptionTest t1 = new ExceptionTest();
        t1.test(25,0)
    }
}
```

# 21 Oct

## collections
### Set interface
- `TreeSet` and `Hashset` are implimentation classes

```java
import java.util.*;
class GFG {
    public static void main(String[] args)
    {
        Set<String> h = new HashSet<String>();
        h.add("India");
        h.add("Australia");
        h.add("South Africa");
        h.add("India");
        System.out.println(h);
        h.remove("Australia");
        System.out.println("Set after removing "
                           + "Australia:" + h);
        System.out.println("Iterating over set:");
        Iterator<String> i = h.iterator();
        while (i.hasNext())
            System.out.println(i.next());
    }
}
```
----
```java
import java.util.*;
class GFG {
    public static void main(String[] args)
    {
        Set<String> ts = new TreeSet<String>();
        ts.add("India");
        ts.add("Australia");
        ts.add("South Africa");
        ts.add("India");
        System.out.println(ts);
        ts.remove("Australia");
        System.out.println("Set after removing "
                           + "Australia:" + ts);

        System.out.println("Iterating over set:");
        Iterator<String> i = ts.iterator();
        while (i.hasNext())
            System.out.println(i.next());
    }
}

```
### List interface

- List is used to store duplicate element also unlike set
-  It is the most useable collection in java
- `ArrayList`, `LinkedList`, and `Vector` are implimenting classes of list interface.
- linkedlist is generally used to get elements in between.
`public interface List<E> extends Collection<E> ;`
#### arrayList
- array list is a dynamic array, can use multiple threads, non-sorted
```java
// ArrayList
public class TestArrayList{
    public static void main(String[] args){
        ArrayList a1 = new ArrayList();
        a1.add('Mathura');
        a1.add('Hardoi');
        a1.add('Agra');
        a1.add('Hardoi');
        a1.add('Delhi');
        a1.add(1,'Delhi');
        System.out.println("List: "+a1);
        a1.remove("Hardoi")
        a1.set(0, 5);
    }
}
```
---
```java
// listIterator
import java.util.*;
public class Main {
    public static void main(String[] argv) throws Exception
    {
            ArrayList<String> arrlist = new ArrayList<String>();
            arrlist.add("A");
            arrlist.add("B");
            arrlist.add("C");
            arrlist.add("D");
            System.out.println("ArrayList: "+ arrlist);
            ListIterator<String>
                iterator = arrlist.listIterator();
            while (iterator.hasNext()) {
                System.out.println("Value is : "+ iterator.next());
            }
            while (iterator.hasPrevious()) {
                System.out.println("Value is : "+ iterator.previous());
            }
    }
}
```
---
```java
//foreach
```
---
#### vector
- vector is synchronized, and uses only one threas at a time making it thread safe

- size method moves by 1  and capacity method moves by 10.
```java
import java.util.Vector;

public class VectorExample {
    public static void main(String[] args) {
        Vector<Integer> vector = new Vector<>();

        vector.add(1);
        vector.add(2);
        vector.add(3);

        System.out.println("Size: " + vector.size());
        System.out.println("Capacity: " + vector.capacity());
    }
}
```

collections class
---
- collections is a static class having methods used for opereration.
- sort, binary sort,
- sort has 2 arguments -> list, instance of implimentation
```java
public class TestArrayList{
    public static void main(String[] args){
        ArrayList a1 = new ArrayList();
        a1.add('Mathura');
        a1.add('Hardoi');
        a1.add('Agra');
        a1.add('Hardoi');
        a1.add('Delhi');
        System.out.println("List: "+a1);
        a1.remove("Hardoi")
        Collections.sort(a1);
        System.out.println("List: "+a1);
        int binSearch = collections.binarySearch(a1,'Hodal');
        System.out.println("List: "+a1);
        int binSearch = collections.synchronizedList(a1,'Hodal');
        System.out.println("List: "+a1);
    }
}
```
----
Comparable
---
```

```
Comparator
---
```java
import java.util.Comparator;
public class Student{
    private int rollno;
    private String name;
    public int getRoll(){
        return roll;
    }
    public void setRoll(int rollno){
        this.rollno = rollno;
    }
    public int getName(){
        return name;
    }
    public void setName(String name){
        this.name = name;
    }
    public Student(int rollno, String name){
        super();
        this.rollno = rollno;
        this.name = name;
    }
    public String toString(){
        return"Name: "+ name+ "Roll no: "+ rollno;
    }
}

public class ComparatorImp implements Comparator<Student>{
    @Override
    public int compare(Student o1, Student o2){
        if (o1.getRoll() >= o2.getRoll()){
            return 1;
        } else {
            return -1;
        }
    }
}

public class ArrayListDemo{
    public static void main(String[] args){
        ArrayList a1 = new ArrayList();
        a1.add(new Student(5,"Mohit"));
        a1.add(new Student(4,"Punit"));
        a1.add(new Student(6,"Purav"));
        a1.add(new Student(1,"Aashish"));
        a1.add(new Student(8,"Tanmay"));
        Collections.sort(a1,new ComparatorImp());
        System.out.println("List: ", a1);

    }
}

```

### Map interface
- It is used to store element in key values pair
- `HashMap` and `TreeMap` are implimenting classes .
- `HashTable` is synchronized hasmap.
```java
import java.util.HashMap;
import java.util.Map;

public class MapDemo{
    public static void main(String[] args){
        Map<Integer,String>mp=new HashMap<Integer,String()>;
        mp.put(11,"Chanchlani");
        mp.put(23,"Purav");
        mp.put(11,"Punit");
        mp.put(9,"Sunraybee");
        mp.put(7,"Ajay");
        System.out.println(mp);
        System.out.println(mp.get(23));

    }

}
```
---
```java
import java.util.HashMap;
import java.util.Map;

public class MapDemo {
    public static void main(String[] args) {
        Map<Integer, String> mp = new HashMap<Integer, String>();
        mp.put(11, capitalizeFirstAndLast("Chanchlani"));
        mp.put(23, capitalizeFirstAndLast("Purav"));
        mp.put(11, capitalizeFirstAndLast("Punit"));
        mp.put(9, capitalizeFirstAndLast("Sunraybee"));
        mp.put(7, capitalizeFirstAndLast("Ajay"));

        System.out.println(mp);
        System.out.println(mp.get(23));
    }

    private static String capitalizeFirstAndLast(String name) {
        if (name == null || name.length() == 0) {
            return name; // Return as is for null or empty strings
        }
        char[] chars = name.toCharArray();
        chars[0] = Character.toUpperCase(chars[0]); // Capitalize first character
        if (chars.length > 1) {
            chars[chars.length - 1] = Character.toUpperCase(chars[chars.length - 1]); // Capitalize last character
        }
        return new String(chars);
    }
}

```
# string API
# 8 oct
Implicit exception
```java
class ExTest{
    public void test(){
        try{
            int ar[] = {1,2,3,4};
            System.out.println(ar[5]);
        } catch(Exception e){
            System.out.println("Invalid index");
        }
    }
    public void mam(String[] args){
        ExTest t1 = new ExTest();
        t1.test();
    }
}
```
Explicit exception
```java
class ExTest{
    public void test(int age){
        try{
            if(age<1||age>100){
                throw new Exception ("Invalid age")
            }else{
            System.out.println("Age: "+age);
            }
        } catch(Exception e){
            System.out.println(e.getMessage());
        }
    }
    public void mam(String[] args){
        ExTest t1 = new ExTest();
        t1.test(12);
    }
}

```
Custom exception
```java
class CustException extends Exception{
    public CustException(String str){
        super(str);
    }
}
```
1. write a program to enter rows, columns, elements of two matrices and print them.
if they compatible for multiply print multiplication otherwise generate explicit exception.

2. write a program to enter a sentence; print its all words with first and last letter same.
if no such word generate explicit exception.

# 18 Nov
```java
import thread_class;
public class ThreadTest extends Thread{
public void run(){
    try{
        for(int i=2;i<=20;i=i+2){
            System.out.println(getName()+" "+i+" ");
            sleep(4000);
        }
    }
    catch(Exception e){
        e.printStackTrace();
    }
}
public static void main(String[] args){
    ThreadTest t1 = new ThreadTest();
    ThreadTest t2 = new ThreadTest();
    t1.start();
    t2.start();
}
}
```
Write a program to enter a number and print all its prime factors at 4 sec interval
```java
```
# 19 Dec
```java
import thread_class;
import java.util.Scanner;
public class ThreadTest2 extends Runnable{
public void run(){
    try{
        Scanner sc = new Scanner(System.in);
        System.out.println("enter");
        String name = sc.next();
        for(char c:(""+n).toCharArray()){
            System.out.println(c+" ");
            Thread.sleep(4000);
        }
        }
    }
    catch(Exception e){
        e.printStackTrace();
    }
}
public static void main(String[] args){
    ThreadTest2 t1 = new ThreadTest2();
    t1.setName("First");
    Thread th = new Thread(t1);
    th.start();
    ThreadTest t2 = new ThreadTest();
    t2.start();
}
}
```
1. All prime numbers from 100-50 at 5 sec interval
2. print factorial of after 10 sec interval
3. enter a sentence and print all its word at 5 sec by changing first and last letter in CAP
4.
# synchronization in multithreading
```java
class Data{
    int num;
    public Data(int num){
        this.num = num;
    }
}
class ThreadTest extends Thread {
    Data d1;
    public ThreadTest(Data d1){
    this.d1=d1;
    }
    public void run(){
    try{
        for (int i=1;i<=5;i++){
            System.out.println(d1.num+' ');
            sleep(4000);
        }
    }
    catch(Exception e){
        System.out.println("Some exception");
    }
    }
}
class MainClass{
public static void main (String[] args){
    ThreadTest t1 = new ThreadTest(new Data(5));
    ThreadTest t2 = new ThreadTest(new Data(10));
        t1.start();
        t2.start();
    }
}
```
---
```java
class Data{
    int num;
    public Data(int num){
        this.num = num;
    }
    synchronized void display(){
        try{
            for (int i = 1; i<=5,i++){
                System.out.println(num+" ");
                Threadsleep(4000);
           }
        catch(Exception e){
            System.out.println("Exception in synchronozation")
        }
        }

    }
}
class ThreadTest extends Thread {
    Data d1;
    public ThreadTest(Data d1){
    this.d1=d1;
    }
    public void run(){
    try{
        di.display();
    }
    catch(Exception e){
        System.out.println("Some exception");
    }
    }
}
class MainClass{
public static void main (String[] args){
    ThreadTest t1 = new ThreadTest(new Data(5));
    ThreadTest t2 = new ThreadTest(new Data(10));
        t1.start();
        t2.start();
    }
}
```
# 25 Nov
java 8 new features
1. functional interface
2. lamda expression
3. default method in iterface
4. for each method in collection

- interface has abstract methods

```java
package java8_features;
@FunctionalInterface
public interface Test{
    public void fun1();
    public void fun2(){
        System.out.println("fun2");
    }
}

public class MainClass {
    public static void main(String[] args){
        Test t1() ->{System.out.println("implementing");};
        t1.fun1();
    }
}
```
---
```java
public interface Test{
    public void fun1();
    public default void fun2(){
        System.out.println("Default method")
    }
}
public class TestImp implements Test{
    @Override
    public void fun1(){
        System.out.println("Abstracted");
    }
}
public class MainClass{
    public static void main(String[] args){
        TestImp t1=new TestImp();
        t1.fun2();
        t1.fun1();
    }
}
```
Array string collection and project

