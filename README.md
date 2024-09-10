# Android-Interview-Questions
Guide to be prepared for an Android Interview.
## KOTLIN QUESTIONS

### What is a data class in Kotlin?
A data class is a class designed to hold data, its primary constructor needs at least one parameter, a data class cannot be open for inheritance and automatically comes with some default functions like:
```kotlin
- copy()
- equals()
- hashCode()
- toString()
- componentN()
```
- copy() : Creates a new instance of a data class by copying an existing instance and allows modification of certain properties.
  
- equals() : Checks if two instances of a data class are equal by comparing their properties, it returns a Boolean. If two objects have the same hash code, equals() is used to verify if they are truly equal in terms of their data.
  
- hashCode() : Generates a hash code for a data class instance based on its properties. Generates an integer (hash code) that serves to identify the object in hash-based collections, like HashMap or HashSet. However, having the same hash code does not guarantee that two objects are equal, as different objects can produce the same hash code (this is called a collision).
  
- toString() : Provides a string representation of the data class, including its class name and property values.

- componentN() : The componentN functions allow you to destructure instances of data classes into their individual properties. This feature is particularly useful when you want to work with individual properties of a data class without directly accessing them by name.

```kotlin
val user = User("Alice", 30, "alice@example.com")

// Destructuring declaration
val (name, age, email) = user

println(name)  // Output: Alice
println(age)   // Output: 30
println(email) // Output: alice@example.com

```

### What is a class in Kotlin?
It is a template that defines attributes and methods, objects can be created from a class. It is used to define the structure and behavior of objects in the real world.
- It can include a primary constructor and one or more secondary constructors.
- Properties can be mutable or immutable.
- To inherit from a class, the keyword "open" is used.
- Classes are final if they are not marked with the "open" keyword.
- The base class is known as the superclass, and the derived class is known as the subclass.

### Data class vs Class
The purpose of a data class is to hold data, unlike a normal class. It must have at least one parameter, cannot be open, and has default methods that a normal class does not have. Therefore, data classes cannot be inherited.

### Which class do all Kotlin classes have in common?
They share the Any class, which acts as a superclass for all Kotlin classes. It is similar to the Object class in Java.

### Explanation of Any
The superclass of all non-null types in Kotlin, this means that any non-nullable type inherits from Any.<br>
Includes fundamental methods such as  `equals()`, `hashCode()`, and `toString()`.

### Explanation of Any?
`Any?` can hold any type of value, including null. In Kotlin, the ? after a type indicates that the type is nullable, meaning it can represent either a value of that type or null.<br>
is used when you want to allow a variable, parameter, or return value to be any type, including `null`.

### Explanation of Nothing
In Kotlin `Nothing` is a special type that represents a value that never exists. it is used to indicate that a function or expression will never successfully complete, either because it always throws an exception or because it enters an infinite loop.

- It consistently throw an exception.
- It is specifically designed to handle fatal errors.
- It clearly signals to the compiler and other developers that a particular execution path should never continue normally.

The primary purpose of `Nothing` is to improve code clarity and safety, particularly in error handling and control flow.

```kotlin
fun throwError(message: String): Nothing {
    throw IllegalArgumentException(message)
}
```
### Explanation of Unit
In Kotlin `Unit` is a special type that represents the absence of a meaningful value. it is the equivalent of `void` in other languages like Java.<br>
When a function  doesn’t explicitly return a value, its return type is inferred as `Unit`.

- Functions that perform actions but do not need to return a result should use `Unit`.
  
```kotlin
fun showMessage(message: String): Unit {
    println(message)
}
```
### Explanation of Null safety
Null safety in Kotlin was designed to prevent nullPointerExceptions. which are common sources of runtime crashes in many programming languages. Kotlin handles null safety through its type system, which distinguishes between nullable and non-nullable types.

