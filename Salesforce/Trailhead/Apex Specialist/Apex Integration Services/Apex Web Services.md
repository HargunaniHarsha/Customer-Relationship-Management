<h2 align=center>Apex Web Services</h2>

**Create an Apex REST service that returns an account and its contacts.**
Create an Apex REST class that is accessible at /Accounts/<Account_ID>/contacts. The service will return the account's ID and name plus the ID and name of all contacts associated with the account. Write unit tests that achieve 100% code coverage for the class and run your Apex tests.

**Prework:** Be sure the Remote Sites from the first unit are set up.
* Create an Apex class
  * Name: AccountManager
  * Class must have a method called getAccount
  * Method must be annotated with @HttpGet and return an Account object
  * Method must return the ID and Name for the requested record and all associated contacts with their ID and Name
* Create unit tests
  * Unit tests must be in a separate Apex class called AccountManagerTest
  * Unit tests must cover all lines of code included in the AccountManager class, resulting in 100% code coverage
* Run your test class at least once (via Run All tests the Developer Console) before attempting to verify this challenge.

<br>

**Solution**

Developer Console | File | New | Apex Class
<br> 

AccountManager.apxc <br>

```
@RestResource(urlMapping = '/Accounts/*/contacts')
global with sharing class AccountManager {
    @HttpGet
    global static Account getAccount() {
        RestRequest request = RestContext.request;
        string accountId = request.requestURI.substringBetween('Accounts/', '/contacts');
        Account result = [SELECT Id, Name, (Select Id, Name From Contacts) From Account Where Id=:accountId Limit 1];
        return result;
    }
}
```

<br>

AccountManagerTest.apxc <br>

```
@IsTest
public class AccountManagerTest {
    @IsTest static void testGetContactsByAccountId(){
        Id recordId = createTestRecord();
        RestRequest request = new RestRequest();
        request.requestUri = 'https://yourInstance.my.salesforce.com/services/apexrest/Accounts/'+ recordId+'/contacts';
        request.httpMethod = 'GET';
        RestContext.request = request;
        Account thisAccount = AccountManager.getAccount();
        System.assert(thisAccount != null);
        System.assertEquals('Test record', thisAccount.Name);
    }
    static Id createTestRecord() {
        Account accountTest = new Account(Name = 'Test record');
        insert accountTest;
        
        Contact contactTest = new Contact(
        	FirstName = 'John',
        	LastName = 'Doe',
        	AccountId = accountTest.Id);
        insert contactTest;
        return accountTest.Id;
    }
}
```

<br>

Test > <br>
- [x] Always Run Asynchronously | Run All. Done!
