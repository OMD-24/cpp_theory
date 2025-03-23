# cpp_theory
Create a Class
To create a class, use the class keyword:

Example
Create a class called "MyClass":

class MyClass {       // The class
  public:             // Access specifier
    int myNum;        // Attribute (int variable)
    string myString;  // Attribute (string variable)
};




Create an Object
In C++, an object is created from a class. We have already created the class named MyClass, so now we can use this to create objects.

To create an object of MyClass, specify the class name, followed by the object name.

To access the class attributes (myNum and myString), use the dot syntax (.) on the object:

Example
Create an object called "myObj" and access the attributes:

class MyClass {       // The class
  public:             // Access specifier
    int myNum;        // Attribute (int variable)
    string myString;  // Attribute (string variable)
};

int main() {
  MyClass myObj;  // Create an object of MyClass

  // Access attributes and set values
  myObj.myNum = 15; 
  myObj.myString = "Some text";

  // Print attribute values
  cout << myObj.myNum << "\n";
  cout << myObj.myString;
  return 0;
}




Multiple Objects
You can create multiple objects of one class:

Example
// Create a Car class with some attributes
class Car {
  public:
    string brand;   
    string model;
    int year;
};

int main() {
  // Create an object of Car
  Car carObj1;
  carObj1.brand = "BMW";
  carObj1.model = "X5";
  carObj1.year = 1999;

  // Create another object of Car
  Car carObj2;
  carObj2.brand = "Ford";
  carObj2.model = "Mustang";
  carObj2.year = 1969;

  // Print attribute values
  cout << carObj1.brand << " " << carObj1.model << " " << carObj1.year << "\n";
  cout << carObj2.brand << " " << carObj2.model << " " << carObj2.year << "\n";
  return 0;
}



Class Methods
Methods are functions that belongs to the class.

There are two ways to define functions that belongs to a class:

Inside class definition
Outside class definition
In the following example, we define a function inside the class, and we name it "myMethod".

Note: You access methods just like you access attributes; by creating an object of the class and using the dot syntax (.):

Inside Example
class MyClass {        // The class
  public:              // Access specifier
    void myMethod() {  // Method/function defined inside the class
      cout << "Hello World!";
    }
};

int main() {
  MyClass myObj;     // Create an object of MyClass
  myObj.myMethod();  // Call the method
  return 0;
}


To define a function outside the class definition, you have to declare it inside the class and then define it outside of the class. This is done by specifiying the name of the class, followed the scope resolution :: operator, followed by the name of the function:

Outside Example
class MyClass {        // The class
  public:              // Access specifier
    void myMethod();   // Method/function declaration
};

// Method/function definition outside the class
void MyClass::myMethod() {
  cout << "Hello World!";
}

int main() {
  MyClass myObj;     // Create an object of MyClass
  myObj.myMethod();  // Call the method
  return 0;
}





Parameters
You can also add parameters:

 Example
#include <iostream>
using namespace std;

class Car {
  public:
    int speed(int maxSpeed);
};

int Car::speed(int maxSpeed) {
  return maxSpeed;
}

int main() {
  Car myObj; // Create an object of Car
  cout << myObj.speed(200); // Call the method with an argument
  return 0;
}



Constructors
A constructor in C++ is a special method that is automatically called when an object of a class is created.

To create a constructor, use the same name as the class, followed by parentheses ():

Example
class MyClass {     // The class
  public:           // Access specifier
    MyClass() {     // Constructor
      cout << "Hello World!";
    }
};

int main() {
  MyClass myObj;    // Create an object of MyClass (this will call the constructor)
  return 0;
}




Constructor Parameters
Constructors can also take parameters (just like regular functions), which can be useful for setting initial values for attributes.

The following class have brand, model and year attributes, and a constructor with different parameters. Inside the constructor we set the attributes equal to the constructor parameters (brand=x, etc). When we call the constructor (by creating an object of the class), we pass parameters to the constructor, which will set the value of the corresponding attributes to the same:

