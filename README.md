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

### Ex.No:8(a)  Pointers with arithmetic operations

#### Aim 
- To write a C++ program for arithmetic operations using pointers.

#### Algorithm

1. Increment (++, +=): Move the pointer to the next element of the same data type.
2. Decrement (--, -=): Move the pointer to the previous element.
3. Addition (+): Calculate the address of an element a certain number of positions forward.
4. Subtraction (-): Calculate the address of an element a certain number of positions backward, or the number of elements between two pointers.
5. De-reference the pointer: Use the * operator to access the value at the memory address the
pointer currently holds.
6. Print results: Display the addresses and values to observe the effects of pointer arithmetic.

#### Program 
```C++
#include <iostream>
using namespace std;
int main() {
// 1. Declare and initialize an array
int arr[] = {10, 20, 30, 40, 50};
// Initialize a pointer to the first element
int* ptr = arr;
cout << "Original address (ptr): " << ptr << ", Value: " << *ptr << endl;
// Increment: move to the next element (increments by sizeof(int), usually 4 bytes)
ptr++;
cout << "After Increment (ptr++): " << ptr << ", Value: " << *ptr << endl;
// Addition: move 2 elements forward from the start of the array
int* new_ptr_add = arr + 2;
cout << "After Addition (arr + 2): " << new_ptr_add << ", Value: " << *new_ptr_add << endl;
// Decrement: move back one element
ptr--;
cout << "After Decrement (ptr--): " << ptr << ", Value: " << *ptr << endl;
// Subtraction: find the number of elements between two pointers
int* ptr2 = &arr[4]; // Point to the last element

ptrdiff_t diff = ptr2 - arr; // Calculate difference
cout << "Pointer Subtraction (ptr2 - arr): " << diff << " elements" << endl;
return 0;
}
```

#### Output
	Original address (ptr): 0x7ffee4b0a980, Value: 10
	After Increment (ptr++): 0x7ffee4b0a984, Value: 20
	After Addition (arr + 2): 0x7ffee4b0a988, Value: 30
	After Decrement (ptr--): 0x7ffee4b0a980, Value: 10
	Pointer Subtraction (ptr2 - arr): 4 elements


### Ex.No:8(b)  This Pointer

#### Aim 
- To write a C++ program using this pointer.

#### Algorithm

1. Define a class (e.g., Example) with a private integer data member (data).
2. Define a public member function (e.g., setValue) that takes an integer parameter with the same
name (data).
3. Inside the function, use this->data to refer to the class's data member and the plain data to refer
to the function parameter.
4. Define another member function (e.g., displayValue) to print the value of the data member.
5. In the main function, create an object of the class.
6. Call the setValue function to assign a value.
7. Call the displayValue function to show the result..

#### Program 
```C++
#include <iostream>
using namespace std;
class Example {
private:
int data; // Class data member
public:
// Member function with a parameter named 'data'

void setValue(int data) {
// 'this->data' refers to the class member
// 'data' (without this->) refers to the function parameter
this->data = data;
}
void displayValue() {
cout << "The value of the data member is: " << this->data << endl;
}
};
int main() {
Example obj;

// Create an object 'obj'

obj.setValue(42);

// Call setValue with the value 42

obj.displayValue(); // Display the stored value
return 0;
}
```

#### Output
	The value of the data member is: 42


### Ex.No:8(c)  Pointers to derived classes and base classes
#### Aim 
- To write a C++ program for accessing data from base classes using pointers.

#### Algorithm

1. Define a Base Class: Create a class (e.g., Animal) with a virtual function (e.g., speak()). The virtual keyword enables dynamic polymorphism.
2. Define a Derived Class: Create another class (e.g., Dog) that inherits from the base class and overrides the virtual function.
3. Create Objects: Instantiate objects of both the base and derived classes.
4. Declare a Pointer: Declare a pointer of the base class type.
5. Assign Pointers: Point the base class pointer to the address of the base class object, call the function, and then point the same pointer to the address of the derived class object and call the function again.
6. Observe Output: Notice how the appropriate function (base or derived) is called at runtime,

#### Program 
```C++
#include <iostream>
// Base Class
class Animal {
public:
// Virtual function enables runtime polymorphism
virtual void speak() {
std::cout << "Animal speaks a generic sound." << std::endl;
}
};
// Derived Class
class Dog : public Animal {
public:
// Overriding the base class function
void speak() {
std::cout << "Dog barks: Woof! Woof!" << std::endl;
}
};
int main() {
Animal genericAnimal;
Dog specificDog;
// Declare a pointer of the base class type
Animal* animalPtr;
// --- Point to Base Class Object --animalPtr = &genericAnimal;
std::cout << "Pointer points to Base Class object:" << std::endl;
animalPtr->speak(); // Calls Base Class speak()
std::cout << "\n----------------------------------\n" << std::endl;
// --- Point to Derived Class Object --// A pointer to a base class can point to a derived class object (upcasting)
animalPtr = &specificDog;
std::cout << "Pointer points to Derived Class object:" << std::endl;

animalPtr->speak(); // Calls Derived Class speak() because it's a virtual function
return 0;
}
```

#### Output
	Pointer points to Base Class object:
	Animal speaks a generic sound.
	---------------------------------Pointer points to Derived Class object:
	Dog barks: Woof! Woof!


