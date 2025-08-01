import java.util.Scanner;

public class DynamicTableCreator {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // 1. Get dimensions for the table from the user
        System.out.print("Enter the number of rows: ");
        int rows = scanner.nextInt();

        System.out.print("Enter the number of columns: ");
        int columns = scanner.nextInt();

        // 2. Create the 2D array based on user input
        int[][] userTable = new int[rows][columns];

        // 3. Take number input for each cell
        System.out.println("\nNow, enter the numbers for each cell:");
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < columns; j++) {
                System.out.printf("Enter number for cell [%d][%d]: ", i, j);
                userTable[i][j] = scanner.nextInt();
            }
        }

        // Close the scanner
        scanner.close();

        // 4. Print the final table
        System.out.println("\nHere is your table:\n");
        printTable(userTable);
    }

    /**
     * Prints a 2D integer array in a table format with dynamic column widths.
     *
     * @param array The 2D integer array to be printed.
     */
    public static void printTable(int[][] array) {
        if (array == null || array.length == 0 || array[0].length == 0) {
            System.out.println("The array is empty or null.");
            return;
        }

        // Find the max width for each column to align numbers
        int[] columnWidths = new int[array[0].length];
        for (int j = 0; j < array[0].length; j++) {
            int maxWidth = 0;
            for (int i = 0; i < array.length; i++) {
                int length = String.valueOf(array[i][j]).length();
                if (length > maxWidth) {
                    maxWidth = length;
                }
            }
            columnWidths[j] = maxWidth;
        }

        // Print the top border
        printHorizontalLine(columnWidths);

        // Print each row
        for (int i = 0; i < array.length; i++) {
            System.out.print("|");
            for (int j = 0; j < array[i].length; j++) {
                String numberString = String.valueOf(array[i][j]);
                int padding = columnWidths[j] - numberString.length();
                
                // Add left padding for right alignment
                for (int k = 0; k < padding; k++) {
                    System.out.print(" ");
                }
                System.out.print(" " + numberString + " |");
            }
            System.out.println();
            
            // Print a separator line after each row
            printHorizontalLine(columnWidths);
        }
    }

    /**
     * A helper method to print a horizontal border line for the table.
     *
     * @param columnWidths An array of the maximum widths of each column.
     */
    private static void printHorizontalLine(int[] columnWidths) {
        System.out.print("+");
        for (int width : columnWidths) {
            // +2 for the space padding on either side of the number
            for (int i = 0; i < width + 2; i++) { 
                System.out.print("-");
            }
            System.out.print("+");
        }
        System.out.println();
    }
}