Example
class Car {        // The class
  public:          // Access specifier
    string brand;  // Attribute
    string model;  // Attribute
    int year;      // Attribute
    Car(string x, string y, int z) { // Constructor with parameters
      brand = x;
      model = y;
      year = z;
    }
};

int main() {
  // Create Car objects and call the constructor with different values
  Car carObj1("BMW", "X5", 1999);
  Car carObj2("Ford", "Mustang", 1969);

  // Print values
  cout << carObj1.brand << " " << carObj1.model << " " << carObj1.year << "\n";
  cout << carObj2.brand << " " << carObj2.model << " " << carObj2.year << "\n";
  return 0;
}





Just like functions, constructors can also be defined outside the class. First, declare the constructor inside the class, and then define it outside of the class by specifying the name of the class, followed by the scope resolution :: operator, followed by the name of the constructor (which is the same as the class):

Example
class Car {        // The class
  public:          // Access specifier
    string brand;  // Attribute
    string model;  // Attribute
    int year;      // Attribute
    Car(string x, string y, int z); // Constructor declaration
};

// Constructor definition outside the class
Car::Car(string x, string y, int z) {
  brand = x;
  model = y;
  year = z;
}

int main() {
  // Create Car objects and call the constructor with different values
  Car carObj1("BMW", "X5", 1999);
  Car carObj2("Ford", "Mustang", 1969);

  // Print values
  cout << carObj1.brand << " " << carObj1.model << " " << carObj1.year << "\n";
  cout << carObj2.brand << " " << carObj2.model << " " << carObj2.year << "\n";
  return 0;
}




Access Specifiers
By now, you are quite familiar with the public keyword that appears in all of our class examples:

Example
class MyClass {  // The class
  public:        // Access specifier
    // class members goes here
};




The public keyword is an access specifier. Access specifiers define how the members (attributes and methods) of a class can be accessed. In the example above, the members are public - which means that they can be accessed and modified from outside the code.

However, what if we want members to be private and hidden from the outside world?

In C++, there are three access specifiers:

public - members are accessible from outside the class
private - members cannot be accessed (or viewed) from outside the class
protected - members cannot be accessed from outside the class, however, they can be accessed in inherited classes. You will learn more about Inheritance later.
In the following example, we demonstrate the differences between public and private members:

Example
class MyClass {
  public:    // Public access specifier
    int x;   // Public attribute
  private:   // Private access specifier
    int y;   // Private attribute
};

int main() {
  MyClass myObj;
  myObj.x = 25;  // Allowed (public)
  myObj.y = 50;  // Not allowed (private)
  return 0;
}
If you try to access a private member, an error occurs:

error: y is private



Note: It is possible to access private members of a class using a public method inside the same class. See the next chapter (Encapsulation) on how to do this.

Tip: It is considered good practice to declare your class attributes as private (as often as you can). This will reduce the possibility of yourself (or others) to mess up the code. This is also the main ingredient of the Encapsulation concept, which you will learn more about in the next chapter.


Note: By default, all members of a class are private if you don't specify an access specifier:



class MyClass {
  int x;   // Private attribute
  int y;   // Private attribute
};



Encapsulation
The meaning of Encapsulation, is to make sure that "sensitive" data is hidden from users. To achieve this, you must declare class variables/attributes as private (cannot be accessed from outside the class). If you want others to read or modify the value of a private member, you can provide public get and set methods.

Access Private Members
To access a private attribute, use public "get" and "set" methods:

Example
#include <iostream>
using namespace std;

class Employee {
  private:
    // Private attribute
    int salary;

  public:
    // Setter
    void setSalary(int s) {
      salary = s;
    }
    // Getter
    int getSalary() {
      return salary;
    }
};

int main() {
  Employee myObj;
  myObj.setSalary(50000);
  cout << myObj.getSalary();
  return 0;
}




Example explained
The salary attribute is private, which have restricted access.

The public setSalary() method takes a parameter (s) and assigns it to the salary attribute (salary = s).

The public getSalary() method returns the value of the private salary attribute.

Inside main(), we create an object of the Employee class. Now we can use the setSalary() method to set the value of the private attribute to 50000. Then we call the getSalary() method on the object to return the value.

