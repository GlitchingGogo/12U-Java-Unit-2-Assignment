# 12U-Java-Unit-2-Assignment
Project by Brandon WD

## Question 1
Instructions: Write a banking program/class. It should handle deposits, withdrawals, interest charge, and have all
attributes you think is necessary (Like total savings). Your program will repeatedly prompt the user for
deposit or withdrawals. Program is to prompt user if they would like to exit after each transaction.

Source Code -
Main:
```
// Question 1 - ICS4U1 Unit 2 Assignment
// Brandon Wong-Dearing
// Teacher: Mr. Naccarto

import java.util.Scanner;

class Main
{
  public static void main(String[] args)
  {
    // Create new instance
    Bank userAccount = new Bank();
    // Variable Init
    String userSelection;
    int transactionCount = 0;

    // While loop until user quits
    while(true)
    {
      Scanner in = new Scanner(System.in);
      double userAmount;
      String format userAmount;
      System.out.print("Please enter deposit, withdraw or exit: ")
      // Gather user input
      userSelection = in.nextLine();
      //Check for deposit
      if("deposit".equals(userChoice))
      {
        System.out.print("Enter the amount you wish to deposit: ")
        // While loop until valid input is gathered
        while(true)
        {
          //Get user $
          String userInput = in.nextLine();
          try
          {
            // Convert to double
            userAmount = Double.parseDouble(userInput);
            // Ensure positive
            if(userAmount<0)
            {
              System.out.println("Please enter a valid, positive number.")
              System.out.print("Enter the amount you wish to withdraw: ");
            }
            else
            {
              break;
            }
          }
          catch(Exception e)
          {
            System.out.print("Please enter a proper number: ");

          }
          // Format user amount to 2 decimal places
          formatUserAmount = String.format("%.2f", userAmount);
          // Convert to Double
          userAmount = Double.parseDouble(formatUserAmount);
          // Call method to deposit
          userAccount.deposit(userAmount);
          System.out.println();
          // If useramount != 0, increase transaction counter
          if(userAmount != 0)
          {
            transactionCount ++;
          }
          //If counter >= 3, interest charge is taken
          if(transactionCount>=3)
          {
            userAccount.addInterest();
            System.out.println("An interest charge of $25 has been subtracted from your account\n");
            transactionCount = 0;
          }
          // Format total to 2 decimal places, print total savings
          String totalSavings = String.format("%.2f", userAccount.getTotalSavings());
          System.out.print("Your account has a total savings of $" + totalSavings+"\n\n");
        }
        // Check to see if user wants to withdraw
        else
        if("withdraw".equals(userSelection))
        {
          System.out.print("Enter the amount you want to withdraw: ");
          // while loop to ensure proper $ amount
          while(true)
          {
            // get $ input
            String userAmount = in.nextLine();
            // check to ensure proper format
            try
            {
              // convert to double
              userAmount = Double.parseDouble(userAmount)
              // check for positive
              if(userAmount<0)
              {
                System.out.println("Please enter a positive amount.");
                System.out.print("Enter the amount you want to withdraw: ")
              }
              // Check user has enough $
              else if(userAmount<=userAccount.getTotalSavings())
              {
                break;
              }
              // Allow user to quit without withdrawing
              if(userAccount.getTotalSavings()< 0 && userAmount==0)
              {
                break;
              }
              else
              {
                System.out.println("You do not have enough savings to withdraw"+userAmount);
                System.out.print("Enter the amount you want to withdraw: ");
              }
            }
            catch(Exception e)
            {
              System.out.print("Please enter a proper number: ");
            }
            // Change to 2 dec places
            formatUserAmount = String.format("&.2f", userAmount);
            // Conv to dbl
            userAmount = Double.parseDouble(formatUserAmount);
            // Call method from class to withdraw
            userAccount.withdraw(userAmount);
            System.out.println();
            if(userAmount != 0)
            {
              transactionCount ++;
            }
            if(transactionCount>=3)
            {
              userAccount.addInterest();
              System.out.println("An interest charge of $25 has been subtracted from your account\n");
              transactionCount = 0;
            }
            String totalSavings = String.format("%.2f", userAccount.getTotalSavings());
            System.out.print("Your account has a total savings of $" + totalSavings+"\n\n");
          }
          // Check to see if user wants to stop
          elseif("stop".equals(userSelection))
          {
            break;
          }
        }
        // Display total savings again
      }
      System.out.println("\n You have a total savings of $"+userAccount.getTotalSavings());
    }
  }
}
```

Bank Class:
```
public class Bank
{
  // var init
  private double deposits;
  private double withdrawals;
  private double interestCharge;
  private double totalSavings

  // Create base values for vars
  public Bank()
  {
    deposits = 0;
    withdrawals = 0;
    totalSavings = 0;
    interestCharge = 25;
  }
  // Method for deposit
  public void deposit(double amount)
  {
    totalSavings += amount;
  }
  // Method for withdraw
  public void withdraw(double amount)
  {
    totalSavings -= amount;
  }
  // Method for interest
  public void addInterest
  {
    totalSavings = totalSavings - interestCharge;
  }
  // Method to return total savings
  public double getTotalSavings()
  {
    return totalSavings;
  }
}
```

