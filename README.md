# poo
poo

#c++
#include<iostream>
using namespace std;

class Encapsulation
{
private:
    // data hidden from outside world
    int x;
public:
    // function to set value of 
    // variable x
    void set(int a)
    {
        x = a;
    }
    // function to return value of
    // variable x
    int get()
    {
        return x;
    }
};
class Polymorphism
{
public:

    // function with 1 int parameter
    void func(int x)
    {
        cout << "value of x is " << x << endl;
    }

    // function with same name but 1 double parameter
    void func(double x)
    {
        cout << "value of x is " << x << endl;
    }

    // function with same name and 2 int parameters
    void func(int x, int y)
    {
        cout << "value of x and y is " << x << ", " << y << endl;
    }
};
class Parent {
public:
    int id_p;
};

// Sub class inheriting from Base Class(Parent)
class Child : public Parent {
public:
    int id_c;
};
class Complex {
private:
    int real, imag;
public:
    Complex(int r = 0, int i = 0) { real = r;   imag = i; }

    // This is automatically called when '+' is used with
    // between two Complex objects
    Complex operator + (Complex const& obj) {
        Complex res;
        res.real = real + obj.real;
        res.imag = imag + obj.imag;
        return res;
    }
    void print() { cout << real << " + i" << imag << '\n'; }
};
class base {
public:
    virtual void print()
    {
        cout << "print base class\n";
    }

    void show()
    {
        cout << "show base class\n";
    }
};

class derived : public base {
public:
    void print()
    {
        cout << "print derived class\n";
    }

    void show()
    {
        cout << "show derived class\n";
    }
};

// main function
int main()
{
    Encapsulation obj;
    obj.set(5);
    cout << obj.get();

    Polymorphism obj1;
    // Which function is called will depend on the parameters passed
    // The first 'func' is called 
    obj1.func(7);
    // The second 'func' is called
    obj1.func(9.132);
    // The third 'func' is called
    obj1.func(85, 64);

    Child obj2;

    // An object of class child has all data members
    // and member functions of class parent
    obj2.id_c = 7;
    obj2.id_p = 91;
    cout << "Child id is: " << obj2.id_c << '\n';
    cout << "Parent id is: " << obj2.id_p << '\n';

    Complex c1(10, 5), c2(2, 4);
    Complex c3 = c1 + c2;
    c3.print();

    base* bptr;
    derived d;
    bptr = &d;
    // Virtual function, binded at runtime
    bptr->print();
    // Non-virtual function, binded at compile time
    bptr->show();

    return 0;
}

//python

# incapsulare si mostenire
print("Incapsulare si mostenire+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++")
class Base:
    def __init__(self):
        # Protected member
        self._a = 2

# Creating a derived class
class Derived(Base):
    def __init__(self):
        # Calling constructor of
        # Base class
        Base.__init__(self)
        print("Calling protected member of base class: ", self._a)

        # Modify the protected variable:
        self._a = 3
        print("Calling modified protected member outside class: ", self._a)

obj1 = Derived()
obj2 = Base()
# Calling protected member
# Can be accessed but should not be done due to convention
print("Accessing protected member of obj1: ", obj1._a)
# Accessing the protected variable outside
print("Accessing protected member of obj2: ", obj2._a)

#polymorphism
print("polymorphism+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++")
class Bird:
    def intro(self):
        print("There are many types of birds.")

    def flight(self):
        print("Most of the birds can fly but some cannot.")

class sparrow(Bird):
    def flight(self):
        print("Sparrows can fly.")

class ostrich(Bird):
    def flight(self):
        print("Ostriches cannot fly.")

obj_bird = Bird()
obj_spr = sparrow()
obj_ost = ostrich()

obj_bird.intro()
obj_bird.flight()

obj_spr.intro()
obj_spr.flight()

obj_ost.intro()
obj_ost.flight()

# Supraincarcare de operatori
print("Supraincarcare de operatori+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++")
# Python Program to perform addition
# of two complex numbers using binary
# + operator overloading.

class complex:
    def __init__(self, a, b):
        self.a = a
        self.b = b

    # adding two objects
    def __add__(self, other):
        return self.a + other.a, self.b + other.b


Ob1 = complex(1, 2)
Ob2 = complex(2, 3)
Ob3 = Ob1 + Ob2
print(Ob3)

#functii virtuale
print("functii virtuale+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ ")


class Super:
    def method(self):
        print('in Super.method')


class Sub(Super):
    def method(self):  # override method
        print('starting Sub.method')  # add actions here
        Super.method(self)  # run default action
        print('ending Sub.method')


x = Super()  # make a Super instance
x.method()  # runs Super.method

x = Sub()  # make a Sub instance
x.method()  # runs Sub.method, which calls Super.method
