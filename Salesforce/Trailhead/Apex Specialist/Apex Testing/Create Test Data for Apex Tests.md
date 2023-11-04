<h3 align=center> Create Test Data for Apex Tests </h3>

**Create a Contact Test Factory**
<p>Create an Apex class that returns a list of contacts based on two incoming parameters: the number of contacts to generate and the last name. Do not insert the generated contact records into the database.</p>

<p>NOTE: For the purposes of verifying this hands-on challenge, don't specify the @isTest annotation for either the class or the method, even though it's usually required.</p>

* Create an Apex class in the public scope
  * Name: RandomContactFactory (without the @isTest annotation)
* Use a Public Static Method to consistently generate contacts with unique first names based on the iterated number in the format Test 1, Test 2 and so on.
  * Method Name: generateRandomContacts (without the @isTest annotation)
  * Parameter 1: An integer that controls the number of contacts being generated with unique first names
  * Parameter 2: A string containing the last name of the contacts
  * Return Type: List < Contact >
<br>

Solution - <br>
Developer Console | File | New Apex Class
```
public class RandomContactFactory {
    public static List<Contact> generateRandomContacts(Integer count, String lastName) {
        List<Contact> Contacts = new List<Contact>();
        for(Integer i=0 ; i<count ; i++) {
            Contact con = new Contact(FirstName='Test '+i, LastName = lastName);
            Contacts.add(con);
        }
        return Contacts;
    }
}
```

<br>
