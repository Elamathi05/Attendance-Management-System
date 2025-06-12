# Attendance-Management-System
import java.util.*;

class Student {
    int id;
    String name;
    boolean isPresent;

    Student(int id, String name) {
        this.id = id;
        this.name = name;
        this.isPresent = false;
    }

    void markPresent() {
        isPresent = true;
    }

    void markAbsent() {
        isPresent = false;
    }

    void displayAttendance() {
        System.out.println(id + " - " + name + " : " + (isPresent ? "Present" : "Absent"));
    }
}

public class AttendanceSystem {
    static Scanner scanner = new Scanner(System.in);
    static List<Student> students = new ArrayList<>();

    public static void main(String[] args) {
        int choice;
        do {
            System.out.println("\n--- Attendance Management System ---");
            System.out.println("1. Add Student");
            System.out.println("2. Mark Attendance");
            System.out.println("3. View Attendance");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            scanner.nextLine();  // consume newline

            switch (choice) {
                case 1:
                    addStudent();
                    break;
                case 2:
                    markAttendance();
                    break;
                case 3:
                    viewAttendance();
                    break;
                case 4:
                    System.out.println("Exiting system.");
                    break;
                default:
                    System.out.println("Invalid choice.");
            }
        } while (choice != 4);
    }

    static void addStudent() {
        System.out.print("Enter student ID: ");
        int id = scanner.nextInt();
        scanner.nextLine();  // consume newline
        System.out.print("Enter student name: ");
        String name = scanner.nextLine();
        students.add(new Student(id, name));
        System.out.println("Student added successfully.");
    }

    static void markAttendance() {
        for (Student student : students) {
            System.out.print("Is " + student.name + " (ID: " + student.id + ") present? (y/n): ");
            String input = scanner.nextLine();
            if (input.equalsIgnoreCase("y")) {
                student.markPresent();
            } else {
                student.markAbsent();
            }
        }
        System.out.println("Attendance marked.");
    }

    static void viewAttendance() {
        System.out.println("\n--- Attendance List ---");
        for (Student student : students) {
            student.displayAttendance();
        }
    }
}
