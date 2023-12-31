<br>
<div> <h2 align=center> Control Access to the Org </h2>

<b> Create a guest administrator user and deactivate it </b><br>
Your hands-on org comes with a System Administrator user. Create a new user using the System Administrator profile, then deactivate that user to preserve the licenses in your org.

<b> Before You Start </b>
* Important: Use the new Trailhead Playground that you created for the hands-on steps and challenges in this module. Using an existing Trailhead Playground might cause problems completing the challenge.
* Visit Setup | Company Settings | Company Information | User Licenses to verify that you have one remaining Salesforce license available.
* If you already used both of your Salesforce licenses, deactivate one to complete this challenge.
<br>
<b> Challenge Requirements </b><br>

* Create a new user:
  * Profile: System Administrator
  * User License: Salesforce
  * Username: must contain guestadmin somewhere in it
  * Alias: guestadm
* The new user must be inactive

<b> Solution: </b>

Setup | Users | New User

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/e40bdbe7-8b64-4eb0-a1a7-0a2c44a808cf)

Edit | Uncheck "Active" checkbox

<br>
<h2 align=center> Control Access to Objects </h2>

<b> Create a Cleaner profile </b><br>
Your company is going through a data cleanup project, and you assigned a consultant to help you. You want the consultant to have read-only access to most objects, but have edit rights only on accounts, contacts, and leads. You don't want the consultant to delete anything or create new records.

<b> Challenge Requirements </b>
* Clone the Minimum Access - Salesforce profile with the following settings:
  * Use existing profile: Minimum Access - Salesforce
  * Profile Name: Cleaner
* Control access for the Cleaner profile:
  * Object Permissions: Accounts (Read, Edit)
  * Object Permissions: Contacts (Read, Edit)
  * Object Permissions: Leads (Read, Edit)
* Make sure Edit and Create object permissions aren't enabled for any other objects in the <b>Cleaner</b> profile.

<b> Solution: </b>

Steup | Users > Profiles | Clone > Minimum Access - Salesforce
![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/c87433cb-83fb-4262-a613-d5875587415a)

Edit | Standard Object Permissions
![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/137b3ec9-8ee8-4194-a51f-28beb6baad12)

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/b61577d8-b9e6-42ec-9afa-6685fdf9caee)

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/0d59be65-6593-4126-9bd8-6888797eca01)

<br>
<h2 align=center> Control Access to Fields </h2>

<b> Create a profile and permission set to handle field access </b>
<p> Sales team members have most of the same object and field permissions as the Standard User profile. But your company wants to make sure that sales team members don’t delete certain records, and that only senior sales members have access to certain fields.</p>
<p>For this challenge, use both profiles and permission sets to control object-level permissions. Make sure that all sales team members can create, edit, and view accounts and contacts, but NOT delete them. Then make sure that most sales members can't see or edit the Rating field on accounts, but some senior sales members can.</p>

<b> Challenge Requirements </b><br>
* Clone the Standard User profile:
  * Existing Profile: Standard User
  * Profile Name: Sales
* Control access for the Sales profile:
  * Standard Object Permissions:
    * Accounts: Read, Create, Edit
    * Contacts: Read, Create, Edit
  * Field Permissions:
    * Rating field on the Accounts object: no access
  * All other permissions from the Standard User profile remain as is
* Create a new permission set:
  * Label: Rating
  * API Name: Rating
  * User License: Salesforce
* Control access for the Rating permission set:
  * Field Permissions:
    * Rating field on the Accounts object: Read Access, Edit Access
   
<b> Solution: </b><br>
Setup | Users > Profiles | Clone > Standard User | Edit - Standard Object Permission | Make changes and "Save" <br> 
For Field Permissions, Field-Level Security | Account <View> | Edit | Uncheck Access boxes for "Rating field | Save <br>
For Permission Sets, Users > Permission Sets | New | Enter details | Save <br>

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/51a7d343-e5ff-45af-9523-bb538e31a8ce)

Object Settings | Accounts | Edit | Check the boxes of Read and Edit Access for "Rating" under Field Permissions | Save <br>

<br>
<h2 align=center> Control Access to Records </h2>