Why Encapsulation?
It is considered good practice to declare your class attributes as private (as often as you can). Encapsulation ensures better control of your data, because you (or others) can change one part of the code without affecting other parts
Increased security of data



Inheritance
In C++, it is possible to inherit attributes and methods from one class to another. We group the "inheritance concept" into two categories:

derived class (child) - the class that inherits from another class
base class (parent) - the class being inherited from
To inherit from a class, use the : symbol.

In the example below, the Car class (child) inherits the attributes and methods from the Vehicle class (parent):

Example
// Base class
class Vehicle {
  public:
    string brand = "Ford";
    void honk() {
      cout << "Tuut, tuut! \n" ;
    }
};

// Derived class
class Car: public Vehicle {
  public:
    string model = "Mustang";
};

int main() {
  Car myCar;
  myCar.honk();
  cout << myCar.brand + " " + myCar.model;
  return 0;
}


Why And When To Use "Inheritance"?
- It is useful for code reusability: reuse attributes and methods of an existing class when you create a new class.




Multilevel Inheritance
A class can also be derived from one class, which is already derived from another class.

In the following example, MyGrandChild is derived from class MyChild (which is derived from MyClass).

Example
// Base class (parent)
class MyClass {
  public:
    void myFunction() {
      cout << "Some content in parent class." ;
    }
};

// Derived class (child)
class MyChild: public MyClass {
};

// Derived class (grandchild)
class MyGrandChild: public MyChild {
};

int main() {
  MyGrandChild myObj;
  myObj.myFunction();
  return 0;
}


Multiple Inheritance
A class can also be derived from more than one base class, using a comma-separated list:

Example
// Base class
class MyClass {
  public:
    void myFunction() {
      cout << "Some content in parent class." ;
    }
};

// Another base class
class MyOtherClass {
  public:
    void myOtherFunction() {
      cout << "Some content in another class." ;
    }
};

// Derived class
class MyChildClass: public MyClass, public MyOtherClass {
};

int main() {
  MyChildClass myObj;
  myObj.myFunction();
  myObj.myOtherFunction();
  return 0;
}

Access Specifiers
You learned from the Access Specifiers chapter that there are three specifiers available in C++. Until now, we have only used public (members of a class are accessible from outside the class) and private (members can only be accessed within the class). The third specifier, protected, is similar to private, but it can also be accessed in the inherited class:

Example
// Base class
class Employee {
  protected: // Protected access specifier
    int salary;
};

// Derived class
class Programmer: public Employee {
  public:
    int bonus;
    void setSalary(int s) {
      salary = s;
    }
    int getSalary() {
      return salary;
    }
};

int main() {
  Programmer myObj;
  myObj.setSalary(50000);
  myObj.bonus = 15000;
  cout << "Salary: " << myObj.getSalary() << "\n";
  cout << "Bonus: " << myObj.bonus << "\n";
  return 0;
}



Polymorphism
Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance.

Like we specified in the previous chapter; Inheritance lets us inherit attributes and methods from another class. Polymorphism uses those methods to perform different tasks. This allows us to perform a single action in different ways.

For example, think of a base class called Animal that has a method called animalSound(). Derived classes of Animals could be Pigs, Cats, Dogs, Birds - And they also have their own implementation of an animal sound (the pig oinks, and the cat meows, etc.):

Example
// Base class
class Animal {
  public:
    void animalSound() {
      cout << "The animal makes a sound \n";
    }
};

// Derived class
class Pig : public Animal {
  public:
    void animalSound() {
      cout << "The pig says: wee wee \n";
    }
};

// Derived class
class Dog : public Animal {
  public:
    void animalSound() {
      cout << "The dog says: bow wow \n";
    }
};
Remember from the Inheritance chapter that we use the : symbol to inherit from a class.

Now we can create Pig and Dog objects and override the animalSound() method:

Example
// Base class
class Animal {
  public:
    void animalSound() {
      cout << "The animal makes a sound \n";
    }
};

// Derived class
class Pig : public Animal {
  public:
    void animalSound() {
      cout << "The pig says: wee wee \n";
    }
};

