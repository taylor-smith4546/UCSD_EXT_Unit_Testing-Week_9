# UCSD Extension: Unit Testing: Supporting Modern Software Development Methods

## Videos: 

[Lecture 9: Test Quality](URL link here)

## Assignment/Classwork:

Quiz #9

Exercise #1:

A simple mocking exercise -

Suppose we have the following to test that security doors are closed:

```java
public class SecurityCentral {
    private final Window window;
    private final Door door;

    public SecurityCentral(Window window, Door door) {
        this.window = window;
        this.door = door;
    }

    void securityOn() {
        window.close();
        door.close();
    }
}
```
In this case, we do not want to use real doors to test that the security method is working. Place door and window mocks objects in the test code.
After execution of securityOn method, the window and door mocks should record all interactions to let us verify that window and door objects were instructed to close themselves.

## Topics Covered: 

o	Static analysis tools

o	Code coverage

o	Code reviews

o	Refactor your tests

o	Running tests with Maven

