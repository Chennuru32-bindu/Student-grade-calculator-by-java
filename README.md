# Student-grade-calculator-by-java
//Student Grade Tracker

import java.util.ArrayList;
import java.util.Scanner;

public class StudentGradeTracker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Integer> grades = new ArrayList<>();

        System.out.println("Enter student grades (-1 to stop):");

        while (true) {
            System.out.print("Enter grade: ");
            int grade = scanner.nextInt();
            
            if (grade == -1) { // Sentinel value to stop input
                break;
            }
            
            if (grade >= 0 && grade <= 100) { // Valid grade range
                grades.add(grade);
            } else {
                System.out.println("Invalid grade! Please enter a value between 0 and 100.");
            }
        }

        scanner.close();

        if (grades.isEmpty()) {
            System.out.println("No grades entered.");
            return;
        }

        // Compute statistics
        int total = 0;
        int highest = grades.get(0);
        int lowest = grades.get(0);

        for (int grade : grades) {
            total += grade;
            if (grade > highest) highest = grade;
            if (grade < lowest) lowest = grade;
        }

        double average = (double) total / grades.size();

        // Display results
        System.out.println("\nGrade Statistics:");
        System.out.println("Total Students: " + grades.size());
        System.out.println("Average Grade: " + String.format("%.2f", average));
        System.out.println("Highest Grade: " + highest);
        System.out.println("Lowest Grade: " + lowest);
    }
}
