#### Understanding Inheritance
- Inheritance is the process by which a subclass automatically includes certain members
  of the class, including primitives, objects, or methods, defined in the parent class.
<br>

#### Declaring a Subclass
![Subclass and superclass declarations](images/figure_6_1.png "Subclass and superclass declarations")
<br>

- All public and protected members are automatically available as part of the child class. If the two classes are in the same package, then package members are available to the child class.
- private members are restricted to the class they are defined in and are never available via inheritance.
<br>

#### Class Modifiers
#### Table: 6.1 Class modifiers
| Modifier   | Description                                                                                           |
|------------|-------------------------------------------------------------------------------------------------------|
| final      | The class may not be extended.                                                                        |
| abstract   | The class is abstract, may contain abstract methods, and requires a concrete subclass to instantiate. |
| sealed     | The class may only be extended by a specific list of classes.                                         |
| non-sealed | A subclass of a sealed class permits potentially unnamed subclasses.                                  |
| static     | Used for static nested classes defined within a class.                                                |
<br>

- The final modifier prevents a class from being extended any further.
<br>

#### Inheriting Object
- All classes inherit from a single class: java.lang.Object, or Object for short.
- Object is the only class that doesn’t have a parent class.
- when you define a new class that extends an existing class, Java does not automatically extend the Object class.
- Primitive types such as int and boolean do not inherit from Object, since they are not classes.
<br>

#### Applying Class Access Modifiers
- A top-level class is one not defined inside another class.
- A .java file can have at most one top-level class.
- You can only have one top-level class.
- A top-level class with protected or private class will lead to a compiler error.
<br>

#### Accessing the this Reference
- The this reference refers to the current instance of the class and can be used to access any member of the class, including inherited members. It can be used in any instance method, constructor, or instance initializer block. It cannot be used when there is no implicit instance of the class, such as in a static method or static initializer block.
<br>

#### Calling the super Reference
<br>

## Declaring Constructors
#### Creating a Constructor
- The name of the constructor, matches the name of the class.
- There is no return type, not even void.
- Constructor parameters can be any valid class, array, or primitive type, including generics, but may not include var.
- A class can have multiple constructors, as long as each constructor has a unique constructor signature.
- The constructor parameters must be distinct.
- Declaring multiple constructors with different signatures is referred to as constructor overloading.
- Constructors are used when creating a new object. This process is called instantiation.
<br>

#### The Default Constructor
- If you don’t include any constructors in the class, Java will create one for you without any parameters.
- The default constructor has an empty parameter list and an empty body.
- This happens during the compile step.
- It only makes an appearance in the compiled file with the .class extension.
- The compiler only inserts the default constructor when no constructors are defined.
- ***private*** constructors in a class tells the compiler not to provide a default no-­argument constructor.
- This is useful when a class has only static methods
<br>

#### Calling Overloaded Constructors with this()
- Constructors can be called only by writing new before the name of the constructor.
- ***this***, refers to an instance of the class.
- ***this()***, refers to a constructor call within the class.
- The ***this()*** call must be the first statement in the constructor.
- The compiler is capable of detecting that this constructor is calling itself infinitely.
<br>

#### Rules you should know about constructors
1. The first statement of every constructor is a call to another constructor within the class using this() , or a call to a constructor in the direct parent class using super() .
2. The super() call may not be used after the first statement of the constructor.
3. If no super() call is declared in a constructor, Java will insert a no-argument super() as the first statement of the constructor.
4. If the parent doesn’t have a no-argument constructor and the child doesn’t define any constructors, the compiler will throw an error and try to insert a default no-argument constructor into the child class.
5. If the parent doesn’t have a no-argument constructor, the compiler requires an explicit call to a parent constructor in each child constructor.
<br>

#### Calling Parent Constructors with super()
- The first statement of every constructor is a call to a parent constructor using ***super()*** or another constructor in the class using ***this()***.
- ***super***, is used to reference members of the parent class,
- ***super()***, calls a parent constructor.
- Calling ***super()*** can only be used as the first statement of the constructor.
<br>

#### Understanding Compiler Enhancements
- Java compiler automatically inserts a call to the no-argument constructor super() if you do not explicitly call ***this()*** or ***super()*** as the first line of a constructor.
- super() always refers to the most direct parent.
<br>

#### Three constructor rules
- The first line of every constructor is a call to a parent constructor using ***super()*** or an overloaded constructor using ***this()***.
- If the constructor does not contain a ***this()*** or ***super()*** reference, then the compiler automatically inserts super() with no arguments as the first line of the constructor.
- If a constructor calls ***super()***, then it must be the first line of the constructor.
<br>

