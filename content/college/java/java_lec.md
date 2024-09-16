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
