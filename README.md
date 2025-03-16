# Python Introduction

- **Inheritance and Polymorphism**: 
  - Learn about how inheritance allows classes to derive from other classes and how polymorphism enables objects to be treated as instances of their parent class.
  - Inheritance - https://www.w3schools.com/python/python_inheritance.asp
  - Polymorphism - https://www.w3schools.com/python/python_polymorphism.asp

- **Encapsulation and Abstraction**: 
  - Understand how encapsulation restricts direct access to some of an object's components and how abstraction allows focusing on essential qualities rather than specific characteristics.
  - Encapsulation - https://www.geeksforgeeks.org/encapsulation-in-python/
  - Abstraction - https://www.geeksforgeeks.org/data-abstraction-in-python/
    
# 📚 Create a Basic Shape Hierarchy

## Task: Create a Basic Shape Hierarchy

**Objective:** Implement a basic inheritance structure with polymorphism in Python.

1. **Create a Base Class:**
   - Define a class `Shape` with an initializer to set a `name` attribute.
   - Add a method `area()` that returns `None` (this will be overridden in subclasses).

2. **Create Subclasses:**
   - Define a subclass `Rectangle` that inherits from `Shape`.
     - Add attributes `width` and `height` in the initializer.
     - Override the `area()` method to return the area of the rectangle.
   - Define a subclass `Circle` that inherits from `Shape`.
     - Add an attribute `radius` in the initializer.
     - Override the `area()` method to return the area of the circle (use `math.pi` for the value of π).

3. **Demonstrate Polymorphism:**
   - Create a function `print_area(shape)` that takes a `Shape` object and prints its name and area.
   - Instantiate a `Rectangle` and a `Circle` and call `print_area()` for each.
