# COP2334-1-Module-5-Programming-Group-Assignment
This is a separate repository link of the COP2334-1 Module 5 Group Programming Assignment on behalf of Marcello Gonzalez

#include <iostream>
#include <iomanip>
using namespace std;

// Function header files
int main() {
    // Declare variables
    int monthsPassed;
    double annualInterestRate, startingBalance, totalDeposits = 0, totalWithdrawals = 0;

    // Prompt user for input
    cout << "Enter the annual interest rate: ";
    cin >> annualInterestRate;
    cout << "Enter your starting balance: ";
    cin >> startingBalance;
    cout << "Enter the number of months passed: ";
    cin >> monthsPassed;

    // Create array to store deposits and withdrawals
    double monthlyInterestRate = (annualInterestRate / 100) / 12;
    double balance = startingBalance;
    double totalInterestEarned = 0;

    // Loop to get deposits and withdrawals for each month
    for (int i = 1; i <= monthsPassed; i++) {
        double deposit, withdrawal;

        // Print month number
        cout << "Month " << i << ":" << endl;

        // Deposit
        do {
            cout << "Enter the amount deposited during month " << i << ": ";
            cin >> deposit;
            if (deposit < 0) {
                cout << "Invalid input. Enter a positive number: ";
            }
        } while (deposit < 0);
        balance += deposit;
        totalDeposits += deposit;

        // Withdrawal
        do {
            cout << "Enter the amount withdrawn during month " << i << ": ";
            cin >> withdrawal;
            if (withdrawal < 0) {
                cout << "Invalid input. Enter a positive number: ";
            }
        } while (withdrawal < 0);
        balance -= withdrawal;
        totalWithdrawals += withdrawal;

        // Monthly interest
        double monthlyInterest = balance * monthlyInterestRate;
        balance += monthlyInterest;
        totalInterestEarned += monthlyInterest;
    }

    // Print results
    cout << "Summary of account activity:" << endl;
    cout << "Ending balance: $" << fixed << setprecision(2) << balance << endl;
    cout << "Total deposits: $" << fixed << setprecision(2) << totalDeposits << endl;
    cout << "Total withdrawals: $" << fixed << setprecision(2) << totalWithdrawals << endl;
    cout << "Total interest earned: $" << fixed << setprecision(2) << totalInterestEarned << endl;

    return 0;
}

