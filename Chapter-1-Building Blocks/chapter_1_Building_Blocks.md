## Building Blocks
#### Major Components of Java
```
Key commands:

- javac : Converts .java source files into .class bytecode
- java : Executes the program
- jar : Packages files together
- javadoc : Generates documentation
```

#### Fields and Methods
- methods and fields, more generally known as variables. Together these are called the members of the class.

#### Creating a main() Method
The rules for what a Java file contains:
- Each file can contain only one public class.
- The filename must match the class name, including case, and have a .java extension.
- If the Java class is an entry point for the program, it must contain a valid main() method.

#### Constructors
- The name of the constructor matches the name of the class, and there’s no return type.

#### Following the Order of Initialization
- Fields and instance initializer blocks are run in the order in which they appear in the file.
- The constructor runs after all fields and instance initializer blocks have run.

#### Understanding Data Type
###### Answare:
- & can have integral as well as boolean operands.
- Unlike &&, & will not "short circuit" the expression if used on boolean parameters.

###### Explanation:
- integral types means byte, short, int, long, and char

As per Section 4.1 of JLS -
- The integral types are byte, short, int, and long, whose values are 8-bit, 16-bit, 32-bit and 64-bit signed two's-complement integers, respectively, and char, whose values are 16-bit unsigned integers representing UTF-16 code units.

The following method returns -1 for all values of x:
```
int printMe(int x){
    int y = x ^ ~x;
    return y;
}
```

###### Explanation:
- This method will always return -1.
- ~ is bitwise negation operator that flips (i.e. it changes a 0 to a 1 and a 1 to a 0) each bit of the given integral value.
- ^ is bitwise xor operator that performs an "xor" (aka exclusive or, in which, the result is 1 only if exactly one of the two operands is 1) operation on each bit of the two operands. Therefore, performing x ^ ~x will return an integer with all bits set to 1, which is same as -1.

###### For example:
```
int x = 2;   //bit pattern of 2 is    : 00000000 00000000 00000000 00000010
int y = ~x; //bit pattern of ~2 is : 11111111 11111111 11111111 11111101, which is same as -3.
int z = x ^ y;  //bit pattern is      : 11111111 11111111 11111111 11111111, which is same as -1.
System.out.println(z); //prints -1
```
###### Explanation:
- Observe that the bits of the number produced by doing ~x are opposite of the bits in the original int value. (The original variable is unchanged.)
- If you want to know why ~2 is same as -3 or why -1 has all bits set to 1, just read about 2's complement method of representing negative integers.
- For the purpose of the exam, you just need to know that x ^ ~x will always be -1.

#### The Primitive Types
- The byte, short, int, and long types are used for integer values without decimal points.
- Each numeric type uses twice as many bits as the smaller similar type. For example, short uses twice as many bits as byte does.
- All of the numeric types are signed and reserve one of their bits to cover a negative range. For example, instead of byte covering 0 to 255 (or even 1 to 256 ) it actually covers -128 to 127.
- A float requires the letter f or F following the number so Java knows it is a float. Without an f or F, Java interprets a decimal value as a double.
- A long requires the letter l or L following the number so Java knows it is a long. Without an l or L , Java interprets a number without a decimal point as an int in most scenarios.

#### Literals and the Underscore Character
```
OK(Valid).

int million2 = 1_000_000;
double annoyingButLegal = 1_00_0.0_0;
reallyUgly = 1__________2;
```

### Identifying Identifiers
There are only four rules to remember for legal identifiers:
- Identifiers must begin with a letter, a currency symbol, or a symbol. Currency symbols include dollar ( $ ), yuan ( ¥ ), euro ( € ), and so on.
- Identifiers can include numbers but not start with them.
- A single underscore _ is not allowed as an identifier.
- You cannot use the same name as a Java reserved word. A reserved word is a special word that Java has held aside so that you are not allowed to use it. Remember that Java is case sensitive, so you can use versions of the keywords that only differ in case.

#### Declaring Multiple Variables
- You can also declare and initialize multiple variables in the same statement as long as they are all of the same type.
- int num, String value; // DOES NOT COMPILE
- This code doesn’t compile because it tries to declare multiple variables of different types in the same statement.

#### Inferring the Type with var
- A var is still a specific type defined at compile time. It does not change type at runtime.
- All the types declared on a single line must be the same type and share the same declaration.
- A var cannot be initialized with a null value without a type, it can be reassigned a null value after it is declared, provided that the underlying data type is a reference type
- A var is only used for local variable type inference
- Cannot use in constructors, method parameters, type return, or instance variables
- var is not a reserved word and allowed to be used as an identifier(name variable).
- A reserved type name means it cannot be used to define a type, such as a class, interface, or enum.

#### Reviewing Scope
- Local variables: In scope from declaration to the end of the block
- Method parameters: In scope for the duration of the method
- Instance variables: In scope from declaration until the object is eligible for garbage collection
- Class variables: In scope from declaration until the program ends.