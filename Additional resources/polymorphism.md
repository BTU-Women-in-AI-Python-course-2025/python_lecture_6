# Polymorphism in Python

Polymorphism is one of the core concepts of Object-Oriented Programming (OOP). The word "polymorphism" comes from Greek, meaning "many forms." In programming, it refers to the ability of different objects to respond to the same method or function call in different ways. Polymorphism allows you to write flexible and reusable code.

---

## Why Use Polymorphism?

1. **Flexibility**: Write code that can work with objects of different classes as long as they implement the required methods.
2. **Code Reusability**: Use the same interface for different types of objects.
3. **Simplified Code**: Reduce the need for conditional logic by treating objects uniformly.

---

## Types of Polymorphism

Polymorphism in Python can be achieved in two main ways:
1. **Method Overriding**: Child classes provide their own implementation of a method defined in the parent class.
2. **Duck Typing**: Objects are used based on their behavior (methods and properties) rather than their type.

---

## Method Overriding (Runtime Polymorphism)

Method overriding occurs when a child class provides a specific implementation of a method that is already defined in its parent class. This allows the child class to customize or extend the behavior of the parent class.

### Example: Method Overriding

```python
class Animal:
    def speak(self):
        return "Animal makes a sound."

class Dog(Animal):
    def speak(self):  # Override the speak method
        return "Dog says woof!"

class Cat(Animal):
    def speak(self):  # Override the speak method
        return "Cat says meow!"
```

### Using Polymorphism with Method Overriding

```python
# Create objects of different classes
animals = [Animal(), Dog(), Cat()]

# Call the speak method on each object
for animal in animals:
    print(animal.speak())

# Output:
# Animal makes a sound.
# Dog says woof!
# Cat says meow!
```

In this example, the `speak` method behaves differently depending on the object's class, even though the method name is the same.

---

## Duck Typing (Compile-Time Polymorphism)

Duck typing is a concept where the type or class of an object is determined by its behavior (methods and properties) rather than its explicit type. The name comes from the phrase: "If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck."

### Example: Duck Typing

```python
class Duck:
    def quack(self):
        return "Duck says quack!"

class Person:
    def quack(self):
        return "Person imitates a duck quack!"

def make_it_quack(duck_like_object):
    print(duck_like_object.quack())
```

### Using Duck Typing

```python
# Create objects of different classes
duck = Duck()
person = Person()

# Pass objects to the function
make_it_quack(duck)    # Output: Duck says quack!
make_it_quack(person)  # Output: Person imitates a duck quack!
```

In this example, the `make_it_quack` function doesn't care about the type of the object passed to it. As long as the object has a `quack` method, it will work.

---

## Polymorphism with Built-in Functions

Python's built-in functions and operators also support polymorphism. For example, the `len()` function works with different types of objects like strings, lists, and dictionaries because they all implement the `__len__` method.

### Example: Polymorphism with `len()`

```python
# Using len() with different types
print(len("Hello"))        # Output: 5 (string)
print(len([1, 2, 3, 4]))   # Output: 4 (list)
print(len({"a": 1, "b": 2}))  # Output: 2 (dictionary)
```

---

## Polymorphism with Abstract Base Classes (ABCs)

Abstract Base Classes (ABCs) are used to define a common interface for a group of subclasses. They ensure that all subclasses implement specific methods, enabling polymorphism.

### Example: Using ABCs

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius ** 2

class Square(Shape):
    def __init__(self, side):
        self.side = side

    def area(self):
        return self.side ** 2
```

### Using Polymorphism with ABCs

```python
# Create objects of different subclasses
shapes = [Circle(5), Square(4)]

# Call the area method on each object
for shape in shapes:
    print(f"Area: {shape.area()}")

# Output:
# Area: 78.5
# Area: 16
```

In this example, the `Shape` class defines an abstract method `area`, and the subclasses (`Circle` and `Square`) provide their own implementations. This ensures that all shapes can be treated uniformly.

---

## Best Practices for Using Polymorphism

1. **Use Consistent Interfaces**: Ensure that objects used polymorphically implement the same methods or properties.
2. **Leverage Duck Typing**: Focus on behavior rather than explicit types when designing flexible code.
3. **Use ABCs for Complex Hierarchies**: Abstract Base Classes can help enforce consistent interfaces across multiple subclasses.
4. **Avoid Overcomplicating**: Use polymorphism only when it simplifies your code and improves readability.

---

## Real-World Example: Polymorphism in a Game

Imagine you're building a game with different types of characters, each with their own `attack` method. Polymorphism allows you to handle all characters uniformly.

```python
class Warrior:
    def attack(self):
        return "Warrior swings a sword!"

class Archer:
    def attack(self):
        return "Archer shoots an arrow!"

class Mage:
    def attack(self):
        return "Mage casts a fireball!"

# List of characters
characters = [Warrior(), Archer(), Mage()]

# Polymorphic behavior
for character in characters:
    print(character.attack())

# Output:
# Warrior swings a sword!
# Archer shoots an arrow!
# Mage casts a fireball!
```

---

## Conclusion

Polymorphism is a powerful concept in Python that allows you to write flexible, reusable, and maintainable code. By leveraging **method overriding**, **duck typing**, and **abstract base classes**, you can create programs that are both elegant and efficient. Practice using polymorphism in your projects to master this essential OOP concept!