// Derived class
class Dog : public Animal {
  public:
    void animalSound() {
      cout << "The dog says: bow wow \n";
    }
};

int main() {
  Animal myAnimal;
  Pig myPig;
  Dog myDog;

  myAnimal.animalSound();
  myPig.animalSound();
  myDog.animalSound();
  return 0;
}


Why And When To Use "Inheritance" and "Polymorphism"?
- It is useful for code reusability: reuse attributes and methods of an existing class when you create a new class.





C++ Files
C++ Files
The fstream library allows us to work with files.

To use the fstream library, include both the standard <iostream> AND the <fstream> header file:

Example
#include <iostream>
#include <fstream>
There are three classes included in the fstream library, which are used to create, write or read files:

Class	Description
ofstream	Creates and writes to files
ifstream	Reads from files
fstream	A combination of ofstream and ifstream: creates, reads, and writes to files
Create and Write To a File
To create a file, use either the ofstream or fstream class, and specify the name of the file.

To write to the file, use the insertion operator (<<).

Example
#include <iostream>
#include <fstream>
using namespace std;

int main() {
  // Create and open a text file
  ofstream MyFile("filename.txt");

  // Write to the file
  MyFile << "Files can be tricky, but it is fun enough!";

  // Close the file
  MyFile.close();
}
Why do we close the file?
It is considered good practice, and it can clean up unnecessary memory space.

Read a File
To read from a file, use either the ifstream or fstream class, and the name of the file.

Note that we also use a while loop together with the getline() function (which belongs to the ifstream class) to read the file line by line, and to print the content of the file:

Example
// Create a text string, which is used to output the text file
string myText;

// Read from the text file
ifstream MyReadFile("filename.txt");

// Use a while loop together with the getline() function to read the file line by line
while (getline (MyReadFile, myText)) {
  // Output the text from the file
  cout << myText;
}

// Close the file
MyReadFile.close();



C++ Exceptions
When executing C++ code, different errors can occur: coding errors made by the programmer, errors due to wrong input, or other unforeseeable things.

When an error occurs, C++ will normally stop and generate an error message. The technical term for this is: C++ will throw an exception (throw an error).

C++ try and catch
Exception handling in C++ consist of three keywords: try, throw and catch:

The try statement allows you to define a block of code to be tested for errors while it is being executed.

The throw keyword throws an exception when a problem is detected, which lets us create a custom error.

The catch statement allows you to define a block of code to be executed, if an error occurs in the try block.

The try and catch keywords come in pairs:

Example
try {
  // Block of code to try
  throw exception; // Throw an exception when a problem arise
}
catch () {
  // Block of code to handle errors
}
Consider the following example:

Example
try {
  int age = 15;
  if (age >= 18) {
    cout << "Access granted - you are old enough.";
  } else {
    throw (age);
  }
}
catch (int myNum) {
  cout << "Access denied - You must be at least 18 years old.\n";
  cout << "Age is: " << myNum;
}
Example explained
We use the try block to test some code: If the age variable is less than 18, we will throw an exception, and handle it in our catch block.

In the catch block, we catch the error and do something about it. The catch statement takes a parameter: in our example we use an int variable (myNum) (because we are throwing an exception of int type in the try block (age)), to output the value of age.

If no error occurs (e.g. if age is 20 instead of 15, meaning it will be be greater than 18), the catch block is skipped:

Example
int age = 20;
You can also use the throw keyword to output a reference number, like a custom error number/code for organizing purposes (505 in our example):

Example
try {
  int age = 15;
  if (age >= 18) {
    cout << "Access granted - you are old enough.";
  } else {
    throw 505;
  }
}
catch (int myNum) {
  cout << "Access denied - You must be at least 18 years old.\n";
  cout << "Error number: " << myNum;
}
Handle Any Type of Exceptions (...)
If you do not know the throw type used in the try block, you can use the "three dots" syntax (...) inside the catch block, which will handle any type of exception:

Example
try {
  int age = 15;
  if (age >= 18) {
    cout << "Access granted - you are old enough.";
  } else {
    throw 505;
  }
}
catch (...) {
  cout << "Access denied - You must be at least 18 years old.\n";
}



