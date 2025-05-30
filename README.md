// Person.java
class Person {
    String name;
    int age;

    // a. Default age of person should be 18;
    // Constructor 1: Initializes with default age if only name is provided
    public Person(String name) {
        this.name = name;
        this.age = 18; // Default age
    }

    // b. A person object can be initialized with name and age;
    // Constructor 2: Initializes with both name and age
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // c. Method to display name and age of person
    public void displayPersonInfo() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }

    public static void main(String[] args) {
        // Creating a person with default age
        System.out.println("Person 1 (Default Age):");
        Person person1 = new Person("Alice");
        person1.displayPersonInfo();
        System.out.println();

        // Creating a person with specified name and age
        System.out.println("Person 2 (Specified Age):");
        Person person2 = new Person("Bob", 30);
        person2.displayPersonInfo();
        System.out.println();

        // Another example with default age
        System.out.println("Person 3 (Default Age):");
        Person person3 = new Person("Charlie");
        person3.displayPersonInfo();
        System.out.println();
    }
}




// Product.java
public class Product {
    private int pid;
    private double price;
    private int quantity;

    // Parameterized constructor
    public Product(int pid, double price, int quantity) {
        this.pid = pid;
        this.price = price;
        this.quantity = quantity;
    }

    // Getter methods to access private properties
    public int getPid() {
        return pid;
    }

    public double getPrice() {
        return price;
    }

    public int getQuantity() {
        return quantity;
    }
}


import java.util.Scanner;

// ProductMain.java
public class ProductMain {

    // c. Method to calculate and return the total amount spent on all products
    public static double calculateTotalAmountSpent(Product[] products) {
        double totalAmount = 0.0;
        for (Product product : products) {
            // amount spent on single product = price of product * quantity of product
            totalAmount += product.getPrice() * product.getQuantity();
        }
        return totalAmount;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Product[] productArray = new Product[5]; // Array to store 5 Product objects

        // a. Accept five product information from user and store in an array
        System.out.println("Please enter details for 5 products:");
        for (int i = 0; i < 5; i++) {
            System.out.println("\n--- Product " + (i + 1) + " ---");
            System.out.print("Enter Product ID (PID): ");
            int pid = scanner.nextInt();

            System.out.print("Enter Price: ");
            double price = scanner.nextDouble();

            System.out.print("Enter Quantity: ");
            int quantity = scanner.nextInt();

            productArray[i] = new Product(pid, price, quantity);
        }

        // b. Find Pid of the product with the highest price.
        int pidWithHighestPrice = -1; // Initialize with a default invalid PID
        double highestPrice = -1.0; // Initialize with a value lower than any possible price

        if (productArray.length > 0) {
            // Initialize with the first product's details
            highestPrice = productArray[0].getPrice();
            pidWithHighestPrice = productArray[0].getPid();

            // Iterate from the second product to find the highest price
            for (int i = 1; i < productArray.length; i++) {
                if (productArray[i].getPrice() > highestPrice) {
                    highestPrice = productArray[i].getPrice();
                    pidWithHighestPrice = productArray[i].getPid();
                }
            }
        }

        System.out.println("\n--- Analysis Results ---");
        System.out.println("Product with the highest price:");
        System.out.println(" Product ID: " + pidWithHighestPrice);
        System.out.println(" Highest Price: " + String.format("%.2f", highestPrice)); // Format to 2 decimal places

        // c. Calculate and display the total amount spent on all products
        double totalAmount = calculateTotalAmountSpent(productArray);
        System.out.println("\nTotal amount spent on all products: " + String.format("%.2f", totalAmount));

        scanner.close(); // Close the scanner to prevent resource leaks
    }
}


class Account:
    """
    A simple class to represent a bank account.
    """

    def __init__(self, initial_balance=0.0):
        """
        Constructor for the Account class.

        Args:
            initial_balance (float): The initial balance for the account.
                                     Defaults to 0.0 if no argument is provided (no-argument constructor behavior).
        """
        if not isinstance(initial_balance, (int, float)):
            raise ValueError("Initial balance must be a number.")
        if initial_balance < 0:
            raise ValueError("Initial balance cannot be negative.")
        self.Balance = float(initial_balance)
        print(f"Account created with initial balance: {self.Balance:.2f}")

    def deposit(self, amount):
        """
        Deposits a specified amount into the account.

        Args:
            amount (float): The amount to deposit.
        """
        if not isinstance(amount, (int, float)):
            raise ValueError("Deposit amount must be a number.")
        if amount <= 0:
            raise ValueError("Deposit amount must be positive.")
        self.Balance += amount
        print(f"Deposited: {amount:.2f}. New balance: {self.Balance:.2f}")

    def withdraw(self, amount):
        """
        Withdraws a specified amount from the account.

        Args:
            amount (float): The amount to withdraw.
        """
        if not isinstance(amount, (int, float)):
            raise ValueError("Withdrawal amount must be a number.")
        if amount <= 0:
            raise ValueError("Withdrawal amount must be positive.")
        if amount > self.Balance:
            print(f"Insufficient funds. Current balance: {self.Balance:.2f}. Attempted to withdraw: {amount:.2f}")
        else:
            self.Balance -= amount
            print(f"Withdrew: {amount:.2f}. New balance: {self.Balance:.2f}")

    def display_balance(self):
        """
        Displays the current balance of the account.
        """
        print(f"Current Account Balance: {self.Balance:.2f}")