## Initializing Objects

#### Initializing Classes
- invoking all static members in the class hierarchy, starting with the highest superclass and working downward.
1. If there is a superclass Y of X, then initialize class Y first.
2. Process all static variable declarations in the order in which they appear in the class.
3. Process all static initializers in the order in which they appear in the class.
<br>

#### Initializing final Fields
- final static variables must be explicitly assigned a value exactly once.
- They can be assigned values in the line in which they are declared or in an instance initializer.
- final instance fields can also be set in a constructor.
- By the time the constructor completes, all final instance variables must be assigned a value exactly once.
- Local final variables, which are not required to have a value unless they are actually used, final instance variables must be assigned a value.
- each constructor is reviewed individually.
- The compiler detects that a value is never set for type and reports an error on the line where the constructor is declared.
- final instance variable is assigned a value exactly once.
- We can assign a null value to final instance variables as long as they are explicitly set.
<br>

## Initializing Instances
##### Initialize Instance of X
1. Initialize class X if it has not been previously initialized.
2. If there is a superclass Y of X, then initialize the instance of Y first.
3. Process all instance variable declarations in the order in which they appear in the class.
4. Process all instance initializers in the order in which they appear in the class.
5. Initialize the constructor, including any overloaded constructors referenced with this().
<br>

#### rules
- A class is initialized at most once by the JVM before it is referenced or used.
- All static final variables must be assigned a value exactly once, either when they are declared or in a static initializer.
- All final fields must be assigned a value exactly once, either when they are declared, in an instance initializer, or in a constructor.
- Non-final static and instance variables defined without a value are assigned a default value based on their type.
- Order of initialization is as follows: variable declarations, then initializers, and finally constructors.
<br>

#### Overriding a Method
- When a subclass declares a new implementation for an inherited method with the same signature and compatible return type.
<br>

#### rules.
1. The method in the child class must have the same signature as the method in the parent class.
2. The method in the child class must be at least as accessible as the method in the parent class.
3. The method in the child class may not declare a checked exception that is new or broader than the class of any exception declared in the parent class method.
4. If the method returns a value, it must be the same or a subtype of the method in the parent class, known as covariant return types.
<br>

#### Declaring private Methods
- You can’t override private methods since they are not inherited.
<br>

#### Hiding Static Methods
- A hidden method occurs when a child class defines a static method with the same name and signature as an inherited static method defined in a parent class.
5. The method defined in the child class must be marked as static if it is marked as static in a parent class.
<br>

#### Hiding Variables
- Java doesn’t allow variables to be overridden.
- A ***hidden variable*** occurs when a child class defines a variable with the same name as a inherited variable defined in the parent class.
- You can’t override a variable; you can only hide it.
<br>

#### Writing final Methods
- final methods cannot be overridden.
<br>

## Creating Abstract Classes
#### Introducing Abstract Classes - Rules
1. Abstract classes cannot be instantiated directly.
2. Abstract classes may be defined with any number, including zero, of abstract and non-abstract methods.
3. Abstract classes may not be marked as private or final.
4. An abstract class that extends another abstract class inherits all of its abstract methods as its own abstract methods.
5. The first concrete class that extends an abstract class must provide an implementation for all of the inherited abstract methods.


#### Declaring Abstract Methods - Rules
1. Abstract methods may only be defined in abstract classes.
2. Abstract methods may not be declared private or final .
3. Abstract methods must not provide a method body/implementation in the abstract
   class for which is it declared.
4. Implementing an abstract method in a subclass follows the same rules for overriding a
   method. For example, the name and signature must be the same, and the visibility of
   the method in the subclass must be at least as accessible as the method in the parent
   class.

#### Creating a Concrete Class
- A concrete class is a non-abstract class.
- The first concrete subclass that extends an abstract class is required to implement all inherited abstract methods.
<br>

#### Creating Constructors in Abstract Classes
- ***abstract classes*** are initialized with constructors in the same way as non-abstract classes.
<br>

#### abstract and final Modifiers
- Java does not permit a class or method to be marked both abstract and final.
<br>

#### abstract and private Modifiers
- A method cannot be marked as both abstract and private.
<br>

#### abstract and static Modifiers
- A static method can only be hidden, not overridden.
<br>

## Creating Immutable Objects
#### Declaring an Immutable Class
1. Mark the class as final or make all of the constructors private.
2. Mark all the instance variables private and final.
3. Don’t define any setter methods.
4. Don’t allow referenced mutable objects to be modified.
5. Use a constructor to set all properties of the object, making a copy if needed.
<br>

#### Performing a Defensive Copy
- ***defensive copy*** because the copy is being made in case other code does something unexpected.