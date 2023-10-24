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

**3. `get(string $name): mixed`:**
   - Accepts a string parameter `$name`, which represents the name of the item to retrieve.
   - Check if the item exists in the container. If it does, return the item.
   - If the item does not exist, throw an exception (e.g., `ItemNotFoundException`).

**4. `set(string $name, $item): void`:**
   - Accepts a string parameter `$name` and an `$item` to be set in the container.
   - If `$item` is a callable, store it in the container.
   - If `$item` is not a callable, consider it a regular item.
   
**5. Autowiring for Class Creation:**
   - If the requested item is a class name (FQCN) and does not exist in the container, attempt to create an instance of the class with its dependencies resolved through autowiring.
   - Use PHP's Reflection to inspect the class's constructor and its parameter types.
   - Try to resolve the dependencies by recursively calling the `get` method for each parameter type.

**6. Exception Handling:**
   - Implement appropriate exception classes, such as `ItemNotFoundException`, to handle errors when items are not found in the container.

**7. Singleton Factory:**
   - When an item is set as a callable, it should act as a singleton factory. This means that the callable should be executed only once, and subsequent calls to `get` for the same item should return the previously created instance.

**8. Usage Example:**
   - Provide a usage example demonstrating how to use the container to store and retrieve items, including autowired class instances.

**9. Documentation:**
   - Include comments and documentation within the code to explain the functionality and usage of the container.

**10. Deliverables:**
   - Provide the PHP class for the DI container.
   - Include a usage example.

This technical specification outlines the requirements for a simple DI container in PHP with autowiring capabilities. Your implementation should adhere to these specifications to provide a functional and reliable DI container.