Date and Time
The <ctime> library allows us to work with dates and times.

To use it, you must import the <ctime> header file:

Example
#include <ctime> // Import the ctime library
Display Current Date and Time
The <ctime> library has a variety of functions to measure dates and times.

The time() function gives us a timestamp representing the current date and time. We can use the ctime() function to show the date and time that a timestamp represents:

Example
Display the current date:

// Get the timestamp for the current date and time
time_t timestamp;
time(&timestamp);

// Display the date and time represented by the timestamp
cout << ctime(&timestamp);
Two ways to use the time() function
The time() function writes a timestamp to the memory location given by the parameter, but it also returns the timestamp's value.

An alternative way to use the time() function is to pass in a NULL pointer and use the return value instead.

time_t timestamp = time(NULL);
Data Types
There are two different data types used to store the date and time: time_t for timestamps and struct tm for datetime structures.

Timestamps represent a moment in time as a single number, which makes it easier for the computer to do calculations.

Datetime structures are structures that represent different components of the date and time as members. This makes it easier for us to specify dates. Datetime structures have the following members:

tm_sec - The seconds within a minute
tm_min - The minutes within an hour
tm_hour - The hour within a day (from 0 to 23)
tm_mday - The day of the month
tm_mon - The month (from 0 to 11 starting with January)
tm_year - The number of years since 1900
tm_wday - The weekday (from 0 to 6 starting with Sunday)
tm_yday - The day of the year (from 0 to 365 with 0 being January 1)
tm_isdst - Positive when daylight saving time is in effect, zero when not in effect and negative when unknown
Always keep in mind the way that date components are represented:

Hours are represented in 24-hour format. 11pm would be represented as 23.
The months go from 0 to 11. For example, December would be represented as 11 rather than 12.
Years are represented relative to the year 1900. The year 2024 would be represented as 124 because 124 years have passed since 1900.
Creating Timestamps
The time() function can only create a timestamp for the current date, but we can create a timestamp for any date by using the mktime() function.

The mktime() function converts a datetime structure into a timestamp.

Example
Create a timestamp using the mktime() function:

struct tm datetime;
time_t timestamp;

datetime.tm_year = 2023 - 1900; // Number of years since 1900
datetime.tm_mon = 12 - 1; // Number of months since January
datetime.tm_mday = 17;
datetime.tm_hour = 12;
datetime.tm_min = 30;
datetime.tm_sec = 1;
// Daylight Savings must be specified
// -1 uses the computer's timezone setting
datetime.tm_isdst = -1;

timestamp = mktime(&datetime);

cout << ctime(&timestamp);
Note: The mktime() function needs these members to have a value: tm_year, tm_mon, tm_mday, tm_hour, tm_min, tm_sec and tm_isdst.

Creating Datetime Structures
The mktime() function also fills in the tm_wday and tm_yday members of the datetime structure with the correct values, which completes the structure and gives a valid datetime. It can be used, for example, to find the weekday of a given date:

Example
Find the weekday of a specified date:

// Create the datetime structure and use mktime to fill in the missing members
struct tm datetime;
datetime.tm_year = 2023 - 1900; // Number of years since 1900
datetime.tm_mon = 12 - 1; // Number of months since January
datetime.tm_mday = 17;
datetime.tm_hour = 0; datetime.tm_min = 0; datetime.tm_sec = 0;
datetime.tm_isdst = -1;
mktime(&datetime);

string weekdays[] = {"Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"};

cout << "The date is on a " << weekdays[datetime.tm_wday];
The localtime() and gmtime() functions can convert timestamps into datetime structures.

The localtime() function returns a pointer to a structure representing the time in the computer's time zone.

The gmtime() function returns a pointer to a structure representing the time in the GMT time zone.

These functions return a pointer to a datetime structure. If we want to make sure its value does not change unexpectedly we should make a copy of it by dereferencing the pointer. To learn about dereferencing, see the C++ Dereference tutorial.

Example
Get a datetime structure and output the current hour:

