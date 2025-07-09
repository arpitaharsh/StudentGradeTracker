import java.util.ArrayList;
import java.util.Scanner;

public class GradeTracker {
    static ArrayList<String> students = new ArrayList<>();
    static ArrayList<Double> grades = new ArrayList<>();
    static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        while (true) {
            System.out.println("1. Add Student & Grade");
            System.out.println("2. Calculate Average");
            System.out.println("3. Find Highest/Lowest");
            System.out.println("4. Display Grades");
            System.out.println("5. Exit");
            System.out.print("Choose: ");
            int option = scanner.nextInt();
            scanner.nextLine();

            switch (option) {
                case 1:
                    addStudentGrade();
                    break;
                case 2:
                    calculateAverage();
                    break;
                case 3:
                    findHighestLowest();
                    break;
                case 4:
                    displayGrades();
                    break;
                case 5:
                    System.exit(0);
            }
        }
    }

    static void addStudentGrade() {
        System.out.print("Enter student name: ");
        students.add(scanner.nextLine());
        System.out.print("Enter grade: ");
        grades.add(scanner.nextDouble());
        scanner.nextLine();
    }

    static void calculateAverage() {
        double sum = 0;
        for (double grade : grades) {
            sum += grade;
        }
        System.out.println("Average grade: " + sum / grades.size());
    }

    static void findHighestLowest() {
        double highest = grades.stream().max(Double::compare).get();
        double lowest = grades.stream().min(Double::compare).get();
        System.out.println("Highest: " + highest);
        System.out.println("Lowest: " + lowest);
    }

    static void displayGrades() {
        for (int i = 0; i < students.size(); i++) {
            System.out.println(students.get(i) + ": " + grades.get(i));
        }
    }
}
