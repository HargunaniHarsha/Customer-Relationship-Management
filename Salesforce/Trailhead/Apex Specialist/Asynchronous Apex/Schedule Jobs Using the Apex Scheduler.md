<h2 align=center>Schedule Jobs Using the Apex Scheduler</h2>

<b>Create an Apex class that uses Scheduled Apex to update Lead records.</b><br>

Create an Apex class that implements the Schedulable interface to update Lead records with a specific LeadSource. (This is very similar to what you did for Batch Apex.)
* Create an Apex class:
  * Name: *DailyLeadProcessor*
  * Interface: Schedulable
  * The execute method must find the first 200 Lead records with a blank LeadSource field and update them with the LeadSource value of Dreamforce
* Create an Apex test class:
  * Name: *DailyLeadProcessorTest*
  * In the test class, insert 200 Lead records, schedule the DailyLeadProcessor class to run and test that all Lead records were updated correctly
  * The unit tests must cover all lines of code included in the **DailyLeadProcessor class**, resulting in 100% code coverage.
* Before verifying this challenge, run your test class at least once using the Developer Console Run All feature.

<h3>Solution</h3>

Developer Console | File | New | Apex Class - DailyLeadProcessor <br>

```
public class DailyLeadProcessor implements schedulable{
    public void execute(schedulableContext sc) {
        List<lead> l_lst_new = new List<lead>();
        List<lead> l_lst = new List<lead>([select id, leadsource from lead where leadsource = null]);
        for(lead l : l_lst) {
            l.leadsource = 'Dreamforce';
            l_lst_new.add(l);
        }
        update l_lst_new;
    }
}
```

<br> New | Apex Class - DailyLeadProcessorTest <br>

```
@isTest
public class DailyLeadProcessorTest {
    @testSetup
    static void setup(){
        List<Lead> lstOfLead = new List<Lead>();
        for(Integer i = 1; i <= 200; i++){
            Lead ld = new Lead(Company = 'Comp' + i ,LastName = 'LN'+i, Status = 'Working - Contacted');
            lstOfLead.add(ld);
        }
        Insert lstOfLead;
    }
    static testmethod void testDailyLeadProcessorScheduledJob(){
        String sch = '0 5 12 * * ?';
        Test.startTest();
        String jobId = System.schedule('ScheduledApexTest', sch, new DailyLeadProcessor());
        
        List<Lead> lstOfLead = [SELECT Id FROM Lead WHERE LeadSource = null LIMIT 200];
        System.assertEquals(200, lstOfLead.size());

        Test.stopTest();
    }
}
```

<br> Click on "Run all tests". Done! <br>
