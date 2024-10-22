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
formal argument args defined during creation of function
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

## collection
### Set interface
- `TreeSet` and `Hashset` are implimentation classes
### List interface

- List is used to store duplicate element also unlike set
-  It is the most useable collection in java
- `ArrayList`, `LinkedList`, and `Vector` are implimenting classes of list interface.
- vector is synchronized, and uses only one threas at a time
- array list has fixed size, can use multiple threads, non-sorted
- linkedlist is generally used from in between .

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
        System.out.println("List: "+a1);
        a1.remove("Hardoi")
    }
}
```
collections class
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

### Map interface
- It is used to store element in key values pair
- `HashMap` and `PreMap` are implimenting classes .

