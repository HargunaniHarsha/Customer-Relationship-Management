<h2 align=center> Control Processes with Queueable Apex </h2>
<br>
<b>Create a Queueable Apex class that inserts Contacts for Accounts.</b><br>

Create a Queueable Apex class that inserts the same Contact for each Account for a specific state. <br>
* Create an Apex class:
  * Name: AddPrimaryContact
  * Interface: Queueable
  * Create a constructor for the class that accepts as its first argument a Contact sObject and a second argument as a string for the State abbreviation
  * The *execute* method must query for a maximum of 200 Accounts with the BillingState specified by the State abbreviation passed into the constructor and insert the Contact sObject record associated to each Account. Look at the sObject clone() method.
* Create an Apex test class:
  * Name: AddPrimaryContactTest
  * In the test class, insert 50 Account records for BillingState NY and 50 Account records for BillingState CA
  * Create an instance of the AddPrimaryContact class, enqueue the job, and assert that a Contact record was inserted for each of the 50 Accounts with the BillingState of CA
  * The unit tests must cover all lines of code included in the AddPrimaryContact class, resulting in 100% code coverage
* Before verifying this challenge, run your test class at least once using the Developer Console Run All feature

<br>
<h3> Solution </h3>

Developer Console | File | New | Apex Class | Name - AddPrimaryContact <br>

```
public class AddPrimaryContact implements Queueable {
    private Contact con;
    private String state;
    
    public AddPrimaryContact(Contact cont, String statestr) {
        this.con = cont;
        this.state = statestr;
    }
    
    public void execute (QueueableContext context) {
        List<Account> accounts = [Select Id, Name,
                                 (Select FirstName, LastName, Id from contacts)
                                 from Account where BillingState = :state
                                 Limit 200];
        List<Contact> primaryContacts = new List<Contact>();
        
        for(Account acc: accounts) {
            Contact c = con.clone();
            c.AccountId = acc.Id;
            primaryContacts.add(c);
        }
        
        if(primaryContacts.size() > 0) {
            insert primaryContacts;
        }
    }
}
```

<br> New | Apex Class | Name - AddPrimaryContactTest <br>
```
@isTest
public class AddPrimaryContactTest {
    static testmethod void testQueueable() {
        List<ACcount> testAccounts = new List<Account>();
        for(Integer i=0 ; i<50 ; i++) {
            testAccounts.add(new Account(Name='Account'+i, BillingState='CA'));
        }
        for(Integer j=0 ; j<50 ; j++) {
            testAccounts.add(new Account(Name='Account'+j, BillingState='NY'));
        }
        insert testAccounts;
        
        Contact testContact = new Contact(FirstName = 'John', LastName = 'Doe');
        insert testContact;
        
        AddPrimaryContact addit = new addPrimaryContact(testContact, 'CA');
        
        Test.startTest();
        system.enqueueJob(addit);
        Test.stopTest();
        
        System.assertEquals(50, [Select count() from Contact Where accountId in 
                                 (Select Id from Account where BillingState='CA')]);
    }
}
```

<br> Click on "Run all tests" button. Done! <br>
