

# Banking Application

## Overview
This Banking Application is a simple console-based system that allows clients and employees to interact with various banking functionalities such as managing accounts, transactions, branches, and employees. The application supports user authentication, account management, branch management, and employee management.

## Features

### Client Features
- View accounts
- Create a new account
- Make a transaction
- Make a deposit
- Make a withdrawal
- View transaction history
- Loan options (to be implemented)

### Employee Features
- View all branches
- View employee details
- Delete branches
- Edit branches
- Add branches

## Project Structure

```
src/
├── main/
│   └── BankApp.java
├── Branches/
│   └── Branch.java
├── Models/
│   ├── Account.java
│   ├── Transaction.java
│   └── Loan.java
├── Client/
│   ├── Client.java
│   └── ClientService.java
├── Collections/
│   ├── AccountCollection.java
│   ├── EmployeeCollection.java
│   └── TransactionCollection.java
├── Employee/
│   ├── Employee.java
│   └── EmployeeService.java
└── data/
    ├── clients.ser
    ├── employees.ser
    └── accounts/
        ├── accounts_1.ser
        └── accounts_2.ser
```


1. **Compile the Code**
   ```sh
   javac -d bin src/main/BankApp.java
   ```

2. **Run the Application**
   ```sh
   java -cp bin main.BankApp
   ```

## Usage

### Role Selection Menu
1. I am a client
2. I am an employee
0. Exit

### Client Menu
1. View Accounts
2. Create Account
3. Make a transaction
4. Make a deposit
5. Make a withdrawal
6. View transaction history
7. Loans options
0. Logout and Exit

### Employee Menu
1. See all branches
2. See employee details
3. Delete branches
4. Edit branches
5. Add branches
0. Logout and Exit

## Adding New Branches

When adding new branches, the application checks if the branch ID already exists. If it does, the user is prompted to try again with a different ID. 

### Code Snippet for Adding Branches
```java
System.out.println("Adding branches...");
System.out.print("Enter branch ID: ");
int newBranchId = scanner.nextInt();
scanner.nextLine();

// Check if the branch ID already exists
boolean branchExists = false;
for (Branch branch : branches) {
    if (branch.getBranchId() == newBranchId) {
        branchExists = true;
        break;
    }
}

if (branchExists) {
    System.out.println("Branch ID already exists. Please try again with a different ID.");
} else {
    System.out.print("Enter branch location: ");
    String newBranchLocation = scanner.nextLine();
    Branch newBranch = new Branch(newBranchId, newBranchLocation, new EmployeeCollection());
    addBranch(branches, newBranch);
    seeBranchDetails(branches);
}
```

## Dependencies
- Java 8 or higher.
