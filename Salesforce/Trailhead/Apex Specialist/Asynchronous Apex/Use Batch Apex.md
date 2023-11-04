<h3 align=center> Use Batch Apex </h3>

**Create an Apex class that uses Batch Apex to update Lead records.**

<p>Create an Apex class that implements the Database.Batchable interface to update all Lead records in the org with a specific LeadSource.</p>

* Create an Apex class:
  * Name: LeadProcessor
  * Interface: Database.Batchable
  * Use a QueryLocator in the start method to collect all Lead records in the org
  * The execute method must update all Lead records in the org with the LeadSource value of Dreamforce
* Create an Apex test class:
  * Name: LeadProcessorTest
  * In the test class, insert 200 Lead records, execute the LeadProcessor Batch class and test that all Lead records were updated correctly
  * The unit tests must cover all lines of code included in the LeadProcessor class, resulting in 100% code coverage
  * Before verifying this challenge, run your test class at least once using the Developer Console Run All feature

<br>
Solution - <br>
LeadProcessor.apxc

```
global class LeadProcessor implements Database.Batchable<sObject> {
    global Integer count = 0;
    global Database.QueryLocator start(Database.BatchableContext bc) {
        return Database.getQueryLocator('Select Id, LeadSource From Lead');
    }
    global void execute (Database.BatchableContext bc, List<Lead> LeadList) {
        List<Lead> newLeadList = new List<Lead>();
        for(Lead l: LeadList) {
            l.LeadSource = 'Dreamforce';
            newLeadList.add(l);
            count += 1;
        }
        update newLeadList;
    }
    global void finish(Database.BatchableContext bc) {
        system.debug('count = ' + count);
    }
}
```

<br>
LeadProcessorTest.apxc

```
@isTest
public class LeadProcessorTest {
    @isTest
    public static void testit() {
        List<Lead> leadList = new List<Lead>();
        for(Integer i=0 ; i<200 ; i++) {
            Lead L = new Lead();
            L.LastName = 'Name'+i;
            L.Company = 'Company';
            L.Status = 'Random Status';
            leadList.add(L);
        }
        insert leadList;
        
        Test.startTest();
        LeadProcessor lp = new LeadProcessor();
        Id batchId = Database.executeBatch(lp);
        Test.stopTest();
    }
}
```

Run Test
<br>
