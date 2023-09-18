# Languages and Compilers

- [ ] [Compiler Design in C](https://www.amazon.com/Compiler-Design-C-Allen-Holub/dp/0131550454)


## C++


### C++ compiling

- Preprocessing: The preprocessor performs tasks like including header files, expanding macros, and removing comments.The output of this stage is an intermediate source code file.
  
- Compiling: The compiler converts the preprocessed source code into assembly code. The output of this stage is object code. (`.o` file)

- Linking: The linker combines the object code with the code of the library functions and generates an executable file.

### C++ overload and override

- Overload: Overload is a compile-time polymorphism where two or more functions can have the same name but different parameters.
  - How to do it: 
    - Different number of parameters
    - Different data types of parameters
    - Different sequence of data types of parameters
- Override: Override is a run-time polymorphism where a function call is resolved during run-time, not at the compile time.
  - How to do it: 
    - Inheritance
    - Virtual functions

Override example:

```cpp
class Base {
public:
    virtual void foo() {
        // 基类的实现
    }
};

class Derived : public Base {
public:
    void foo() override {
        // 派生类提供的覆盖实现
    }
};
```

About override and virtual functions:
- Only virtual functions can be overridden.
- Virual functions can be called directly using the base class pointer.

### C++ templates

- Function templates: A function template is a blueprint for creating the functions. It allows us to create a function template whose functionality can be adapted to more than one type or class without repeating the entire code for each type.

```cpp
template <typename T>
T max(T a, T b) {
    return a > b ? a : b;
}
```

- Class templates: A class template is a blueprint for creating the classes. It allows us to create a class template whose functionality can be adapted to more than one type or class without repeating the entire code for each type.

```cpp
template <typename T>
class Stack {
private:
    vector<T> elems;
public:
    void push(T const&);
    void pop();
    T top() const;
    bool empty() const {
        return elems.empty();
    }
};
```

- Template specialization: Template specialization allows us to have different code for a particular data type.


---

## Comparsion

### Python

- Python is an interpreted language. It is compiled and run at the same time.
- Python is dynamically typed. It means that the type of a variable is decided at the run time.
- Python is strongly typed. It means that the type of a variable is not changed implicitly.
- Python is object-oriented. It means that Python supports object-oriented style or technique of programming that encapsulates code within objects.
  
### Javascript

- Javascript is an interpreted language. It is compiled and run at the same time.
- Javascript is dynamically typed. It means that the type of a variable is decided at the run time.
- Javascript is weakly typed. It means that the type of a variable can be changed implicitly.
- Javascript is object-oriented. It means that Javascript supports object-oriented style or technique of programming that encapsulates code within objects.

### Compare C++ and Javascript

- C++ is a compiled language. It means that C++ code is converted into machine language at compile time.
- C++ is statically typed. It means that the type of a variable is decided at the compile time.
- C++ is strongly typed. It means that the type of a variable is not changed implicitly.
- C++ is object-oriented. It means that C++ supports object-oriented style or technique of programming that encapsulates code within objects.

#### Performance

