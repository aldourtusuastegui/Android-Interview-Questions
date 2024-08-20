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