### Ex.No:9(a)  Virtual base class
#### Aim 
- To write a C++ program for virtual base class.
#### Algorithm

1. Define the initial base class (e.g., A).
2. Define two intermediate derived classes (e.g., B and C), both of which inherit from the initial
base class virtually using the virtual keyword.
3. Define the final derived class (e.g., D) which inherits from both intermediate classes (B and C).
4. Instantiate an object of the final derived class (D). Due to virtual inheritance, only one shared
instance of the initial base class (A) is created.
5. Access members of the initial base class through the final derived class object without
ambiguity.

#### Program 
```C++
#include <iostream>
using namespace std;
// Step 1: Define the initial base class (A)
class A {
public:
int value;
A() {
value = 0;
}

};
// Step 2: Define intermediate class B, virtually inheriting from A
class B : virtual public A {
public:
B() {
// Constructor for B might set value, but the most derived class controls construction
}
};
// Step 2: Define intermediate class C, virtually inheriting from A
class C : virtual public A {
public:
C() {
// Constructor for C might set value, but the most derived class controls construction
}
};
// Step 3: Define final class D, inheriting from B and C
class D : public B, public C {
public:
// The most derived class (D) is responsible for constructing the virtual base class (A)
D() {
value = 42; // Accessing 'value' directly is unambiguous
}
};
int main() {
// Step 4: Create an object of the most derived class (D)
D obj;
// Step 5: Access the shared member 'value' from the single instance of A
cout << "Value stored in the shared base A instance: " << obj.value << endl;
return 0;
}
```

#### Output
	Value stored in the shared base A instance: 42

### Ex.No:9(b)  Virtual Destructors
#### Aim 
- To write a C++ program for virtual function using destructors.
#### Algorithm

1. Define the Base Class: Create a base class with a constructor, a member for dynamically
allocated memory (if needed to demonstrate the leak), and a virtual destructor.
2. Define the Derived Class: Create a derived class that inherits from the base class, has its own
dynamically allocated memory, constructor, and destructor. The derived destructor
automatically overrides the base's virtual destructor.
3. Use Polymorphism: In the main function, dynamically allocate an object of the derived class,
but store its address in a pointer to the base class.
4. Delete through Base Pointer: Use the delete operator on the base class pointer.
5. Verify Deletion: The virtual destructor mechanism ensures the derived class destructor is called
first, followed by the base class destructor, leading to proper cleanup.

#### Program 
```C++
#include <iostream>
#include <string>
using namespace std;
// Base class
class Base {
public:
Base() {
cout << "Base constructor called" << endl;
}
// Declare destructor as virtual
virtual ~Base() {
cout << "Base destructor called" << endl;
}
};

// Derived class
class Derived : public Base {
private:
int* data; // Dynamically allocated memory
public:
Derived() {
data = new int(100); // Allocate memory
cout << "Derived constructor called, allocated data" << endl;
}
~Derived() {
delete data; // Deallocate memory
cout << "Derived destructor called, freed data" << endl;
}
};
int main() {
cout << "Creating Derived object via Base pointer:" << endl;
Base* ptr = new Derived(); // Pointer to Base, pointing to Derived object
cout << "\nDeleting object via Base pointer:" << endl;
delete ptr; // Calls the virtual destructor, ensuring correct order
return 0;
}
```

#### Output
	Creating Derived object via Base pointer:
	Base constructor called
	Derived constructor called, allocated data
	Deleting object via Base pointer:
	Derived destructor called, freed data
	Base destructor called









### Ex.No:9(c)  Pure Virtual Functions
#### Aim 
- To write a C++ program for virtual functions.
#### Algorithm

1. Define an abstract base class Shape with a public pure virtual function draw() using the
syntax virtual void draw() = 0;. This makes Shape an abstract class, preventing direct
instantiation.
2. Define concrete derived classes Circle and Rectangle that inherit from Shape and provide their
specific implementations for the draw() function, using the override keyword for clarity.
3. In the main function, create instances of the derived classes (circleObj, rectObj).
4. Declare a pointer of the base class type (Shape* shape1). Abstract classes can have pointers and
references.
5. Assign the address of the Circle object to the base class pointer.
6. Call the draw() function through the base class pointer, which uses runtime polymorphism to
execute the derived class's version of the function.
7. Repeat for the Rectangle object, demonstrating dynamic binding.

#### Program 
```C++
#include <iostream>
using namespace std;
// Abstract base class
class Shape {
public:
// Pure virtual function declaration
virtual void draw() = 0;
};
// Derived class Circle
class Circle : public Shape {
public:
// Implementation of the pure virtual function
void draw() override {
cout << "Drawing a Circle" << endl;
}
};
// Derived class Rectangle
class Rectangle : public Shape {
public:

// Implementation of the pure virtual function
void draw() override {
cout << "Drawing a Rectangle" << endl;
}
};
int main() {
// Pointers of the abstract base class type are used for polymorphism
Shape* shape1;
Circle circleObj;
Rectangle rectObj;
// Point to a Circle object and call the draw function
shape1 = &circleObj;
shape1->draw(); // Calls Circle's draw()
// Point to a Rectangle object and call the draw function
shape1 = &rectObj;
shape1->draw(); // Calls Rectangle's draw()
return 0;
}
```

#### Output
	Drawing a Circle
	Drawing a Rectangle







