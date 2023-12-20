<h2 align=center>Apex REST Callouts</h2>

**Create an Apex class that calls a REST endpoint and write a test class.**

Create an Apex class that calls a REST endpoint to return the name of an animal, write unit tests that achieve 100% code coverage for the class using a mock response, and run your Apex tests.

**Prework**: Be sure the Remote Sites from the first unit are set up.

* Create an Apex class:
  * Name: AnimalLocator
  * Method name: getAnimalNameById
  * The method must accept an Integer and return a String.
  * The method must call https://th-apex-http-callout.herokuapp.com/animals/<id>, replacing <id> with the ID passed into the method
  * The method returns the value of the name property (i.e., the animal name)
* Create a test class:
  * Name: AnimalLocatorTest
  * The test class uses a mock class called AnimalLocatorMock to mock the callout response
* Create unit tests:
  * Unit tests must cover all lines of code included in the AnimalLocator class, resulting in 100% code coverage
  * Run your test class at least once (via Run All tests the Developer Console) before attempting to verify this challenge.