time_t timestamp = time(&timestamp);
struct tm datetime = *localtime(&timestamp);

cout << datetime.tm_hour;
Display Dates
So far we have been using the ctime() function to display the date contained in a timestamp. To display dates from a datetime structure we can use the asctime() function.

Example
Display the date represented by a datetime structure:

time_t timestamp = time(NULL);
struct tm datetime = *localtime(&timestamp);

cout << asctime(&datetime);
Note: The asctime() function does not correct invalid dates. For example, if you set the day of the month to 32 it will display 32. The mktime() function can correct these kinds of errors:

Example
Correct a date before displaying it:

// Create the datetime structure and use mktime to correct mistakes
struct tm datetime;
datetime.tm_year = 2022 - 1900; // Number of years since 1900
datetime.tm_mon = 0; // 0 is January
datetime.tm_mday = 32;
datetime.tm_hour = 0; datetime.tm_min = 0; datetime.tm_sec = 0;
datetime.tm_isdst = -1;
mktime(&datetime);

cout << asctime(&datetime);
The ctime() and asctime() functions allow us to display the date but they do not allow us to choose how it is displayed.

To choose how a date is displayed we can use the strftime() function.

Example
Represent the current date in different ways:

time_t timestamp = time(NULL);
struct tm datetime = *localtime(&timestamp);

char output[50];

strftime(output, 50, "%B %e, %Y", &datetime);
cout << output << "\n";

strftime(output, 50, "%I:%M:%S %p", &datetime);
cout << output << "\n";

strftime(output, 50, "%m/%d/%y", &datetime);
cout << output << "\n";

strftime(output, 50, "%a %b %e %H:%M:%S %Y", &datetime);
cout << output << "\n";
The strftime() function formats a date and writes it as a C-style string into a char array. It has four parameters:

The first parameter points to the char array where the formatted date will be written.
The second parameter specifies the space available in the array.
The third parameter allows us to choose how the date is formatted using format specifiers.
The last parameter is a pointer to the datetime structure which contains the date we want to display.
The following table has some useful format specifiers. For a more complete list, look at the strftime() reference page.

Format Specifier	Description	Example
%a	Short representation of the weekday	Fri
%b	Short representation of the month name	Dec
%B	Full representation of the month name	December
%d	Day of the month with leading zero	09
%e	Day of the month with leading spaces	 9
%H	24-hour format of an hour	14
%I	12-hour format of an hour	02
%M	Minutes within an hour	30
%p	AM or PM	PM
%S	Seconds within a minute	01
%y	2-digit year representation	23
%Y	4-digit year representation	2023
Measuring Time
There are two different functions that can be used to measure differences in time.

The difftime() function measures the number of seconds that passed between two different time stamps. This is useful when measuring time differences between dates.

Example
Measure the time difference between two timestamps

time_t now;
time_t nextyear;
struct tm datetime;

now = time(NULL);
datetime = *localtime(&now);
datetime.tm_year = datetime.tm_year + 1;
datetime.tm_mon = 0;
datetime.tm_mday = 1;
datetime.tm_hour = 0; datetime.tm_min = 0; datetime.tm_sec = 0;
datetime.tm_isdst = -1;
nextyear = mktime(&datetime);

int diff = difftime(nextyear, now);

cout << diff << " seconds until next year";
The clock() function is useful for measuring short intervals of time while the program is running. It is more precise than the difftime() function.

Each call to the clock function returns a special kind of timestamp measured in clocks (a unit of time that depends on how the library was implemented) which has a data type clock_t. To measure a time difference, store a timestamp at two different moments in time and then subtract them. The time difference is measured in clocks, but you can convert it into seconds by dividing it by the CLOCKS_PER_SEC constant.

Example
Measure how long it takes for the program to run:

clock_t before = clock();
int k = 0;
for(int i = 0; i < 100000; i++) {
  k += i;
}
clock_t duration = clock() - before;
cout << "Duration: " << (float)duration / CLOCKS_PER_SEC << " seconds";
Note: Make sure to cast the value to a float or double type before dividing, otherwise it may result in an integer division which would cause the decimal part to be cut off.