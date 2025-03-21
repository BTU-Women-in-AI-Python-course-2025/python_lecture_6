# Encapsulation in Python

Encapsulation is one of the fundamental concepts of Object-Oriented Programming (OOP). It refers to the bundling of data (attributes) and methods (functions) that operate on the data into a single unit, called a **class**. Encapsulation also involves restricting direct access to some of an object's components, which is achieved using access modifiers like **private** and **protected** members.

---

## Why Use Encapsulation?

1. **Data Protection**: Prevent unauthorized access or modification of data.
2. **Controlled Access**: Provide controlled access to data through methods (getters and setters).
3. **Code Maintainability**: Encapsulate implementation details, making the code easier to maintain and modify.
4. **Modularity**: Group related data and behavior into a single unit, improving code organization.

---

## Access Modifiers in Python

Python uses naming conventions to indicate the access level of attributes and methods:
1. **Public**: No restrictions. Attributes and methods are accessible from anywhere.
   - Example: `name`
2. **Protected**: Intended for use within the class and its subclasses. Marked with a single underscore (`_`).
   - Example: `_age`
3. **Private**: Restricted to the class itself. Marked with a double underscore (`__`).
   - Example: `__salary`

---

## Example of Encapsulation

Let’s create a `BankAccount` class to demonstrate encapsulation.

```python
class BankAccount:
    def __init__(self, owner, balance):
        self.owner = owner  # Public attribute
        self._balance = balance  # Protected attribute
        self.__pin = "1234"  # Private attribute

    # Public method to deposit money
    def deposit(self, amount):
        if amount > 0:
            self._balance += amount
            return f"Deposited ${amount}. New balance: ${self._balance}"
        return "Invalid deposit amount."

    # Public method to withdraw money
    def withdraw(self, amount, pin):
        if pin == self.__pin:  # Access private attribute
            if 0 < amount <= self._balance:
                self._balance -= amount
                return f"Withdrew ${amount}. New balance: ${self._balance}"
            return "Insufficient funds or invalid amount."
        return "Incorrect PIN."

    # Public method to check balance
    def get_balance(self):
        return f"Current balance: ${self._balance}"
```

---

### Using the `BankAccount` Class

```python
# Create a BankAccount object
account = BankAccount("John Doe", 1000)

# Access public attribute
print(account.owner)  # Output: John Doe

# Access protected attribute (not recommended)
print(account._balance)  # Output: 1000

# Access private attribute (will raise an error)
# print(account.__pin)  # AttributeError: 'BankAccount' object has no attribute '__pin'

# Use public methods to interact with the object
print(account.deposit(500))  # Output: Deposited $500. New balance: $1500
print(account.withdraw(200, "1234"))  # Output: Withdrew $200. New balance: $1300
print(account.get_balance())  # Output: Current balance: $1300
```

---

## Getters and Setters

Getters and setters are methods used to access and modify private or protected attributes. They provide controlled access to the data.

### Example: Getters and Setters

```python
class Person:
    def __init__(self, name, age):
        self.__name = name  # Private attribute
        self.__age = age    # Private attribute

    # Getter for name
    def get_name(self):
        return self.__name

    # Setter for name
    def set_name(self, name):
        if isinstance(name, str):
            self.__name = name
        else:
            print("Name must be a string.")

    # Getter for age
    def get_age(self):
        return self.__age

    # Setter for age
    def set_age(self, age):
        if isinstance(age, int) and age > 0:
            self.__age = age
        else:
            print("Age must be a positive integer.")
```

### Using Getters and Setters

```python
# Create a Person object
person = Person("Alice", 25)

# Use getters to access private attributes
print(person.get_name())  # Output: Alice
print(person.get_age())   # Output: 25

# Use setters to modify private attributes
person.set_name("Bob")
person.set_age(30)

print(person.get_name())  # Output: Bob
print(person.get_age())   # Output: 30

# Invalid updates
person.set_name(123)      # Output: Name must be a string.
person.set_age(-5)        # Output: Age must be a positive integer.
```

---

## Name Mangling for Private Attributes

Python uses **name mangling** to make private attributes harder to access directly. When you define a private attribute with a double underscore (`__`), Python internally changes its name to `_ClassName__attribute`.

### Example: Name Mangling

```python
class Employee:
    def __init__(self, name, salary):
        self.__name = name
        self.__salary = salary

# Create an Employee object
emp = Employee("John", 50000)

# Access private attribute using name mangling
print(emp._Employee__name)    # Output: John
print(emp._Employee__salary)  # Output: 50000
```

---

## Best Practices for Encapsulation

1. **Use Private Attributes**: Mark attributes as private (`__`) if they should not be accessed or modified directly.
2. **Provide Getters and Setters**: Use getters and setters to control access to private or protected attributes.
3. **Avoid Direct Access**: Discourage direct access to protected attributes (single underscore) outside the class or its subclasses.
4. **Document Your Code**: Clearly document the purpose of attributes and methods to guide users of your class.

---

## Real-World Example: Encapsulation in a `Car` Class

Let’s create a `Car` class that encapsulates its attributes and provides controlled access.

```python
class Car:
    def __init__(self, make, model, year):
        self.__make = make
        self.__model = model
        self.__year = year
        self.__mileage = 0

    # Getter for make
    def get_make(self):
        return self.__make

    # Getter for model
    def get_model(self):
        return self.__model

    # Getter for year
    def get_year(self):
        return self.__year

    # Getter for mileage
    def get_mileage(self):
        return self.__mileage

    # Method to update mileage
    def drive(self, miles):
        if miles > 0:
            self.__mileage += miles
            return f"Driven {miles} miles. Total mileage: {self.__mileage}"
        return "Invalid mileage."
```

### Using the `Car` Class

```python
# Create a Car object
my_car = Car("Toyota", "Corolla", 2022)

# Access attributes using getters
print(my_car.get_make())    # Output: Toyota
print(my_car.get_model())   # Output: Corolla
print(my_car.get_year())    # Output: 2022
print(my_car.get_mileage()) # Output: 0

# Update mileage
print(my_car.drive(100))    # Output: Driven 100 miles. Total mileage: 100
print(my_car.drive(50))     # Output: Driven 50 miles. Total mileage: 150
```

---

## Conclusion

Encapsulation is a key principle of OOP that helps you protect and control access to data within your classes. By using **private attributes**, **getters**, **setters**, and **name mangling**, you can create robust and maintainable code. Practice encapsulation in your projects to build secure and well-organized applications!