Sample Output:
```//x```

## Question 2
Instructions: Modify your program in the previous question. It should have a GUI. For the beginning it will have a login
screen (Make changes to your classes to handle passwords and usernames.). Your graphics should have
a deposit screen and a withdrawal screen after login

Source Code -
Main:
```
// Question 2 - ICS4U1 Unit 2 Assignment
// Brandon Wong-Dearing
// Teacher: Mr. Naccarto

import java.util.Scanner;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

class Main
{
  public static void main(String[] args)
  {
    // Create new instance
    Bank userAccount = new Bank();
    JFrame window = new Jframe("Bank");
    window.setSize(640,480);
    window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    JPanel loginPanel = new JPanel(newGridBagLayout());
    GridBagConstraints loginConstraints = new GridBagConstraints();
    JLabel login = new JLabel("Login");
    JTextField username = new JTextField("Username");
    loginPanel.add(username);
    JTextField password = new JTextField("Password");
    loginPanel.add(password);
    JButton submit = new JButton ("Submit");

    JFrame optionsWindow = new JFrame("Bank");
    optionsWindow.setSize(640,480);
    optionsWindow.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    JPanel optionsPanel = new JPanel(new GridBagLayout());
    GridBagConstraints optionsConstraints = new GridBagConstraints();
    JButton deposit = new JButton ("Deposit");
    optionPanel.add(deposit);
    JButton withdraw = new JButton ("Withdraw");
    optionPanel.add(withdraw);

    JFrame depositWindow = new JFrame("Bank");
    depositWindow.setSize(640,480);
    
    // Variable Init
    String userSelection;
    int transactionCount = 0;

    // While loop until user quits
    while(true)
    {
      Scanner in = new Scanner(System.in);
      double userAmount;
      String format userAmount;
      System.out.print("Please enter deposit, withdraw or exit: ")
      // Gather user input
      userSelection = in.nextLine();
      //Check for deposit
      if("deposit".equals(userChoice))
      {
        System.out.print("Enter the amount you wish to deposit: ")
        // While loop until valid input is gathered
        while(true)
        {
          //Get user $
          String userInput = in.nextLine();
          try
          {
            // Convert to double
            userAmount = Double.parseDouble(userInput);
            // Ensure positive
            if(userAmount<0)
            {
              System.out.println("Please enter a valid, positive number.")
              System.out.print("Enter the amount you wish to withdraw: ");
            }
            else
            {
              break;
            }
          }
          catch(Exception e)
          {
            System.out.print("Please enter a proper number: ");

          }
          // Format user amount to 2 decimal places
          formatUserAmount = String.format("%.2f", userAmount);
          // Convert to Double
          userAmount = Double.parseDouble(formatUserAmount);
          // Call method to deposit
          userAccount.deposit(userAmount);
          System.out.println();
          // If useramount != 0, increase transaction counter
          if(userAmount != 0)
          {
            transactionCount ++;
          }
          //If counter >= 3, interest charge is taken
          if(transactionCount>=3)
          {
            userAccount.addInterest();
            System.out.println("An interest charge of $25 has been subtracted from your account\n");
            transactionCount = 0;
          }
          // Format total to 2 decimal places, print total savings
          String totalSavings = String.format("%.2f", userAccount.getTotalSavings());
          System.out.print("Your account has a total savings of $" + totalSavings+"\n\n");
        }
        // Check to see if user wants to withdraw
        else
        if("withdraw".equals(userSelection))
        {
          System.out.print("Enter the amount you want to withdraw: ");
          // while loop to ensure proper $ amount
          while(true)
          {
            // get $ input
            String userAmount = in.nextLine();
            // check to ensure proper format
            try
            {
              // convert to double
              userAmount = Double.parseDouble(userAmount)
              // check for positive
              if(userAmount<0)
              {
                System.out.println("Please enter a positive amount.");
                System.out.print("Enter the amount you want to withdraw: ")
              }
              // Check user has enough $
              else if(userAmount<=userAccount.getTotalSavings())
              {
                break;
              }
              // Allow user to quit without withdrawing
              if(userAccount.getTotalSavings()< 0 && userAmount==0)
              {
                break;
              }
              else
              {
                System.out.println("You do not have enough savings to withdraw"+userAmount);
                System.out.print("Enter the amount you want to withdraw: ");
              }
            }
            catch(Exception e)
            {
              System.out.print("Please enter a proper number: ");
            }
            // Change to 2 dec places
            formatUserAmount = String.format("&.2f", userAmount);
            // Conv to dbl
            userAmount = Double.parseDouble(formatUserAmount);
            // Call method from class to withdraw
            userAccount.withdraw(userAmount);
            System.out.println();
            if(userAmount != 0)
            {
              transactionCount ++;
            }
            if(transactionCount>=3)
            {
              userAccount.addInterest();
              System.out.println("An interest charge of $25 has been subtracted from your account\n");
              transactionCount = 0;
            }
            String totalSavings = String.format("%.2f", userAccount.getTotalSavings());
            System.out.print("Your account has a total savings of $" + totalSavings+"\n\n");
          }
          // Check to see if user wants to stop
          elseif("stop".equals(userSelection))
          {
            break;
          }
        }
        // Display total savings again
      }
      System.out.println("\n You have a total savings of $"+userAccount.getTotalSavings());
    }
  }
}
```

