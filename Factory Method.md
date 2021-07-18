# :truck:Factory Method

Factory method is Creational pattern that provide an interface for creating an object in a super class , but allows subclasses to alter the type of objects that will be created.



## :disappointed:Problem

Imagine that you’re creating a logistics management application. The first version of your app can only handle transportation by trucks, so the bulk of your code lives inside the `Truck` class.
After a while, your app becomes pretty popular. Each day you receive dozens of requests from sea transportation companies to incorporate sea logistics into the app.



## :smile:Solution

The Factory Method pattern suggests that you replace direct object construction calls (using the new operator) with calls to a special factory method. Don’t worry: the objects are still created via the new operator, but it’s being called from within the factory method. Objects returned by a factory method are
often referred to as `“products.”`



## :bulb:Applicability

Use the Factory Method when you don’t know beforehand the exact types and dependencies of the objects your code shouldwork with.

 **Use the Factory Method when you want to provide users of**
**your library or framework with a way to extend its internal**
**components.**

**Use the Factory Method when you want to save system**
**resources by reusing existing objects instead of rebuilding**
**them each time.**



#### :thinking: Pros and Cons

:heavy_check_mark: You avoid tight coupling between the creator and the concrete products.
:heavy_check_mark: Single Responsibility Principle. You can move the product creation code into one place in the program,making the code easier to support.
:heavy_check_mark: Open/Closed Principle. You can introduce new types of products into the program without breaking existing client code.

:heavy_multiplication_x:The code may become more complicated since you need to introduce a lot of new subclasses to implement the pattern. The best case scenario is when you’re introducing the pattern into an existing hierarchy of creator classes.



#### :arrows_counterclockwise:Relations with Other Patterns

- Many designs start by using <u>Factory Method</u> (less complicated and more customizable via subclasses) and evolve toward <u>Abstract Factory</u>, <u>Prototype</u>, or <u>Builder</u> (more flexible, but more complicated).
- <u>Abstract Factory</u> classes are often based on a set of Factory Methods, but you can also use <u>Prototype</u> to compose the methods on these classes.
- You can use <u>Factory Method</u> along with Iterator to let collection subclasses return different types of iterators that are compatible with the collections.
- <u>Prototype</u> isn’t based on inheritance, so it doesn’t have its drawbacks. On the other hand, Prototype requires a complicated initialization of the cloned object. <u>Factory Method</u> is based on inheritance but doesn’t require an initialization step.
-  <u>Factory Method</u> is a specialization of Template Method. At the same time, a Factory Method may serve as a step in a large Template Method.

