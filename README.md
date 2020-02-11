# UCSD Extension: Unit Testing: Supporting Modern Software Development Methods

## Videos: 

[Lecture 9: Test Quality](URL link here)

## Assignment/Classwork:

Quiz #9

Exercise #1:

Clean this Mess

The listing below presents a naive implementation of the Fridge class. It allows one to put food into
the fridge, take it out, and inspect it to see whether something is in there.

Fridge Implementation
```java
public class Fridge {
 private Collection<String> food = new HashSet<String>();
 public boolean put(String item) {
 return food.add(item);
 }
 public boolean contains(String item) {
 return food.contains(item);
 }
 public void take(String item) throws NoSuchItemException {
 boolean result = food.remove(item);
 if (!result) {
 throw new NoSuchItemException(item
 + " not found in the fridge");
 }
 }
}
```

The next two listings show test code of the Fridge class, which - after everything we have explored
up to now, and taking a mere glance at the code - we can say is a complete mess! It works, which
means it tests some features of the SUT, but it could have been much better written. I hope to never
see anything like this again in the rest of my life. Anyway, your task for now is to clean this mess!
Use the knowledge of high-quality testing you have gained from this chapter, but also refer to the
examples given previously, in order to rewrite this test! For example, you should probably take care
of:

• the proper naming of test classes, methods and variables,

• the use of parameterized tests,

• duplicated code,

• and many more issues that are hidden there.

Make sure you do not loose any test case by redesigning this test class!
The two test methods of the FoodTesting class are shown below:

testFridge() method
```java
@Test
void testFridge() {
 Fridge fridge = new Fridge();
 fridge.put("cheese");
 assertEquals(true, fridge.contains("cheese"));
 assertEquals(false, fridge.put("cheese"));
 assertEquals(true, fridge.contains("cheese"));
 assertEquals(false, fridge.contains("ham"));
 fridge.put("ham");
 assertEquals(true, fridge.contains("cheese"));
 assertEquals(true, fridge.contains("ham"));
 try {
 fridge.take("sausage");
 fail("There was no sausage in the fridge!");
 } catch (NoSuchItemException e) {
 // ok
 }
 ```
 
testPutTake() method
```java
@Test
void testPutTake() throws NoSuchItemException {
 Fridge fridge = new Fridge();
 List<String> food = new ArrayList<String>();
 food.add("yogurt");
 food.add("milk");
 food.add("eggs");
 for (String item : food) {
 fridge.put(item);
 assertEquals(true, fridge.contains(item));
 fridge.take(item);
 assertEquals(false, fridge.contains(item));
 }
 for (String item : food) {
 try {
 fridge.take(item);
 fail("there was no " + item + " in the fridge");
 } catch (NoSuchItemException e) {
 assertEquals(true, e.getMessage().contains(item));
 }
 }
}
```


## Topics Covered: 

o	Static analysis tools

o	Code coverage

o	Code reviews

o	Refactor your tests

o	Running tests with Maven

