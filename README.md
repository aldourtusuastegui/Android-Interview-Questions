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