- By default, all the types in Kotlin are non-nullable. This means that a variable of a non-nullable type cannot hold a `null` value.
```kotlin
var name: String = "John"
// name = null // This will cause a compilation error
```
- To allow a variable to hold a `null` value, you need to explicitly declare it as nullable by appending a question mark `?` to the type.
```kotlin
var name: String? = "John"
name = null // This is allowed
```
- When working with nullables types, you can use the safe call operator `?.`, if the variable is `null`, the expression returns `null` instead of throwing a `NullPointerException`.
```kotlin
val length: Int? = name?.length // if name is null, length will also be null.
```
- The Elvis operator `?:` provides a way to handle `null` values by providing a default value if the expression is `null`
```kotlin
val length: Int = name?.length ?: 0 // if name is null, length will be set to 0
```
- If you are sure that a variable is not `null`, you can use the non-null assertion operator `!!` it should be used cautiosly because if the varibable is null it will throw a  `NullPointerException`.
```kotlin
val length: Int = name!!.length //if name is null, this will throw a NullPointerException.
```
- You can use the `as?` operator for safe casting. If the cast fails, it returns `null` instead of throwing a `ClassCastException`.
```kotlin
val number: Int? = someObject as? Int
```
- You can use the `let` function with the safe call operator to execute a block of code only if the variable is not `null`.
```kotlin
name?.let {
    println("Name length: ${it.length}")
}
```
In summary null safety help us to minimize the risk of null pointer exceptions by making nullability explicit and providing safe ways to handle `null` values.

### Explain final keyword
It is used to prevent a class, method or property from being changed, (overridden or inherited). By default classes in Kotlin are `final`, meaning you can't inherit from them unless you mark them as `open`.

```kotlin
open class Animal {
    final fun makeSound() {
        println("Some sound")
    }
}

class Dog : Animal() {
    // I can't override the makeSound method here.
}
```
  
### Explain Inheritance
Allows creating new classes based on existing ones.
- The keyword open is used to indicate that a class can be inherited.
- Classes are final if not marked with the open keyword.
- The base class is known as the superclass, and the derived class as the subclass.
- You can alter the behavior of an inherited method using the override keyword.

In summary, inheritance allows creating class hierarchies, reusing code, extending functionalities, and achieving a more organized programming structure.

### What is polymorphism?
- The ability of objects from different classes to behave in multiple ways.
- Overriding or Overloading a method are types of polymorphism.
- We can achieve polymorphism through inheritance or interfaces.
- Polymorphism also allows treating objects from different subclasses as instances of a common superclass. For example, you can create an instance of Cat, but when used in a context where Animal is expected, it behaves like an Animal.

### What is overloading?
Method overloading refers to having methods in the same class with the same name but different parameters.

### What is overriding?
Method overriding refers to providing a new implementation of a method in a subclass that is already defined in its superclass, giving it a new behavior in the subclass.

### What is abstraction?
It refers to modeling real-world objects by focusing on their essential aspects and relevant behaviors while hiding internal details. Examples of abstraction include classes and objects that define properties and methods.

### What is encapsulation?
It refers to the practice of hiding the internal details of a class or object, and this is achieved using access modifiers. The benefits of encapsulation are the following:<br>

- Hiding details: The internal details of a class are hidden and cannot be modified from outside the class.

- Improves security: it limits access to the member of a class and helps prevent data corruption.

- Facilitates maintenance: Internal changes can be made to the class without affecting the code that interacts with the class.

- Promotes good practices: Access is enforced through public methods.

### What are access modifiers?
Access modifiers are used to control the visibility of classes, properties, and functions. These modifiers determine which parts of the code can access the member of a class or package.

- public modifier : Members marked as public are accessible from anywhere in the code.

- internal modifier : Members marked as internal are only accessible within the same module.

- protected modifier: Members marked as protected are accessible in the class where they are defined and in their subclasses.

- private modifier: Members marked as private are only accessible to the class in which they are defined.

### What are abstract classes?
These are classes that cannot be instantiated but can be used as bases for other classes. They are useful for defining a common structure for related classes, but creating objects from the base class doesn't have a practical purpose.

- Cannot be instantiated.
- Can have properties and methods.
- Methods can be abstract or concrete.
- Abstract properties and methods must  be implemented in the subclass that make use of the abstract class.
```kotlin
abstract class Shape {
   var color: String = "unknown"

   abstract fun calculateArea() : Double

   fun description() {
       println("this shape has an unknown color")
   }
}
```
Use abstract class when a class doesn't make sense to be instantiated. it is a template for other classes (class hierarchy).

