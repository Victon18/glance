# 3 Sept
```java
public class courseProgram{
    public static void main (String[] args){
        Course c1 = new Course(10,"Java","Astik",5,10);
        Course c2 = new Course(20,"Python","Pratik",4,30);
        Course c3 = new Course(30,"Ruby","Kalpana",2,40);
        Course arr[] = {c1,c2,c3}
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
