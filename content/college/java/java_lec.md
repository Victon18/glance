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
