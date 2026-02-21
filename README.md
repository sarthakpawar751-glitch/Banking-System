# Banking-System
#include <iostream>
#include <vector>
using namespace std;

class Transaction {
public:
    string type;
    double amount;

    Transaction(string t, double a) {
        type = t;
        amount = a;
    }
};

class Account {
    double balance;
    vector<Transaction> history;

public:
    Account() {
        balance = 0;
    }

    void deposit(double amount) {
        balance += amount;
        history.push_back(Transaction("Deposit", amount));
        cout << "Amount Deposited Successfully!\n";
    }

    void withdraw(double amount) {
        if (amount > balance) {
            cout << "Insufficient Balance!\n";
        } else {
            balance -= amount;
            history.push_back(Transaction("Withdraw", amount));
            cout << "Withdrawal Successful!\n";
        }
    }

    void showBalance() {
        cout << "Current Balance: " << balance << endl;
    }

    void showTransactions() {
        cout << "\nTransaction History:\n";
        for (int i = 0; i < history.size(); i++) {
            cout << history[i].type << " - " << history[i].amount << endl;
        }
    }
};

class Customer {
public:
    string name;
    Account account;

    Customer(string n) {
        name = n;
    }
};

int main() {

    Customer c1("Sarthak");

    c1.account.deposit(5000);
    c1.account.withdraw(2000);
    c1.account.showBalance();
    c1.account.showTransactions();

    return 0;
}
