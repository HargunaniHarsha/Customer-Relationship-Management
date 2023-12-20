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

**Solution**

<br>Developer Console | File | New | Apex Class - AnimalLocator

```
public class AnimalLocator {
    public static String getAnimalNameById(Integer x) {
        Http http = new Http();
        HttpRequest req = new HttpRequest();
        req.setEndpoint('https://th-apex-http-callout.herokuapp.com/animals/' + x);
        req.setMethod('GET');
        Map<String, Object> animal = new Map<String, Object>();
        HttpResponse res = http.send(req);
        if(res.getStatusCode() == 200) {
            Map<String, Object> results = (Map<String, Object>)JSON.deserializeUntyped(res.getBody());
            animal = (Map<String, Object>) results.get('animal');
        }
        return (String)animal.get('name');
    }
}
```

<br>File | New | Apex Class - AnimalLocatorTest

```
@isTest
private class AnimalLocatorTest {
    @isTest static void AnimalLocatorMock1() {
        try{
            Test.setMock(HttpCalloutMock.class, new AnimalLocatorMock());
            string result = AnimalLocator.getAnimalNameById(1);
            string expectedResult = 'fox';
            System.assertEquals(result, expectedResult);
        }
        catch(exception e) {
            System.debug('The following exception has occurred: ' + e.getMessage());
        }
    }
}
```

<br>File | New | Apex Class - AnimalLocatorMock

```
@isTest
global class AnimalLocatorMock implements HttpCalloutMock {
    global HTTPResponse respond(HTTPRequest request) {
        HttpResponse response = new HttpResponse();
        response.setHeader('Content-Type', 'application/json');
        response.setBody('{"animals": ["lion", "fox", "bear", "panda", "snake", "racoon"]}');
        response.setStatusCode(200);
        return response;
    }
}
```

<br> Test >
- [x] Always Run Asynchronously |  Run All | Success!