<b> Configure organization-wide defaults </b>
<p> Your company needs a custom object for tracking projects. Project records should be visible only to the owner of the record and to users above the owner in the role hierarchy. Create the Project custom object, then create an organization-wide default sharing setting for the Project object for this use case. </p>

<b> Challenge Requirements </b>
* Create a custom object:
  * Label: Project
  * Plural Label: Projects
  * Object Name: Project
  * Record Name: Project Name
  * Record Name Data Type: Text
* Configure organization-wide default sharing settings for the Project object so that Project records are visible only to the record owner.
* Also configure the sharing settings so that Project records are visible to users above them in the role hierarchy. (We won't check for this.)

<b> Solution: </b>

Setup | Object Manager | Create > Custom Object | Enter details | Save <br>
For Organisation-wide shaing settings, Home | Security > Sharing Settings | Edit | Set "Default Internal Access" of "Project" object as "Private" | Save <br>

<br>
<h2 align=center> Create a Role Hierarchy </h2>

<b> Create a role hierarchy for a reorganized team </b><br>
Following your company's sales kickoff meeting, teams have realigned. The Sales organization includes a number of new strategic positions, such as a Training Coordinator, Sales Strategy Manager, and Chief Sales Officer.
The Sales Strategy Manager reports to the Chief Sales Officer and directly supervises the Training Coordinator. The Chief Sales Officer reports directly to the CEO.

<b> Challenge Requirements </b><br>

* Create the Chief Sales Officer role:
  * Label: Chief Sales Officer
  * Role Name: Chief_Sales_Officer
  * Reports to: CEO
* Create the Sales Strategy Manager role:
  * Label: Sales Strategy Manager
  * Role Name: Sales_Strategy_Manager
  * Reports to: Chief Sales Officer
* Create the Training Coordinator role:
  * Label: Training Coordinator
  * Role Name: Training_Coordinator
  * Reports to: Sales Strategy Manager

<b> Solutions </b><br>

Setup | Home | Users > Roles | Setup Roles | Add Role under <b>CEO</b> | Enter Details | Save <br>
For Strategy Manager | Expand CEO and click on "Add Roles" under Chief Sales Officer
![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/ee5d8fd8-5d58-4820-bf2c-1a7555d46980)

Follow same for Training Coordinator. Final Tree will look like - 

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/f85c3343-92f9-44ce-98a1-535da80c4575)

<br>
<h2 align=center> Define Sharing Rules </h2>

<b> Create a sharing rule for the Project object </b>
<p> In most cases, only the record owner or users above the owner in the role hierarchy should see project records. However, the Training Coordinator needs read-only access to high-priority project records.
Create a custom picklist field on the Project object named Priority with the following values: High, Medium, and Low. Then create a criteria-based sharing rule to share high-priority records with the Training Coordinator. </p>

<b> Before You Start </b>
<p> Make sure you complete the hands-on challenges in the previous units of this module before you attempt this challenge. The work you do here builds on work you do in those units.
If you haven't created a custom field before, complete the Data Modeling module before you attempt this challenge. </p>

<b> Challenge Requirements </b>
* Create a custom field for the Project object:
  * Field Type: Picklist
  * Field Label: Priority
  * Field Name: Priority
  * Values (each value separated by a new line):
    * High
    * Medium
    * Low
   * Make the field visible to all profiles and add it to all page layouts
* Create a sharing rule for the Project object:
  * Label: choose any label you want
  * Rule Name: Share_Project_Records
  * Rule Type: Based on criteria
  * Field: Priority
  * Operator: equals
  * Value: High
  * Share with (role): Training Coordinator
  * Access level: Read Only
* Make sure the organization-wide defaults for the Project object are set to Private

<b> Solution: </b><br>

Setup | Home | Sharing Settings
![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/cbb62d13-ff92-49ee-b4ab-24a8b19a144e)

Enter given details | Save
![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/ba661f69-bd70-4623-8731-312f136bad12)

Ensure the organization-wide defaults for the Project object are set to Private
![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/634260d1-7f2e-4de1-81a9-2e06e53b7a72)
