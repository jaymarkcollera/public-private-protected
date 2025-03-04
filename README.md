class BankAccount:
    def __init__(self, account_holder, balance, account_type):
        self.account_holder = account_holder  # Public Member
        self.__balance = balance  # Private Member
        self._account_type = account_type  # Protected Member

    def deposit(self, amount):
        """Public Method to deposit money."""
        if amount > 0:
            self.__balance += amount
            print(f"Deposited:  ₱{amount}")
        else:
            print("Invalid deposit amount!")

    def withdraw(self, amount):
        """Public Method to withdraw money."""
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            print(f"Withdrawn: ₱{amount}")
        else:
            print("Invalid withdrawal amount or insufficient funds!")

    def get_balance(self):
        """Public Method to check balance."""
        return self.__balance

# Subclass to demonstrate protected member access
class SavingsAccount(BankAccount):
    def account_details(self):
        print(f"Account Holder: {self.account_holder}")
        print(f"Account Type: {self._account_type}")  # Accessing protected member

# Execution
acc = BankAccount("Jay Mark", 1000, "Checking")
acc.deposit(500)
acc.withdraw(200)
print(f"Current Balance: ₱{acc.get_balance()}")

# Trying to access private member directly (will raise an error)
# print(acc.__balance)  # Uncommenting this will cause an AttributeError

# Accessing protected member from subclass
savings = SavingsAccount("charlotte & jay mark", 2000, "Savings")
savings.account_details()
