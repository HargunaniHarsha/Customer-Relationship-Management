Create an Apex trigger for Account that matches Shipping Address Postal Code with Billing Address Postal Code based on a custom field.
For this challenge, you need to
* create a trigger - 'AccountAddressTrigger'
* before insert or update
* Condition : If Match Billing Address is true
* Set : the Shipping Postal Code (whose API name is ShippingPostalCode) to be the same as the Billing Postal Code (BillingPostalCode).

The Account object will need a new custom checkbox that should have the Field Label 'Match Billing Address' and Field Name of 'Match_Billing_Address'. The resulting API Name should be 'Match_Billing_Address__c'.
With 'AccountAddressTrigger' active, if an Account has a Billing Postal Code and 'Match_Billing_Address__c' is true, the record should have the Shipping Postal Code set to match on insert or update.


<B>Code</B>

```
trigger AccountAddressTrigger on Account (before insert, before update) {
    for(Account a: trigger.New){
        if(a.Match_Billing_Address__c == true) {
            a.ShippingPostalCode=a.BillingPostalCode;
        }
    }
}
```
