### EX.No:6(e)          Hierarchical Inheritance

#### Aim :

- To write a C++ program for hierarchical inheritance.
#### Algorithm :

1. Start the program and include necessary headers (iostream for input/output)
2. Define a base class (e.g., Animal) with common data members and member functions that all
derived classes will share.
3. Define multiple derived classes (e.g., Dog, Cat), each inheriting from the single base class
using the colon (:) syntax and a visibility mode (typically public).
4. Add unique data members and member functions specific to each derived class.
5. Create objects of the derived classes in the main function.
6. Call both the inherited (base class) and unique (derived class) member functions using the
derived class objects.
7. Print the results to demonstrate access to all members.
8. End the program

#### Program
```C++
#include <iostream>
using namespace std;
// Base class
class Animal {
  public:
    void eat() { cout << "This animal eats food." << endl; }
};
// Derived class 1
class Dog : public Animal {
  public:
    void bark() { cout << "The dog barks." << endl; }
};
// Derived class 2
class Cat : public Animal {

  public:
    void meow() { cout << "The cat meows." << endl; }
};
int main() {
    // Create an object of the Dog class
    Dog d;
    cout << "Dog Class:" << endl;
    d.eat();      // Accessing base class function
    d.bark();     // Accessing derived class function
    cout << endl; // Add a newline for readability
    // Create an object of the Cat class
    Cat c;
    cout << "Cat Class:" << endl;
    c.eat();  // Accessing base class function
    c.meow(); // Accessing derived class function
    return 0;
}
```

#### Output :
	Dog Class:
	This animal eats food.
	The dog barks.
	Cat Class:
	This animal eats food.
	The cat meows.

### Ex.No:7(a)    Operator Overloading

#### Aim:
- To write a C++ program for Operator Overloading.
#### Algorithm 

1. Define a class with the necessary data members (usually private) and member functions (public).
2. Declare a special operator function within the class (as a member function) or outside the class (as a global function, often a friend function if private member access is needed).
3. The function should use the syntax returnType operator symbol(arguments) (e.g., Complex operator+(const Complex& other)).
4. Implement the logic within the function to perform the desired operation on the user-defined types.
5. This typically involves creating a temporary object, performing the calculation on its members, and returning it.
6. In the main function, create objects of the class and use the overloaded operator in a natural syntax
(e.g., C3 = C1 + C2;). The compiler will internally translate this into a call to the operator function (e.g., C3 = C1.operator+(C2); or a global function call).

#### Program

``` C++
#include <iostream>
using namespace std;
class Complex {
  private:
    int real, imag;

  public:
    // Constructor
    Complex(int r = 0, int i = 0) : real(r), imag(i) {}
    // Overload the + operator
    Complex operator+(const Complex &other) {
        Complex temp; // Create a temporary object to store the result
        temp.real = real + other.real; // Add the real parts
        temp.imag = imag + other.imag; // Add the imaginary parts
        return temp;                   // Return the result object
    }
    // Function to display the complex number
    void display() { cout << real << " + i" << imag << endl; }
};
int main() {
    Complex c1(10, 5);
    Complex c2(2, 3);
    Complex c3;
    // Use the overloaded + operator
    c3 = c1 + c2;

    cout << "First complex number: ";
    c1.display();
    cout << "Second complex number: ";
    c2.display();
    cout << "Sum of complex numbers: ";
    c3.display();
    return 0;
}
```
#### Output 
	First complex number: 10 + i5
	Second complex number: 2 + i3
	Sum of complex numbers: 12 + i8

### Ex.No:7(b)  Operator overloading with Friend Functions

#### Aim
- To write a C++ program overloads the binary + operator for a Complex number class using a
function.

#### Algorithm
``` C++
#include <iostream>
using namespace std;
class Complex {
  private:
    float real, imag;

  public:
    // Constructors
    Complex() : real(0), imag(0) {}
    Complex(float r, float i) : real(r), imag(i) {}
    // Declare the addition operator as a friend function
    friend Complex operator+(Complex a, Complex b);
    // Display function
    void display() { cout << real << " + i" << imag << endl; }
};
// Define the friend function outside the class
Complex operator+(Complex a, Complex b) {
    Complex temp;
    temp.real = a.real + b.real; // Direct access to private members
    temp.imag = a.imag + b.imag; // Direct access to private members
    return temp;
}
int main() {
    Complex c1(2.5, 3.5);
    Complex c2(1.6, 2.7);
    Complex c3;
    // Use the overloaded + operator

    c3 = c1 + c2; // Equivalent to c3 = operator+(c1, c2);
    cout << "Complex Number 1: ";
    c1.display();
    cout << "Complex Number 2: ";
    c2.display();
    cout << "Sum (CN1 + CN2): ";
    c3.display();
    return 0;
}

```
#### Output:

	Complex Number 1: 2.5 + i3.5
	Complex Number 2: 1.6 + i2.7
	Sum (CN1 + CN2): 4.1 + i6.2
### Ex.No:7(c)  Overloading Unary Operators

#### Aim 

#### Algorithm

1. Start the program.
2. Define a class (e.g., Number) with private data members.
3. Declare the overloaded operator function as a public member function within the class. This function
should use the operator keyword followed by the operator symbol (e.g., operator-()) and take no
arguments for member functions.
4. Implement the operator function to perform the desired operation on the object's data members (e.g.,
negate a value, increment a counter).
5. Create an object of the class in the main function.
6. Call the overloaded operator function using the operator symbol with the object (e.g., -n1).
7. Display the results to verify the output.
8. Stop the program.

#### Program 
```C++
#include <iostream>
using namespace std;
class Number {
private:
int x;
public:
// Constructor to initialize the value
Number(int p) {
x = p;
}
// Overload the unary - operator
void operator -() {
x = -x; // Negates the value of the data member
}
// Function to display the value
void display() {
cout << "x = " << x << endl;

}
};
int main() {
Number n(10); // Create an object 'n' with initial value 10
cout << "Initial value: ";
n.display();
-n; // Calls the overloaded operator-() function
cout << "Value after overloading unary - operator: ";
n.display();
return 0;
}
```

#### Output
	Initial value: x = 10
	Value after overloading unary - operator: x = -10
