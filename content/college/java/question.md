Create a class called Employee with the below attributes:

---
employeeld - int
name - String
branch - String
rating - double
company Transport - boolean

---
The above attributes should be private. write getters, setters and parameterized constructor as required.

Create class MyClass with main method.
Implement two static methods findCountOfEmployeesUsingCompTransport and findEmployeeWithSecondHighestRating in MyClass class.

findCountOfEmployeesUsingCompTransport method:
----------------------------------------------
This method will take an array of Employee object and a String parameter as input parameters.
This method will calculate and return the count of Employees who are all using company transport in the given branch (String parameter passed).
If no Employee in the given branch using company transport in the array of Employee objects, then the method should return 0.

findEmployeeWithSecondHighestRating method:
--------------------------------------------
This method will take an array of Employee objects as an input parameter.
This method will return  the object of the second highest rating employee from the array of Employee objects who are not using  company transport.
If all Employees using company transport in the array of Employee objects, then the method should return null.

Note: All the searches should be case sensitive, companyTransport and rating combination of each Employee is unique.
For findCountOfEmployeesUsingCompTransport method, The main method should print the returned count as it is if the returned value is greater than 0, else it should print "No such Employees".
Before calling these static methods in main, use Scanner object to read the values of four Employee
objects referring attributes in the above mentioned attributes sequence. Next, read the value of String
parameter for capturing branch.

---

```java
import java.util.*;
class Employee {
    private int employeeId;
    private String name;
    private String branch;
    private double rating;
    private boolean companyTransport;
    public Employee(int employeeId, String name, String branch, double rating, boolean companyTransport) {
        this.employeeId = employeeId;
        this.name = name;
        this.branch = branch;
        this.rating = rating;
        this.companyTransport = companyTransport;
    }
    public int getEmployeeId() {
        return employeeId;
    }
    public void setEmployeeId(int employeeId) {
        this.employeeId = employeeId;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public String getBranch() {
        return branch;
    }
    public void setBranch(String branch) {
        this.branch = branch;
    }
    public double getRating() {
        return rating;
    }
    public void setRating(double rating) {
        this.rating = rating;
    }
    public boolean isCompanyTransport() {
        return companyTransport;
    }
    public void setCompanyTransport(boolean companyTransport) {
        this.companyTransport = companyTransport;
    }
}
public class MyClass {
    public static int findCountOfEmployeesUsingCompTransport(Employee[] employees, String branch) {
        int count = 0;
        try {
            for (Employee emp : employees) {
                if (emp.getBranch().equals(branch) && emp.isCompanyTransport()) {
                    count++;
                }
            }
        } catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
        }
        return count;
    }
    public static Employee findEmployeeWithSecondHighestRating(Employee[] employees) {
        List<Employee> nonTransportEmployees = new ArrayList<>();
        try {
            for (Employee emp : employees) {
                if (!emp.isCompanyTransport()) {
                    nonTransportEmployees.add(emp);
                }
            }
            if (nonTransportEmployees.isEmpty()) {
                return null;
            }
            nonTransportEmployees.sort((e1, e2) -> Double.compare(e2.getRating(), e1.getRating()));
            if (nonTransportEmployees.size() < 2) {
                return null;
            }
            return nonTransportEmployees.get(1);
        } catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
            return null;
        }
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        try {
            System.out.print("How many employees do you want to input? ");
            int numEmployees = sc.nextInt();
            Employee[] employees = new Employee[numEmployees];
            for (int i = 0; i < numEmployees; i++) {
                System.out.println("Enter details for employee " + (i + 1) + ":");
                System.out.print("Employee ID: ");
                int employeeId = sc.nextInt();
                sc.nextLine(); // Consume the newline left-over from nextInt
                System.out.print("Name: ");
                String name = sc.nextLine();
                System.out.print("Branch: ");
                String branch = sc.nextLine();
                System.out.print("Rating: ");
                double rating = sc.nextDouble();
                System.out.print("Using company transport (true/false): ");
                boolean companyTransport = sc.nextBoolean();
                employees[i] = new Employee(employeeId, name, branch, rating, companyTransport);
            }
            sc.nextLine(); // Consume the leftover newline from nextBoolean
            System.out.print("Enter branch to search: ");
            String branch = sc.nextLine();
            int count = findCountOfEmployeesUsingCompTransport(employees, branch);
            if (count > 0) {
                System.out.println(count);
            } else {
                System.out.println("No such Employees");
            }
            Employee secondHighestRatedEmployee = findEmployeeWithSecondHighestRating(employees);
            if (secondHighestRatedEmployee != null) {
                System.out.println(secondHighestRatedEmployee.getEmployeeId());
                System.out.println(secondHighestRatedEmployee.getName());
            } else {
                System.out.println(" Employees using company transport");
            }
        } catch (Exception e) {
            System.out.println("Invalid input: " + e.getMessage());
        } finally {
            sc.close();
        }
    }
}
```
---
```java
import java.util.*;
public class Solution {
    static class Student {
        private int rollNo;
        private String name;
        private String subject;
        private char grade;
        private String date;
        public Student(int rollNo, String name, String subject, char grade, String date) {
            this.rollNo = rollNo;
            this.name = name;
            this.subject = subject;
            this.grade = grade;
            this.date = date;
        }
        public int getRollNo() {
            return rollNo;
        }
        public String getName() {
            return name;
        }
        public String getSubject() {
            return subject;
        }
        public char getGrade() {
            return grade;
        }
        public String getDate() {
            return date;
        }
    }
    public static Student[] findStudentByGradeAndMonth(Student[] students, char grade, int month) {
        List<Student> matchingStudents = new ArrayList<>();
        String monthString = String.format("%02d", month);
        try {
            for (Student student : students) {
                String studentMonth = student.getDate().split("/")[1];

                if (student.getGrade() == grade && studentMonth.equals(monthString)) {
                    matchingStudents.add(student);
                }
            }
            if (matchingStudents.isEmpty()) {
                return null;
            }
            Student[] result = new Student[matchingStudents.size()];
            matchingStudents.toArray(result);
            Arrays.sort(result, Comparator.comparingInt(Student::getRollNo));
            return result;
        } catch (Exception e) {
            System.out.println("Error occurred while processing data: " + e.getMessage());
            return null;
        }
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        try {
            System.out.print("How many students do you want to input? ");
            int numStudents = sc.nextInt();
            sc.nextLine();
            Student[] students = new Student[numStudents];
            for (int i = 0; i < numStudents; i++) {
                System.out.println("Enter details for student " + (i + 1) + ":");
                System.out.print("Roll No: ");
                int rollNo = sc.nextInt();
                sc.nextLine();
                System.out.print("Name: ");
                String name = sc.nextLine();
                System.out.print("Subject: ");
                String subject = sc.nextLine();
                System.out.print("Grade: ");
                char grade = sc.nextLine().charAt(0);
                System.out.print("Date (DD/MM/YYYY): ");
                String date = sc.nextLine();
                students[i] = new Student(rollNo, name, subject, grade, date);
            }
            System.out.print("Enter grade to filter: ");
            char grade = sc.nextLine().charAt(0);
            System.out.print("Enter month (1-12) to filter: ");
            int month = sc.nextInt();
            Student[] result = findStudentByGradeAndMonth(students, grade, month);
            if (result != null) {
                for (Student student : result) {
                    System.out.println(student.getName());
                    System.out.println(student.getSubject());
                }
                System.out.println(result.length);
            } else {
                System.out.println("No student found");
            }
        } catch (Exception e) {
            System.out.println("Invalid input: " + e.getMessage());
        } finally {
            sc.close();
        }
    }
}
```
----
- write a program to create an array of 10 numbers and print average of prime elements. if no prime element generate exception.
```java
import java.util.Scanner;
public class Main{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[] numbers = new int[10];
        System.out.println("Enter 10 numbers:");
        for (int i = 0; i < 10; i++) {
            numbers[i] = scanner.nextInt();
        }
        try {
            double average = calculatePrimeAverage(numbers);
            System.out.println("The average of prime elements is: " + average);
        } catch (NoPrimeElementException e) {
            System.out.println(e.getMessage());
        }
    }
    private static double calculatePrimeAverage(int[] numbers) throws NoPrimeElementException {
        int sum = 0;
        int count = 0;
        for (int num : numbers) {
            if (isPrime(num)) {
                sum += num;
                count++;
            }
        }
        if (count == 0) {
            throw new NoPrimeElementException("No prime elements found in the array.");
        }
        return (double) sum / count;
    }
    private static boolean isPrime(int num) {
        if (num <= 1) {
            return false;
        }
        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) {
                return false;
            }
        }
        return true;
    }
}
class NoPrimeElementException extends Exception {
    public NoPrimeElementException(String message) {
        super(message);
    }
}
```
----
- write a program to enter two strings and print all common vowels. if no common vowels found generate exception

