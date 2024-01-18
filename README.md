import java.util.Scanner;

public class banksystem {
    public static void main(String[] args) {
        Banksystem bank1 = new Banksystem("XYZ", "01");
        bank1.showMenu();
    }
}

class Banksystem {
    int balance;
    int previousTransaction;

    Banksystem(String cname, String cid) {
        // You might want to use cname and cid to set customer name and ID
    }
    void deposit(int amount) {
        if (amount != 0) {
            balance = balance + amount;
            previousTransaction = amount;
        }
    }

    void withdraw(int amount) {
        if (amount != 0) {
            balance = balance - amount;
            previousTransaction = -amount;
        }
    }

    void getPreviousTransaction() {
        if (previousTransaction > 0) {
            System.out.println("Deposit: " + previousTransaction);
        } else if (previousTransaction < 0) {
            System.out.println("Withdrawn: " + Math.abs(previousTransaction));
        } else {
            System.out.println("No transaction history.");
        }
    }

    void showMenu() {
        Scanner sc = new Scanner(System.in);

        System.out.println("Welcome: " + " customerName");
        System.out.println("Your ID is: " + " costumerid");
        System.out.println();
        char option;

        do {
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
                case 'A' -> {
                    System.out.println("===================");
                    System.out.println("Balance is: " + balance);
                    System.out.println("===================");
                }

                case 'B' -> {
                    System.out.println("====================");
                    System.out.println("Enter the amount to deposit:");
                    int depositAmount = sc.nextInt();
                    deposit(depositAmount);
                    System.out.println("====================");
                }

                case 'C' -> {
                    System.out.println("====================");
                    System.out.println("Enter the amount to withdraw:");
                    int withdrawAmount = sc.nextInt();
                    withdraw(withdrawAmount);
                    System.out.println("====================");
                }

                case 'D' -> {
                    System.out.println("====================");
                    getPreviousTransaction();
                    System.out.println("====================");
                }

                case 'E' -> System.out.println("Exiting the system. Thank you!");

                default -> System.out.println("Invalid Option! Please try again");
            }
        } while (option != 'E');
    }
}
