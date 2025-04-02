/*
 * CSC-239 JAVA
 * Project 1: Days Since Start of Year
 * Student: Weiquan Mai
 * Date: February 24, 2025
 * Description: This program prompts the user to input a string of text representing a numeric date in the following format: MM DD YYYY
 * The program then calculates and displays the number of days that has elapsed
 * since start of specified year until user specified date.
 */

import java.util.Scanner;

public class DaySinceStartOfYear {
    /*__________________________________________________________________________________________
     * Method main
     * Inputs: An array of three integers or q from getDate method. 
     * Boolean value from validateMonth, validateDay, and validateYear method.
     * Outputs: daysElapsed since start of specified year until specified date.
     * Description: Uses a do-while loop to calculate daysElapsed unless q is entered.
     */
    public static void main (String[] args){
        // Create a scanner
        Scanner input = new Scanner(System.in);

        // Variables
        String[] monthName = {"January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"};
        int [] maxDayPerMonth = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
        int MM, DD, YYYY;
        boolean isValidDate = false;
        boolean keepRunning = true;

        //Explain program and prompt user to enter a string in MM DD YYYY format
        System.out.println("This program accepts numeric dates in MM DD YYYY format.");
        System.out.println("Then calculates the number of days since start of specified year.");
       
        // do-while loop to keep running program unless q is pressed.
        do {
            int [] numbers = getDate();
            if (numbers == null){
                break;
            }
            // Convert numbers array into MM DD YYYY format for better readability
            MM = numbers[0];
            DD = numbers[1];
            YYYY = numbers[2];
            int daysElapsed = 0;
            
            // Determine if the year is a leap year
            boolean isLeapYear = (YYYY % 4 == 0 && YYYY % 100 != 0 || YYYY % 400 == 0);
            
            // If year is a leap year, set max day in February to 29
            if (isLeapYear) {
                maxDayPerMonth[1] = 29;
            } else {maxDayPerMonth[1] = 28;}

            // Validate data input for month, day and year
            isValidDate = validateMonth(MM, DD, YYYY)&& 
            validateDay(DD, maxDayPerMonth[MM-1], MM, YYYY)&&
            validateYear(MM, DD, YYYY);

            // If date is a valid date, then calculate daysElapsed using a for loop and print out daysElapsed
            if(isValidDate){
                for(int i = 1; i < MM; i++)
                {
                    daysElapsed += maxDayPerMonth[i-1];
                }
                daysElapsed += DD;
                System.out.println(daysElapsed + " day has elapsed from Jan 01, " + YYYY + " to " + monthName[MM-1] + " " + DD + ", " + YYYY);
            }
        } while (keepRunning);

        // Close scanner
        input.close();

    } // End of main method

    /*__________________________________________________________________________________________
     * Method getDate
     * Inputs: A string in MM DD YYYY format
     * Outputs: An int array containing three integers.
     * Description: Uses a while loop to continue prompting user to enter a
     * numeric date or q to exit the program. If numeric loop is entered, passes
     * data into validateData method. If numbers are valid, return numbers
     * into an int array in main method.
     */
    public static int[] getDate() {
        // Create a scanner
        Scanner input = new Scanner(System.in);

        int [] numbers = new int [3];

        // Use a while loop to ask user to enter numeric date in MM DD YYYY
        // format or q to exit the program
        while(true){
            System.out.println("Please enter a numeric date (or q to exit program): ");
            String date = input.nextLine();
            
            /* Utilize date.equalsIgnoreCase("q") instead of 
            date == "q" || date == "Q" because q is a char and it going to be
            returned into an int array in main
             */ 
            if(date.equalsIgnoreCase("q")){
                System.out.println("Exit program.");
                return null;
            }

            String [] digit = date.split(" ");
            numbers = validateData(digit);

            if (numbers != null)
            {
                return numbers;
            } 
        }
    } // End of getDate method

    /*__________________________________________________________________________________________
     * Method validateData
     * Inputs: String array from getDate method
     * Outputs: Int array of three integers
     * Description: Validates string array from getDate method using try/catch.
     * If date is valid, then return date as an array of three integers.
     */
    public static int[] validateData(String[] digit) {
        int [] validate = new int [3];

        // Utilize try/catch and for loop to validate data entered by user
        // If data entered can be parsed as an int, return validate
        // If data entered cannot be parsed, then return error message
        try {
            for (int i = 0; i < 3; i++) {
                validate[i] = Integer.parseInt(digit[i]);
            }
            return validate;
        } catch (NumberFormatException ex) {
            System.out.println("Non-numeric data entered: " + digit[0] + " " + digit[1] + " " + digit[2] );
            return null;
        }
    } // End of validateData method

    /*__________________________________________________________________________________________
     * Method validateMonth
     * Inputs: MM, DD, YYYY from main method
     * Outputs: Boolean true/false value
     * Description: Input validation for MM. If MM is less than 1 or greater than 12, return false and generate an error message.
     * Otherwise, return true into main method
     */
    public static boolean validateMonth (int month, int day, int year){
        if (month < 1 || month > 12){
            System.out.println("ERROR: Invalid numeric month: " + month);
            System.out.println("Error: Invalid Date string \"" + month + " " + day + " " + year + " \"resulted in invalid numeric date:");
            System.out.println("month=" + month + ", day=" + day + ", year=" + year);
            return false;
        }
        return true;
    } // End of validateMonth method

    /*__________________________________________________________________________________________
     * Method validateDay
     * Inputs: MM, maxDayPerMonth[MM-1], DD, YYYY 
     * Outputs: Boolean true/false value
     * Description: Input validation for day. If DD is greater than maximum day
     * in month, then return false and generate an error message.
     * Otherwise, return true into main method.
     */
    public static boolean validateDay (int day, int max, int month, int year){
        if (day > max){
            System.out.println("ERROR: Invalid day " + day + ", for numeric month: " + month + " (year = " + year + ")");
            System.out.println("Error: Invalid Date string \"" + month + " " + day + " " + year + " \"resulted in invalid numeric date:");
            System.out.println("month=" + month + ", day=" + day + ", year=" + year);
            return false;
        }
        return true;
    } // End of validateDay method

    /*__________________________________________________________________________________________
     * Method 
     * Inputs: MM, DD, YYYY
     * Outputs: Boolean true/false value
     * Description: Input validation for year. If year is less than 1900 or
     * greater than 2100, return false and generate an error message.
     * Otherwise, return true into main method.
     */
    public static boolean validateYear(int month, int day, int year){
        if (year < 1900 || year > 2100){
            System.out.println("ERROR: Invalid year " + year + ". Year must be between 1900 and 2100.");
            System.out.println("Error: Invalid Date string \"" + month + " " + day + " " + year + " \"resulted in invalid numeric date:");
            System.out.println("month=" + month + ", day=" + day + ", year=" + year);
            return false;
        }
        return true;
    } // End of validateYear method
}
