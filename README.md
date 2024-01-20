import java.util.Scanner;

public class BankSystem {
    private int balance;
    private int previousTransaction;
    private String customerName;
    private String customerID;

    public BankSystem(String cname, String cid) {
        customerName = cname;
        customerID = cid;
    }

    public void deposit(int amount) {
        if (amount != 0) {
            balance = balance + amount;
            previousTransaction = amount;
        }
    }

    public void withdraw(int amount) {
        if (amount != 0) {
            balance = balance - amount;
            previousTransaction = -amount;
        }
    }

    public void getPreviousTransaction() {
        if (previousTransaction > 0) {
            System.out.println("Deposit: " + previousTransaction);
        } else if (previousTransaction < 0) {
            System.out.println("Withdrawn: " + Math.abs(previousTransaction));
        } else {
            System.out.println("No transaction history.");
        }
    }

    public void showMenu() {
        Scanner sc = new Scanner(System.in);
        char option;

        do {
            System.out.println("====================");
            System.out.println("Welcome: " + customerName);
            System.out.println("Your ID is: " + customerID);
            System.out.println();
            System.out.println("====================");
            System.out.println("A. Check balance");
            System.out.println("B. Deposit");
            System.out.println("C. Withdraw");
            System.out.println("D. Previous Transaction");
            System.out.println("E. Exit");
            System.out.println("====================");
            System.out.println("Enter the option:");

            option = sc.next().charAt(0);

            switch (option) {
                case 'A':
                    System.out.println("===================");
                    System.out.println("Balance is: " + balance);
                    System.out.println("===================");
                    break;

                case 'B':
                    System.out.println("====================");
                    System.out.println("Enter the amount to deposit:");
                    int depositAmount = sc.nextInt();
                    deposit(depositAmount);
                    System.out.println("====================");
                    break;

                case 'C':
                    System.out.println("====================");
                    System.out.println("Enter the amount to withdraw:");
                    int withdrawAmount = sc.nextInt();
                    withdraw(withdrawAmount);
                    System.out.println("====================");
                    break;

                case 'D':
                    System.out.println("====================");
                    getPreviousTransaction();
                    System.out.println("====================");
                    break;

                case 'E':
                    System.out.println("Exiting the system. Thank you!");
                    break;

                default:
                    System.out.println("Invalid Option! Please try again");
                    break;
            }
        } while (option != 'E');
    }

    public static void main(String[] args) {
        BankSystem bank1 = new BankSystem("fed", "SL900201");
        bank1.showMenu();
    }
}
