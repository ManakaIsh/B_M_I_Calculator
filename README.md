package bmicalculator;

import java.util.Scanner;
import java.util.Locale;

public class BmiCalculator {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		 scanner.useLocale(Locale.US);
		
		 char repeat = 0;
		 
		 	do {
		 		
		 		//all code
		 		int unitChoice = getUnitChoice(scanner);
		 		
		 		double weight = (unitChoice == 1) ? getValidInput(scanner, "enter your weight in kilograms: ", 10, 600)
		 				: getValidInput(scanner, "Enter your weight in pounds: ", 22, 1300);
		 		
		 		double height = (unitChoice == 1) ? getValidInput(scanner, " Enter your height in meters: ", 0.5, 2.5)
		 				: getValidInput(scanner, "Enter your height in inches: ", 20, 100);
		 		
		 		double bmi = calculateBMI(unitChoice, weight, height);
		 		System.out.println("Your BMI is " + bmi);
		 		
		 		if(bmi < 16.0)
		 			System.out.println("You are: Serverely underweight");
		 			else if(bmi >= 16.0 && bmi <= 18.4) 
		 				System.out.println("You are: Underweight");
		 				else if(bmi >= 18.5 && bmi <=24.9)
		 					System.out.println("You are: Normal");
		 						else if(bmi >= 25.0 && bmi <=29.9)
		 							System.out.println("You are: Overweight");
		 							else if(bmi >= 30.0 && bmi <=34.9)
		 								System.out.println("You are: Moderate obese");
		 								else if(bmi >= 35.0 && bmi <=39.9)
		 									System.out.println("You are: Severly obese");
		 								else
		 									System.out.println("You are: Morbidly Obese");
		 		
		 		System.out.println("world you like recommendation to stay healthy (Yes/No): ");
		 		
		 		String response = scanner.nextLine();
		 		response = scanner.nextLine();
		 		
		 		if (response.equalsIgnoreCase( "yes")) {
		 			System.out.println("eat health and execise");
		 			}else if(response.equalsIgnoreCase("no"))
		 				System.exit(0);
		 			else
		 				System.out.println("Invalid input please rerun the program");
		 		
		 		
		 		//repeat = askToRepeat(scanner);
		 		System.out.println();
		 		
		 	} while (repeat == 'Y' || repeat == 'y');

	}
	
	// unit - metrics and imperial
	public static int getUnitChoice(Scanner scanner) {
		int choice;
		
			while(true) {
				System.out.print("Select a preferred unit:\n"
						+ "1. metrics (kg, m)\n"
						+ "2. Imperial (lbs, in)\n"
						+ "Please select either option 1 or option 2: ");
				if(scanner.hasNextInt()) {
					choice = scanner.nextInt();
					if (choice == 1 || choice == 2) {
						break;
					}else {
						System.out.println("Invalid choice. Please select 1 or 2");
					}
				}else {
					System.out.println("invalid input. Please enter a number (1 or 2)");
					scanner.next();
				}
			}
		
		return choice;
	}
	
	
	public static double getValidInput(Scanner scanner, String prompt, double min, double max) {
		double value;
		
		while(true) {
			System.out.println(prompt);
			if (scanner.hasNextDouble()) {
				value = scanner.nextDouble();
				if(value >= min && value <= max) {
					break;
				}else {
					System.out.printf("Please enter a value between %.1f and %.1f./n", min, max);
				}
			}else {
				System.out.print("Invalid input. Please enter a value");
				scanner.next();
			}
		}
		return value;
	}
	
	public static double calculateBMI(int unitChoice, double weight, double height){
		double totalBMI;
		
		if(unitChoice == 1){
			totalBMI = weight / (height * height);
		}else {
			totalBMI = (703 * weight) /(height / height);
		}
		return totalBMI;
	
	}
	
}
