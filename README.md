# Bank Account Management System

A console-based banking application in Java that demonstrates Object-Oriented
Programming and basic Data Structures & Algorithms.

**Author:** Annick Ujeneza

## Features
- Create savings and checking accounts for regular and premium customers
- View all accounts with balances and totals
- Deposit and withdraw money, with a confirmation step
- View transaction history per account (newest first) with summary totals
- Simple menu with input validation

## Account and customer rules
| Type | Rules |
|---|---|
| Savings | 3.5% annual interest, \$500 minimum balance |
| Checking | \$1,000 overdraft limit, \$10 monthly fee |
| Regular customer | Standard services |
| Premium customer | Monthly fees waived, \$10,000 minimum deposit |

## Project structure
```
src/
├── model/     Customer, RegularCustomer, PremiumCustomer, Account,
│              SavingsAccount, CheckingAccount, Transactable, Transaction
├── service/   AccountManager, TransactionManager
└── app/       Main
```

## OOP concepts used
- **Encapsulation:** private fields with public getters/setters
- **Inheritance:** `Account` -> Savings/Checking; `Customer` -> Regular/Premium
- **Abstraction:** abstract classes `Account` and `Customer`, interface `Transactable`
- **Polymorphism:** overridden `withdraw`, `canWithdraw`, `displayAccountDetails`, `getAccountType`
- **Composition:** `Account` has a `Customer`; managers hold arrays of accounts/transactions
- **Static members:** counters generating ACC001, CUS001 and TXN001 style IDs

## Data structures and algorithms
- Accounts and transactions are stored in fixed-size arrays (50 and 200) with a counter
- Accounts are found by **linear search**, O(n)
- Transaction history is shown newest first by looping backwards through the array,
  so no extra sorting is needed

## How to run

**Requirements:** JDK 17 or newer.

**In IntelliJ IDEA:** open the project, open `src/app/Main.java`, and click Run.

**From the terminal** (in the project folder):
```
# Windows PowerShell
mkdir out -Force
javac -d out (Get-ChildItem -Recurse src -Filter *.java).FullName
java -cp out app.Main

# Mac / Linux / Git Bash
mkdir -p out
javac -d out $(find src -name "*.java")
java -cp out app.Main
```

## Testing notes
- By default the app loads 5 sample accounts (3 Savings, 2 Checking), so new
  accounts start at ACC006 / CUS006, matching the lab's example screenshots.
- To test ID auto-generation from a clean start (Test Scenario 9), run with
  `--empty`, for example `java -cp out app.Main --empty`. New IDs then start at
  ACC001, CUS001 and TXN001.