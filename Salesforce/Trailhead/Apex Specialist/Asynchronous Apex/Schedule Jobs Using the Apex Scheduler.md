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