```java
import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the first string:");
        String firstString = scanner.nextLine();
        System.out.println("Enter the second string:");
        String secondString = scanner.nextLine();
        try {
            Set<Character> commonVowels = findCommonVowels(firstString, secondString);
            System.out.println("Common vowels: " + commonVowels);
        } catch (NoCommonVowelsException e) {
            System.out.println(e.getMessage());
        }
    }
    private static Set<Character> findCommonVowels(String str1, String str2) throws NoCommonVowelsException {
        Set<Character> vowelsInFirst = getVowels(str1);
        Set<Character> vowelsInSecond = getVowels(str2);
        vowelsInFirst.retainAll(vowelsInSecond);
        if (vowelsInFirst.isEmpty()) {
            throw new NoCommonVowelsException("No common vowels found in the strings.");
        }
        return vowelsInFirst;
    }
    private static Set<Character> getVowels(String str) {
        Set<Character> vowels = new HashSet<>();
        for (char ch : str.toLowerCase().toCharArray()) {
            if ("aeiou".indexOf(ch) != -1) {
                vowels.add(ch);
            }
        }
        return vowels;
    }
}
class NoCommonVowelsException extends Exception {
    public NoCommonVowelsException(String message) {
        super(message);
    }
}
```
----
- write a program to make matrix of 5 x 5 by taking inputs and print sum of prime elements of matrix. If no prime number is there generate exception
```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[][] matrix = new int[5][5];
        System.out.println("Enter the elements of a 5x5 matrix:");
        for (int i = 0; i < 5; i++) {
            for (int j = 0; j < 5; j++) {
                matrix[i][j] = scanner.nextInt();
            }
        }
        try {
            int sum = calculatePrimeSum(matrix);
            System.out.println("The sum of prime elements in the matrix is: " + sum);
        } catch (NoPrimeElementException e) {
            System.out.println(e.getMessage());
        }
    }
    private static int calculatePrimeSum(int[][] matrix) throws NoPrimeElementException {
        int sum = 0;
        boolean hasPrime = false;
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                if (isPrime(matrix[i][j])) {
                    sum += matrix[i][j];
                    hasPrime = true;
                }
            }
        }
        if (!hasPrime) {
            throw new NoPrimeElementException("No prime elements found in the matrix.");
        }
        return sum;
    }
    private static boolean isPrime(int num) {
        if (num <= 1) {
            return false;
        }
        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) {
                return false;
            }
        }
        return true;
    }
}
class NoPrimeElementException extends Exception {
    public NoPrimeElementException(String message) {
        super(message);
    }
}
```