### What are interfaces?
Allow defining abstract methods and properties that must be provided by the classes implementing them. it is a contract that a class has to follow.
- A class can implement multiple interfaces.
- Interfaces cannot be instantiated.
- An interface can also have concrete methods.
- These concrete methods can be overriden.
- They can define properties with a default value or have abstract properties.
```kotlin
interface Drawable { 

   val myProperty: Int get() = 42

   fun draw() 

   fun drawLine() {
       println("draw line")
   }

}
```
They allow us to define common behaviors outside the class hierarchy.
interfaces help us to:
- Abstract behaviors.
- Apply polymorphism.
- Unify layers.

### Explain composition
instead of implementing all functionalities in a single class, they are modularized into independent instances.

### Explain composition over inheritance
Preferably use composition over inheritance, classes should have polymorphic behavior through composition rather than inheritance, achieved by using interfaces. Use composition to reuse behaviors and inheritance to inherit properties.

### What is the difference between val and var?
`val` means that is immutable, its value cannot change once initialized, they are read-only variables. `var`, on other hand, means that it can change its value, they are read-write variables.

### What is the difference between val and const?
Both are immutable, but the value of `const` must be known at compile time, whereas the value of `val`can also be assigned at runtime.<br>
A constant can only be initialized as a `String` or with a primitive value. Constants must be in a companion object or declared as a top-level property.

### What is a companion object?
It is the way Kotlin handles statics. They have to be declared within a class. The class can access the members of the companion object, and it can implement interfaces. it is not necessary to instantiate a class to access the companion object.

### What is the difference between == and ===?
== is used to compare the values stored in variables, and === is used to check if the references of the variables are equal or not. However, in the case of primitive types, === also checks the value, not just the reference.

### What are lazy and lateinit?
They are two ways to initialize variables until they are needed. Both are used to improve performance and reduce memory usage when you have variables that do not to be initialized immediately.

### Explain lateinit
Means late initialization. It is used when you are certain that the property will be initialized before it is used, but you want to delay the initialization. It is used to declare properties that cannot be null.

Use cases:
- Properties that need to be initialized in a secondary constructor.
- Properties that need to be initialized in the lifecycle, for example in onCreate.

Characteristics:
- Does not allow primitive values (Double, Int, Boolean, Char, etc).
- You cannot use lateinit with objects that can be nullable.
- It must be ensured that lateinit was initialized before use.
- If not initialized, it throws a LateInitPropertyAccessException.
- isInitialized checks if it was initialized.
- Can only be used with mutable properties (var).

```kotlin
lateinit var someValue: String
```

### Explain lazy
Means lazy initialization, you can postpone the initialization of a property until the moment it is required.

Use cases:
- It is used when you want to perform a costly initialization only when t is actually needed, which helps improve performance.
- Database connections.
- Network requests.

Characteristics:
- `lazy` can only be initialized once and will retain its value.
- it makes use of lambdas.
- it can contain any type of object.

```kotlin
val lazyInt: Int by lazy { 42 }
```

### Explain Sequences
In Kotlin, sequences are an alternative to traditional collections. While collections like `List` or `Set` store all elements in memory, sequences generate them as needed, which is known as lazy processing. This means that operations on sequences are only performed when the final result is required, in contrast to collections where each intermediate step generates a new collection immediately.

Sequence performs all the processing steps one-by-one for every single element. In turn, Iterable completes each step for the whole collection and then proceeds to the next step.

So, the sequences let you avoid building results of intermediate steps, therefore improving the performance of the whole collection processing chain. However, the lazy nature of sequences adds some overhead which may be significant when processing smaller collections or doing simpler computations. Hence, you should consider both Sequence and Iterable and decide which one is better for your case.

Example: 
![image](https://github.com/user-attachments/assets/10d8da57-d2fe-4e32-84e6-f3c9e36c55e6)

### Data Structures

### List
A list is an ordered collection that can contain duplicate elements. Kotlin provides two types of lists:
- `List` (immutable): You cannot modify the list once it is created.
- `MutableList` (mutable): You can add, remove, or change elements.

### Set
A set is an unordered collection that does not allow duplicate elements. Like lists, there are two versions:
- `Set` (immutable): Elements cannot be changed.
- `MutableSet` (mutable): You can add and remove elements.

### Map
A map is a collection that associates keys with values. Kotlin provides immutable and mutable maps.
- `Map` (immutable): Keys and values cannot be modified.
- `MutableMap` (mutable): You can add, remove, or update key-value pairs.

### Array
An Array is a fixed-size collection that can store data of specific type. Unlike lists, arrays have a predefined size and cannot grow or shrink once created.

### ArrayList

