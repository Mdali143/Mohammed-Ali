import java.util.Scanner;

public class SimpleCalculator {

    // Methods for each operation
    public static double add(double a, double b) {
        return a + b;
    }

    public static double subtract(double a, double b) {
        return a - b;
    }

    public static double multiply(double a, double b) {
        return a * b;
    }

    public static double divide(double a, double b) {
        if (b == 0) {
            System.out.println("Error: Cannot divide by zero!");
            return Double.NaN; // Not a Number
        }
        return a / b;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        boolean keepRunning = true;

        while (keepRunning) {
            System.out.println("\nSimple Calculator");
            System.out.println("Choose an operation: +, -, *, /");
            System.out.print("Enter operator: ");
            char operator = scanner.next().charAt(0);

            if (operator != '+' && operator != '-' && operator != '*' && operator != '/') {
                System.out.println("Invalid operator! Please enter one of +, -, *, /.");
                continue; // Skip the rest and prompt the user again
            }

            System.out.print("Enter first number: ");
            while (!scanner.hasNextDouble()) {
                System.out.println("Invalid input. Please enter a valid number.");
                scanner.next(); // Clear the invalid input
            }
            double num1 = scanner.nextDouble();

            System.out.print("Enter second number: ");
            while (!scanner.hasNextDouble()) {
                System.out.println("Invalid input. Please enter a valid number.");
                scanner.next(); // Clear the invalid input
            }
            double num2 = scanner.nextDouble();

            double result;

            switch (operator) {
                case '+':
                    result = add(num1, num2);
                    break;
                case '-':
                    result = subtract(num1, num2);
                    break;
                case '*':
                    result = multiply(num1, num2);
                    break;
                case '/':
                    result = divide(num1, num2);
                    break;
                default:
                    System.out.println("Invalid operator!");
                    continue;
            }

            System.out.println("Result: " + result);

            // Ask user if they want to continue
            System.out.print("\nDo you want to perform another calculation? (yes/no): ");
            String response = scanner.next();
            if (response.equalsIgnoreCase("no")) {
                keepRunning = false;
            }
        }

        System.out.println("Thanks for using the calculator!");
        scanner.close();
    }
}