X Class:
```//x```

Sample Output:
```//x```

## Question 3
Instructions: Create a dice rolling game. Each player rolls two dice. The roll numbers are to be added together until
one of the player gets to 100. If a player rolls snake eyes (two 1s) the player’s score is reset. If the player
rolls a lucky 7 (Any combination to 7) have the player gain an extra 7 points (So 14 points). Each player
has the choice to pass their turn. The player keeps rolling until they get 21 points. Anymore and they lose
all points in the round and the round goes to the next player, if they reach 21 the round passes to the next
player, player keeps his points. This program is to have graphics for the dice. Your dice is to be its own
class. It’s to have methods to change its picture and randomize numbers for its roll. Your main game is to
have a button for the dice roll, the images of the rolled dice, and the points for each player. The game is to
have a pop up when stating which player wins when it’s game over.

Source Code -
Main:
```//x```

X Class:
```//x```

Sample Output:
```//x```

## Question 4
Instructions: Create a phonebook application. Your program is to be have a person class. Its attributes should be,
name, last name, address, and phone number. Write your program to take in people’s information until the
user enters “-1” at any point. Output the collection of data when the program has ended (Store your info in
an array of size 50).

Source Code -
Main:
```
// Question 4 - ICS4U1 Unit 2 Assignment
// Brandon Wong-Dearing
// Teacher: Mr. Naccarto
import java.util.Scanner;

class Main
{
  // Create var --> Total people added
  static int counter;
  public static void main(String[] args)
  {
    // Create instance for people class
    Person adding = new Person("Brandon","WD","Thornhill",1231231);
    // create instance for phonebook class
    Phonebook user = new Phonebook();

    System.out.println("\n Phonebook: ")
    // Ask for user input until user stops or cap at 50 people added
    while(true)
    {
      // Scaner Init
      Scanner input = new Scanner(System.in);
      System.out.print("\nPlease enter a name or enter -1 to stop: ")
      // user input --> name
      String contactName = input.nextLine();
      // Check for stop
      if(contactName.equals("-1"))
      {
        break;
      }
      System.out.print("Please enter a family name or enter -1 to stop: ");
      // user input --> family name
      String contactFamilyName = input.nextLine();
      if(contactFamilyName.equals("-1"))
      {
        break;
      }
      System.out.print("Please enter an address or enter -1 to stop: ");
      // user input --> address
      String contactAddress = input.nextLine();
      if(contactAddress.equals("-1"))
      {
        break;
      }
      System.out.print("Please enter a phone number or enter -1 to stop: ");
      // user input --> phone number
      int contactPhoneNumber;
      while(true)
      {
        Scanner inputs = new Scanner(System.in);
        // Check that input is int
        try
        {
          contactPhoneNumber = inputs.nextInt();
          break;
        }
        catch(Exception e)
        {
          System.out.print("Please enter a proper phone number:")
        }
      }
      if(contactPhoneNumber==-1)
      {
        break;
      }
      // Call method to add all info to phonebook
      user.addingToPhonebook(contactName,contactFamilyName,contactAddress,contactPhoneNumber);
      // Check if max 50 people is reached
      if(counter>=50)
      {
        break;
      }
      //Otherwise increase counter
      counter++;
    }
    //Print all phonebook contacts
    for(int x=0; x<=(counter-1); x++)
    {
      user.returningInfo(x);
    }
  }
}
```

Person Class:
```
public class Person
{
  // Var init
  public String name;
  public String lastName;
  public String address;
  public int phoneNumber;

  // Create method to contain all aspects
  public Person(String name, String lastName, String address, int phoneNumber)
  {
    this.name = name;
    this.lastName = lastName;
    this.address = address;
    this.phoneNumber = phoneNumber;
  }
}
```

Phonebook Class:
```
public class Phonebook
{
  // Init array of people
  public Person [] phonebook = new Person[51];
  // Create counter to track locations
  private int location;

  // Method to add to Phonebook
  public void addingToPhonebook(String name, String lastName, String address, int phoneNumber)
  {
    phonebook[location] = new Person(name, lastName, address, phoneNumber);
    // increase location ++ 1
  }
  // Create method to print all contacts
  public void returningInfo(int x)
  {
    System.out.println("\nPerson #" + (x+1));
    System.out.println("Name: "+phonebook[x].name);
    System.out.println("Family Name: "+phonebook[x].lastName);
    System.out.println("Address: "+phonebook[x].address);
    System.out.println("Phone #: "+phonebook[x].phoneNumber)+"\n");
  }
}
```

Sample Output:
```//x```

