**Technical Specification: Simple DI-Container with Autowiring in PHP**

**1. Introduction:**
You are tasked with creating a simple Dependency Injection (DI) container in PHP that supports autowiring. The container should implement the following methods:

- `get(string $name): mixed`: Retrieves an item from the container by its name. If the item does not exist, it should throw an exception.
- `set(string $name, $item): void`: Sets an item in the container. The item can be a callable, which acts as a singleton factory with on-demand creation.
- If an item with the specified name does not exist in the container, and the name is a Fully Qualified Class Name (FQCN) that exists, the container should attempt to create the class, providing its dependencies through autowiring.

**2. Class Structure:**
You should create a PHP class for the DI container. Here's an example class structure:

```php
class SimpleContainer
{
    private $items = [];
    
    public function get(string $name)
    {
        // Implement the logic to retrieve an item or throw an exception
    }
    
    public function set(string $name, $item)
    {
        // Implement the logic to set an item in the container
    }
    
    // Additional methods and properties as needed
}
```

**3. Autowiring for Class Creation:**
   - If the requested item is a class name (FQCN) and does not exist in the container, attempt to create an instance of the class with its dependencies resolved through autowiring.
   - Use PHP's Reflection to inspect the class's constructor and its parameter types.
   - Try to resolve the dependencies by recursively calling the `get` method for each parameter type.

**4. Exception Handling:**
   - Implement appropriate exception classes, such as `ItemNotFoundException`, to handle errors when items are not found in the container.

**5. Singleton Factory:**
   - When an item is set as a callable, it should act as a singleton factory. This means that the callable should be executed only once, and subsequent calls to `get` for the same item should return the previously created instance.

**6. Usage Example:**
   - Create the `RandomGreetingInterface` with a single method: `random(): string;`. This method should return a random greeting from an array of greetings (e.g., "hello," "good morning," "good evening," and more).

   - Implement the `RandomGreeting` class that implements the `RandomGreetingInterface`. The constructor of the `RandomGreeting` class should accept an array of greetings.

   - Create the `Greeter` class, which should accept a `RandomGreetingInterface` as an argument in its constructor.

   - Implement the `greet(string $name): string` method in the `Greeter` class. This method should return a greeting message in the format `sprintf("%s, %s", $this->randomGreeter->random(), $name)`.

   - Register the `RandomGreetingInterface` as a callable-factory in the container, which returns an instance of the `RandomGreeting` implementation.

   - Use the container's `get` method to create an instance of the `Greeter` class. The container should perform autowiring and provide the `RandomGreeting` implementation to the `Greeter` constructor.

This example demonstrates how the DI container should be used to register and resolve dependencies while leveraging the autowiring feature to wire up the `Greeter` class with the `RandomGreeting` implementation.

**7. Documentation:**
   - Include comments and documentation within the code to explain the functionality and usage of the container.

**8. Coding Standards:**
   - The source code should be located under a "src/" directory.
   - Use Composer as an autoloader.
   - Ensure that the code adheres to PSR standards.
   - Hint: In your solution, please do not create a separate interface for the SimpleContainer class. Additionally, avoid using "PSR-11" in your implementation, as it is a standard that describes containers, and in this task, we want a simple container without creating a new interface.

**9. Leveraging SOLID, DRY, and KISS:**
   - Utilize SOLID principles, Don't Repeat Yourself (DRY), and Keep It Simple, Stupid (KISS) in your code to create a well-structured and maintainable solution.

**10. Final Evaluation:**
   - We will thoroughly evaluate your solution for compliance with PSR standards, adherence to SOLID, DRY, and KISS principles, and the correct implementation of the DI container with autowiring.

This technical specification outlines the requirements for a simple DI container in PHP with autowiring capabilities. Your implementation should adhere to these specifications to provide a functional and reliable DI container.
