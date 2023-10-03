<br>
<h2 align=center> Get to Know Lightning Reports and Dashboards </h2>

Q1. What is a dashboard?<br>
A. a visual display of key metrics and trends for records in your org

Q2. What does a report type determine?<br>
A. Which fields and records are available for use when creating a report


<br>
<h2 align=center> Create Reports with the Report Builder </h2>

<b> Create a Report to Show Leads </b><br>
Remember to create a new Trailhead Playground for the hands-on steps and challenges in this module.
CEO Sita Nagappan-Alvarez wants to get a better handle on where the company’s leads are coming from. Create a report for Sita that includes the lead’s state or province.
* Start a new report:
  * Report type: Leads
* Standard filter:
  * Click the All Time link if you don’t see any data in the report preview (We won’t check for this)
* Include these fields:
  * State/Province
  * Lead Source
* Save the report.
  * Report name: Lead Source Report

<b> Solution: </b>

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/ea02b9c2-cb64-4cc0-9648-5adcc02fbe6d)

<br>
<h2 align=center> Filter Your Report </h2>

<b> Create a Report with Filter Logic </b><br>
Help Erin fine-tune her opportunity report to show all the open opportunities with Amount greater than $100,000 or Probability greater than 50%.
* Create an Opportunities report.
* Set the following standard filter:
  * Date: Close Date
  * Range: All Time
* Verify that the following fields are included:
  * Amount
  * Probability
  * Stage
* Set up the following filters in this order:
  * Amount: Greater than 100,000
  * Probability: Greater than 50
  * Stage: Contains Closed
* Add the following filter logic:
  * (1 OR 2) AND NOT 3
* Save the report.
  * Report name: Opportunities to Work
 
<b> Solution: </b>

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/f5340818-ccfe-4f14-9002-fe6e1b90afed)

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/a7d6753e-ffa0-403c-8abe-dc9138eb85b2)

<b> Output: </b>

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/18dc0090-0167-4e7b-9fa3-af23f6f89180)

<br>
<h2 align=center> Format Your Report </h2>

<b> Create a report to show cases </b><br>
Roberto Alvarez, Ursa Major Solar's COO, has asked for a report of the company's customer service cases. He wants the report formatted so he can see at a glance which cases are new and which are closed. Create a summary report of cases for Roberto.
* Report type: Cases
* Standard filter:
  * Date: Opened Date
  * Range: All Time
* Fields:
  * Case Owner
  * Subject
  * Account Name
* Group: Status
* Report name: Case Status

<b> Solution: </b>

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/e23391b4-04d2-471f-837a-e482baed1623)

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/34508c1e-e36e-48c7-8009-bd389675164d)

<br>
<h2 align=center> Visualize Your Data with the Lightning Dashboard Builder </h2>

<b> Create an Opportunities Report and Add It to a Dashboard </b><br>
Lincoln Ulrich, the top salesperson at Ursa Major Solar, wants a dashboard that shows all the company’s deals. He wants to see quickly how many opportunities his team has at each stage of the pipeline. Create the underlying opportunities report, then create a dashboard. Add a component that displays the report as a donut chart on the dashboard.
* Create a report:
  * Type: Opportunities
  * Standard Filter:
    * Date: Close Date
    * Range: All Time
   * Fields:
     * Opportunity Name
     * Opportunity Owner
   * Group: Stage
   * Report name: Opportunity Stages
* Create a dashboard:
  * Name: Big Deals
  * Add a component:
    * Report: Opportunity Stages
    * Title: Opportunity Stages
    * Display As: Donut Chart
  * Save the dashboard
 
<b> Solution </b>

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/2054eaff-fc38-460a-a119-e3a2552b596d)

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/8062cd69-8704-4b7f-ab5c-2470a9ffb87a)


<br>
