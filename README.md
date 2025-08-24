# South-African-ID-Application.
A simple java program that uses some string methods and character methods and user-defined methods to display the ID number in this format: dd/mm/yyyy and also displays the gender.
/*
By Picasso_03
S.A ID Application
18/08/25
*/
import java.util.Scanner;
public class SouthAfricanIDApplication
{
	public static void main(String [] args)
	{
		Scanner kb = new Scanner(System.in);
		
		System.out.print("Enter your ID number: ");
		String ID = kb.nextLine();
		
		while(!ID.equals("*"))
		{
			
		
		boolean isLengthValid = validateLength(ID);
		if(isLengthValid){
		
			String day = ID.substring(4,6);
			
			
			if(validateBornDay(day)){
				int dayOfBirth = Integer.parseInt(day);
				
				String Month = ID.substring(2,4);
				//System.out.print(Month);
				if(validateBornMonth(Month)){
					String year = ID.substring(0,2);
					
					System.out.print(year);
					int yearOfUser = Integer.parseInt(year);
					
					int MonthOfBirsth = Integer.parseInt(Month);
					
					String birthMonth = determineMonth(MonthOfBirsth);
					
					yearOfUser = determineYear(yearOfUser);
					
					String gender = ID.substring(6,7);
					
					int Gender = Integer.parseInt(gender);
					
					String genderType = getGender(Gender);
					
					displaySummary(dayOfBirth, birthMonth,yearOfUser,genderType );
					
				}
			}
	
			
		}else{
			System.out.print("Invalid length");
		}
		System.out.print("Enter your ID number: ");
		ID = kb.nextLine();
		}
		
	}
	
	public static boolean validateLength(String ID)
	{
		boolean isLengthValid = false;
		
		if(ID.length() == 13){
			isLengthValid = true;
		}
		return isLengthValid;
	}
	
	public static boolean validateBornDay(String day)
	{
		boolean isDayValid = false;
		int Day = Integer.parseInt(day);
		if(Day>1 && Day<=31){
			isDayValid = true;
		}
		return isDayValid;
	}
	
	public static boolean validateBornMonth(String MonthOfBirsth)
	{
		boolean isMonthValid = false;
		int Month = Integer.parseInt(MonthOfBirsth);
		if(Month>=1 && Month<=12){
			isMonthValid = true;
		}
		return isMonthValid;
	}
	
	public static String determineMonth(int Month)
	{
		String birthMonth = "";
		switch(Month)
		{
			case 1: birthMonth = "January"; break;
			case 2: birthMonth = "February"; break;
			case 3: birthMonth = "March"; break;
			case 4: birthMonth = "April"; break;
			case 5: birthMonth = "May"; break;
			case 6: birthMonth = "June"; break;
			case 7: birthMonth = "July"; break;
			case 8: birthMonth = "August"; break;
			case 9: birthMonth = "September"; break;
			case 10: birthMonth = "October"; break;
			case 11: birthMonth = "November"; break;
			case 12: birthMonth = "December"; break;
			
		}
		return birthMonth;
	}
	
	public static int determineYear(int yearOfUser)
	{
		int yearOfBirth = 20;
		yearOfBirth += yearOfUser;
		return yearOfBirth;
	}
	
	public static String getGender(int Gender)
	{
		String genderType="";
		if(Gender >=0 && Gender<=4){
			genderType = "Female";
		}else if(Gender>=5 && Gender<=9){
			genderType = "Male";
		}
		return genderType;
	}
	
	public static void displaySummary(int dayOfBirth,  String birthMonth, int yearOfUser, String genderType )
	{
		System.out.print("===============" + "\n Born Date " + dayOfBirth + " " + birthMonth + " " + yearOfUser + " " + "\n Gender: " + genderType + "\n =============");
	}


}
