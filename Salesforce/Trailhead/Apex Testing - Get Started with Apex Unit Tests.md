<h3 align=center> Get Started with Apex Unit Tests </h3>

Developer Console | File> New> ApexClass | Enter Name - VerifyDate
```
public class VerifyDate {
    //method to handle potential checks against two dates
	public static Date CheckDates(Date date1, Date date2) {
		//if date2 is within the next 30 days of date1, use date2.  Otherwise use the end of the month
		if(DateWithin30Days(date1,date2)) {
			return date2;
		} else {
			return SetEndOfMonthDate(date1);
		}
	}
	
	//method to check if date2 is within the next 30 days of date1
	private static Boolean DateWithin30Days(Date date1, Date date2) {
		//check for date2 being in the past
        	if( date2 < date1) { return false; }
        
        	//check that date2 is within (>=) 30 days of date1
        	Date date30Days = date1.addDays(30); //create a date 30 days away from date1
		if( date2 >= date30Days ) { return false; }
		else { return true; }
	}

	//method to return the end of the month of a given date
	private static Date SetEndOfMonthDate(Date date1) {
		Integer totalDays = Date.daysInMonth(date1.year(), date1.month());
		Date lastDay = Date.newInstance(date1.year(), date1.month(), totalDays);
		return lastDay;
	}
}
```

<br>
Save | File> New> ApexClass | Enter Name - TestVerifyDate

```
@isTest
public class TestVerifyDate {
    static testmethod void WithinMonthCheckDates(){
        Date date1 = date.today();
        Date date2 = date.today().addDays(15);
        Date date3 = date.today().addDays(45);
        Date date4 = date.today().addDays(-10);

        Date newDate = VerifyDate.CheckDates(date1,date2);
        System.assertEquals(date2, newDate);

        Date newDate2 = VerifyDate.CheckDates(date1,date3);
        System.assertEquals(date2, newDate);

        Date newDate3 = VerifyDate.CheckDates(date1,date4);
        System.assertEquals(date2, newDate);

       }
}
```

<br>
Save | Test> NewRun | Select TestVerifyDate <br><br>

![Screenshot 2023-11-04 114943](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/41781229-a680-480b-a831-9ebb52c97373)

<br>
Click Run.
<br>
