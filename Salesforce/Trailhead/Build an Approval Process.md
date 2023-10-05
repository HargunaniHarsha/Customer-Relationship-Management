<b> Create an approval process </b>
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

<b> Soultion </b> <br>

