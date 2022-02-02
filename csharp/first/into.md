# OOP

In OOP a **class** is what encapsulates related data.

For example, A user has a first name and a last name. A User class might look something like

```c#
/*
    This class is implemented as simple as possble, without using the new c# features.
    We write it this way do build solid understanding.
*/
class User  {
    private string firstName;
    private string lastName;

    public string FullName {
        get {
            return firstName + " " + lastName;
        }
        set {
            // assume value is in the for "firstName lastName"
            firstName = value.Split(' ')[0];
            lastName = value.Split(' ')[1];
        }
    }

    public User() {
        this.firstName = "";
        this.lastName = "";
    }

    public User(string firstName, string lastName) {
        this.firstName = firstName;
        this.lastame = lastName;
    }

    // Method
    public void SayHello() {
        Console.WriteLine("hello from " + this.FullName);
    }
}

```

An ```Object``` is an instance of a ```Class```.

For example, in the following code

```c#
User noname = new User();
User yossi = new User("yossi", "shor");
User tal = new User("tal", "glanzman");
```

The ```User``` is a class, ```yossi``` and ```tal``` are objects.


In C#, a class has the following components

- fields / members
- properties
- constructor
- methods

__Fields / Members__ are the data the class holds. Can also be refered to as it's state. In the ```User``` class those are ```firstName``` and ```lastName```.

- Fields represent the internal state of the object
- Usually we don't want to provide direct access to the fields since unmonitored access can lead to corrupted state

__Properties__ are get/set functions, providing access to members. In the ```User```, the ```FullName``` is the property, providing a getter and a setter.

- We can use properties to validate input, compute trivial stuff, provide defaults etc...

__Methods__ are just functions the are bound to a specific object

- The bound object is refered by the ```this``` keyword
- A mtehod have complete access the the object's fields

For example, in python we can have the following code

```python
class User:
    def __init__(self, name):
        self.name = name
    
    def sayHello(self):
        print("hello from: " + self.name)
```

the ```this``` keyword in c# is provided to us without decleration as in the python case.

__Constructor__ is a special kind of method used to initialize the object

- The constructor is a method with the same name of the class
- Practically, the constructor is the method being invoke when using the ```new``` keyword 
- It is the python's ```__init__``` equivalent


## Visibility modifiers

- **private** - Only the same object can access
- **public** - Everyone can access
- **internal** - Accessible only within the same dll/project (We can also directly specify specific project with access - pretty isoteric)
- **protected** - Accessible only within the inheritence tree