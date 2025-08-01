import java.util.Scanner;

public class GradeChecker {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        getInfo(input);
        input.close();
    }

    public static void getInfo(Scanner input) {
        System.out.print("Enter your name: ");
        String name = input.nextLine();

        System.out.print("Enter your grade (A+, A, B, etc): ");
        String grade = input.nextLine();

        checkWithIfElse(grade);
        checkWithSwitch(grade);
    }

    public static void checkWithIfElse(String grade) {
        if (grade.equals("A+")) {
            System.out.println("You got grade A+");
        } else if (grade.equals("A")) {
            System.out.println("You got grade A");
        } else if (grade.equals("B")) {
            System.out.println("You got grade B");
        } else {
            System.out.println("Unknown grade");
        }
    }

    public static void checkWithSwitch(String grade) {
        switch (grade) {
            case "A+":
            case "A":
                System.out.println("Excellent");
                break;
            case "B":
                System.out.println("Good");
                break;
            default:
                System.out.println("No comment");
        }
    }
}
