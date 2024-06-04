import java.util.ArrayList;
import java.util.Scanner;

// Student class to represent student details
class Student {
    private String name;
    private int age;
    private String id;

    // Constructor to initialize student details
    public Student(String name, int age, String id) {
        this.name = name;
        this.age = age;
        this.id = id;
    }

    // Getter for student ID
    public String getId() {
        return id;
    }

    // toString method to represent student details as a string
    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", id='" + id + '\'' +
                '}';
    }
}

// Main class to manage student details
public class
StudentManagementSystem {
    // ArrayList to store the list of students
    private ArrayList<Student> students;

    // Constructor to initialize the student list
    public StudentManagementSystem() {
        students = new ArrayList<>();
    }

    // Method to add a new student
    public void addStudent(String name, int age, String id) {
        Student student = new Student(name, age, id);
        students.add(student);
    }

    // Method to display the details of a student by ID
    public void displayStudent(String id) {
        for (Student student : students) {
            if (student.getId().equals(id)) {
                System.out.println(student);
                return;
            }
        }
        System.out.println("Student not found!");
    }

    // Method to list all students
    public void listStudents() {
        for (Student student : students) {
            System.out.println(student);
        }
    }

    // Main method to run the program
    public static void main(String[] args) {
        StudentManagementSystem sms = new StudentManagementSystem();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1. Add Student");
            System.out.println("2. Display Student");
            System.out.println("3. List Students");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume the newline

            switch (choice) {
                case 1:
                    System.out.print("Enter name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter age: ");
                    int age = scanner.nextInt();
                    scanner.nextLine(); // Consume the newline
                    System.out.print("Enter ID: ");
                    String id = scanner.nextLine();
                    sms.addStudent(name, age, id);
                    break;
                case 2:
                    System.out.print("Enter student ID: ");
                    id = scanner.nextLine();
                    sms.displayStudent(id);
                    break;
                case 3:
                    sms.listStudents();
                    break;
                case 4:
                    System.out.println("Exiting...");
                    scanner.close();
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
}
}
}
