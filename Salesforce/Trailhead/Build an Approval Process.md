<h2 align=center> Create an approval process </h2>
<p> Create an approval process to ensure that prospect accounts with more than 500 employees are approved before they’re converted to customers </p>

<b> Before You Start </b>
<p> Go to Object Manager. In Fields and Relationships for the Account object, check the Type field’s picklist values for Prospect, Customer, and Pending. Add any of these values that are missing. </p>

<i> Use the Jump Start Wizard to create an approval process: </i>
* Manage Approval Processes For: Account
* Name: Approve New Account
* Unique Name: Approve_New_Account
* Approval Assignment Email Template: choose any template
* Entry Criteria:
  * Account: Type equals Prospect
  * Account: Employees is greater than 500
* Approver:
  * Automatically assign to approver(s)
  * User: assign yourself
* Add an initial submission action that updates fields:
  * Name: Account Type To Pending (we won’t check for this)
  * Unique Name: Account_Type_To_Pending (we won’t check for this)
  * Action: Update the Type field to Pending
* Add a final approval action that updates fields:
  * Name: Account Type To Customer (we won’t check for this)
  * Unique Name: Account_Type_To_Customer (we won’t check for this)
  * Action: Update the Type field to Customer
* Edit the existing final approval action:
  * Name: Record Lock
  * Unique Name: Record_Lock
  * Action: Unlock the record for editing
* Add a final rejection action that updates fields:
  * Name: Account Type To Prospect (we won’t check for this)
  * Unique Name: Account_Type_To_Prospect (we won’t check for this)
  * Action: Update the Type field to Prospect
* Activate the approval process

<br>
<b> Soultion </b> <br>

Setup | Home | Approval Process | Manage Approval Processes For: Account | Create New Approval Process | Use Jump Start Wizard | Enter Details | Save
![Screenshot 2023-10-05 213208](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/927ed0fe-4018-44e6-acd4-b1c6197177ce)

Scroll down to <i>Initial Submission Actions</i> | Add New | Field Update | Enter Details | Save
![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/60278c63-d691-4a6a-9f87-308bd99bb8d0)

<i>Initial Submission Actions</i> | Add Existing | Search - Field Update | Select the Action and click rigth arrow below "Add"
![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/99d9e96c-3cde-49ce-a1fd-2f86c0281a90)

Follow Similar Steps for <i>Final Approval Actions</i>

Click on "Activate" | Ok
![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/b158c422-3e77-4a62-a0c3-05edbef3648e)

