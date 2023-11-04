<h3 align=center> Test Apex Triggers </h3>

<p>Create and install a simple Apex trigger which blocks inserts and updates to any contact with a last name of 'INVALIDNAME'. You'll copy the code for the class from GitHub. Then write unit tests that achieve 100% code coverage.</p>

Solution - <br>
Developer Console | File | New | Apex Trigger <br>
Trigger Name - RestrictContactByName <br>
sObject - Contact <br>

```
trigger RestrictContactByName on Contact (before insert, before update) {
	
	//check contacts prior to insert or update for invalid data
	For (Contact c : Trigger.New) {
		if(c.LastName == 'INVALIDNAME') {	//invalidname is invalid
			c.AddError('The Last Name "'+c.LastName+'" is not allowed for DML');
		}

	}

}
```

Save <br>
Developer Console | File | New | Apex Class <br>
ApexClass Name - TestRestrictContactByName <br>
```
@isTest
public class TestRestrictContactByName {
    @isTest static void Test_insertupdateContact(){
        Contact c = new Contact();
        c.LastName='INVALIDNAME';
        
        Test.startTest();
        Database.SaveResult result = Database.insert(c, false);
        Test.stopTest();
        
        System.assert(!result.isSuccess());
        System.assert(result.getErrors().size() > 0);
        System.assertEquals('The Last Name "INVALIDNAME" is not allowed for DML', result.getErrors()[0].getMessage());
    }
}
```

Save <br>
Test | New Run | Select the test class and run. <br>

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/31d20719-b0bd-479f-aa7f-d0b394f84711)

<br>
