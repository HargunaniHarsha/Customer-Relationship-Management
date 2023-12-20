<h2 align=center>Apex SOAP Callouts</h2>

**Generate an Apex class using WSDL2Apex and write a test class.**
Generate an Apex class using WSDL2Apex for a SOAP web service, write unit tests that achieve 100% code coverage for the class using a mock response, and run your Apex tests.

**Prework**: Be sure the Remote Sites from the first unit are set up.
* Generate a class using this using this WSDL file:
  * Name: ParkService (Tip: After you click the Parse WSDL button, change the Apex class name from parksServices to ParkService)
  * Class must be in public scope
* Create a class:
  * Name: ParkLocator
  * Class must have a country method that uses the ParkService class
  * Method must return an array of available park names for a particular country passed to the web service (such as Germany, India, Japan, and United States)
* Create a test class:
  * Name: ParkLocatorTest
  * Test class uses a mock class called ParkServiceMock to mock the callout response
* Create unit tests:
  * Unit tests must cover all lines of code included in the ParkLocator class, resulting in 100% code coverage.
  * Run your test class at least once (via Run All tests the Developer Console) before attempting to verify this challenge.
 
**Solution**
<br>
1. Download WSDL file and rename as _parkServices_
2. Setup | QuickFind Box - Apex Class | Generate from WSDL
3. Choose File - upload _parkServices.xml_ file and click "parse xml".
4. Give Apex Class Name - **ParkService**.
5. Developer Console | File | New | Apex Class

<br>
ParkLocator.apxc <br>

```
public class ParkLocator {
    public static string[] country(string theCountry) {
        ParkService.ParksImplPort parkSvc = new ParkService.ParksImplPort();
        return parkSvc.byCountry(theCountry);
    }
}
```

<br>
ParkServiceMock.apxc <br>

```
@isTest
global class ParkServiceMock implements WebServiceMock {
    global void doInvoke(
        Object stub,
        Object request,
        Map<String, Object> response,
        String endpoint,
        String soapAction,
        String requestName,
        String responseNS,
        String responseNam,
        String responseType
    ){
        ParkService.byCountryResponse response_x = new ParkService.byCountryResponse();
        response_x.return_x = new List<String>{'Yellowstone', 'Mackinac National Park', 'Yosemite'};
            response.put('response_x', response_x);
    }
}
```

<br>
ParkLocator.apxc <br>

```
@isTest
public class ParkLocatorTest {
    @isTest static void testCallout() {
        Test.setMock(WebServiceMock.class, new ParkServiceMock());
        String country = 'United States';
        List<String> result = ParkLocator.country(country);
        List<String> parks = new List<String>{'Yellowstone', 'Mackinac National Park', 'Yosemite'};
        System.assertEquals(parks, result);
    }
}
```

Test >
- [x] Always Run Asynchronously | Run All.
Done!
