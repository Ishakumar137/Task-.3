import java.util.Scanner;

public class GradeCalculator {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welcome to the Student Grade Calculator!");

        // Ask for the number of students
        System.out.print("Enter the number of students: ");
        int numStudents = scanner.nextInt();
        scanner.nextLine(); // Consume the newline

        // Arrays to hold student names and grades
        String[] studentNames = new String[numStudents];
        double[] studentGrades = new double[numStudents];

        // Input student names and grades
        for (int i = 0; i < numStudents; i++) {
            System.out.print("Enter name of student " + (i + 1) + ": ");
            studentNames[i] = scanner.nextLine();

            System.out.print("Enter grade for " + studentNames[i] + ": ");
            studentGrades[i] = scanner.nextDouble();
            scanner.nextLine(); // Consume the newline
        }

        // Calculate and display results
        displayResults(studentNames, studentGrades);

        scanner.close();
    }

    public static void displayResults(String[] names, double[] grades) {
        System.out.println("\n--- Student Grades Report ---");
        double total = 0;

        for (int i = 0; i < names.length; i++) {
            total += grades[i];
            System.out.printf("%s: %.2f (%s)%n", names[i], grades[i], getGradeLetter(grades[i]));
        }

        double average = total / names.length;
        System.out.printf("Average Grade: %.2f (%s)%n", average, getGradeLetter(average));
    }

    public static String getGradeLetter(double grade) {
        if (grade >= 90)
            return "A";
        else if (grade >= 80)
            return "B";
        else if (grade >= 70)
            return "C";
        else if (grade >= 60)
            return "D";
        else
            return "F";
    }
}
