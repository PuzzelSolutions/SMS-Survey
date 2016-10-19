# Collect Push API

The Collect push API is a module in the Collect platform that triggers at 5 minutes intervals and sends any new data over to a customer server using HTTP(S) GET or HTTP(S) POST with JSON data. If no new data is available, no requests will be sent.

The server side will have to respond with a HTTP 200 ok if the request was successfully received, if any HTTP error codes are returned then the request will be retried on the next trigger. 

![](http://i.imgur.com/205JOAi.png)

The API is configurable from the Collect adminweb and depending on the type of activity can send two types of data:

1. Standard Collect data - Information about new donations / donators
2. Member data - Information about new members

If you have a service that is using both modes it is possible to set up multiple triggers. Please refer to the Connect user manual for more information about how to configure the API from the adminweb. 

### Definitions
<table>
<tr><th>Term</th><th>Description</th></tr>	
<tr><td>Activity</td><td>A Collect service consists of one or more activities. An activity might be a SMS service for donations, a web donation form or a SMS service for recruiting, billing and communicating with a member network.</td></tr>	
<tr><td>Donator</td><td>A user donating an amount to an activity</td></tr>	
<tr><td>Collection unit</td><td>A digital analog to a collection tin. For activities where there is for example just one keyword to donate to there will only exist one collection unit for the activity</td></tr>	
<tr><td>Collector</td><td>The person that is requesting / handles the donation for the donator. Like for collection unit there will in many cases only be a default colletor. </td></tr>	
<tr><td>Member</td><td>A user joining an activity as member. For example for recurring donations or starting a NGO membership</td></tr>	
</table>


## Standard Collect mode (Donation) - Parameter list

<table>
<tr><th>Parameter Name</th><th>Data Type</th><th>Description</th><th>Mandatory</th></tr>	
<tr><td>id</td><td>Integer</td><td>Unique integer identifier for donation</td><td>Yes</td></tr>	
<tr><td>serviceId</td><td>Integer</td><td>SMS service id</td><td>Yes</td></tr>		
<tr><td>moMessageId</td><td>String</td><td>Identifier for incoming SMS message</td><td>Yes</td></tr>
<tr><td>billingMessageId</td><td>String</td><td>Identifier for billing SMS message</td><td>No</td></tr>	
<tr><td>firstName</td><td>String</td><td>First name of the donator</td><td>No</td></tr>	
<tr><td>lastName</td><td>String</td><td>Last name of the donator</td><td>No</td></tr>	
<tr><td>address</td><td>String</td><td>Address of the donator</td><td>No</td></tr>	
<tr><td>areaCode</td><td>String</td><td>Areacode of the donator</td><td>No</td></tr>	
<tr><td>city</td><td>String</td><td>City of the donator</td><td>No</td></tr>	
<tr><td>activityId</td><td>Integer</td><td>Identifier for the activity</td><td>Yes</td></tr>	
<tr><td>activityType</td><td>String</td><td>Type of activity (collect or member)</td><td>Yes</td></tr>	
<tr><td>activityGuid</td><td>String</td><td>GUID for the activity</td><td>Yes</td></tr>	
<tr><td>activityName</td><td>String</td><td>The name of the activity</td><td>Yes</td></tr>	
<tr><td>activityInvoiceName</td><td>String</td><td>Invoice text (on the Intelecom invoice)</td><td>No</td></tr>	
<tr><td>collectionUnitId</td><td>Integer</td><td>Identifier for the collection unit</td><td>Yes</td></tr>	
<tr><td>collectionUnitGuid</td><td>String</td><td>GUID for the collection unit</td><td>Yes</td></tr>	
<tr><td>collectionUnitCode</td><td>String</td><td>Code for the collection unit</td><td>Yes</td></tr>	
<tr><td>collectorId</td><td>Integer</td><td>Id of the collector</td><td>Yes</td></tr>	
<tr><td>collectorName</td><td>String</td><td>Name of the collector</td><td>No</td></tr>	
<tr><td>collectorNumber</td><td>Integer</td><td>Number of the donator</td><td>No</td></tr>	
<tr><td>msisdn</td><td>String</td><td>Mobile phone number of the donator</td><td>Yes</td></tr>	
<tr><td>orderId</td><td>Integer</td><td>Order identifier</td><td>Yes</td></tr>	
<tr><td>orderDate</td><td>Date</td><td>The data the order was processed</td><td>Yes</td></tr>	
<tr><td>price</td><td>Integer</td><td>Price of the billing message</td><td>Yes</td></tr>	
<tr><td>isDelivered</td><td>Boolean</td><td>True if the billing message was delivered</td><td>Yes</td></tr>	
<tr><td>isProcessed</td><td>Boolean</td><td>True if the order has been processed</td><td>Yes</td></tr>	
<tr><td>moKeyword</td><td>String</td><td>Keyword used when sending the donation SMS</td><td>Yes</td></tr>	
</table>


### Example Request - Push of donation data using HTTP(S) GET

	http://customer.server-url.com?id=256213&serviceId=1131&moMessageId=7a07w0002e00&billingMessageId=7a02g1fm7300&firstName=Intelecom++AS&lastName=Group&address=Brynsveien+13&areaCode=0667&city=Oslo&activityId=492&activityType=CollectActivity&activityGuid=07113B9A-7238-4A65-AD56-543DAD01470B&activityName=Test+innsamling&activityInvoiceName=Test+innsamling&collectionUnitId=4250&collectionUnitGuid=70DD51D3-960A-4A97-BBA5-B7DEAA6BF472&collectionUnitCode=23&collectorId=34&collectorName=Test&collectorNumber=234&msisdn=%2B4799999999&orderId=254265&orderDate=2016-02-04+09%3A27%3A28.653&price=100&isDelivered=true&isProcessed=false&moKeyword=grmkunst

### Example - Push of donation data using HTTP(S) POST with JSON

	[{
		"id": 256213,
		"serviceId": 2731,
		"moMessageId": "7f07m0001s00",
		"moMessageContent": "test",
		"moKeyword": "grmkunst",
		"billingMessageId": "7v02g1hm7s00",
		"firstName": "Intelecom",
		"lastName": "Group AS",
		"address": "Brynsveien13",
		"areaCode": "0667",
		"city": "Oslo",
		"activityId": 492,
		"activityType": "CollectActivity",
		"activityGuid": "07223B9A-7738-4B65-AD56-543DAD01470B",
		"activityName": "Test innsamling",
		"activityInvoiceName": "Test innsamling",
		"collectionUnitId": 4250,
		"collectionUnitGuid": "70EE51D3-960A-4C97-BBA5-B7DEAA6BF472",
		"collectionUnitCode": "12",
		"collectorId": 34,
		"collectorName": "Bjarne",
		"collectorNumber": 23,
		"msisdn": "+4799999999",
		"orderId": "254265",
		"orderDate": "2016-02-04 09:27:28.653",
		"price": 100,
		"isDelivered": true,
		"isDone": true,
		"isProcessed": false,
		"isSendtToCustomer": false
	}]

## Member mode - Parameter list


<table>
<tr><th>Parameter Name</th><th>Data Type</th><th>Description</th><th>Mandatory</th></tr>	
<tr><td>memberId</td><td>Integer</td><td>Unique integer identifier for member</td><td>Yes</td></tr>	
<tr><td>activityId</td><td>Integer</td><td>Identifier for the activity</td><td>Yes</td></tr>
<tr><td>serviceId</td><td>Integer</td><td>SMS service id</td><td>Yes</td></tr>		
<tr><td>msisdn</td><td>String</td><td>Members mobile phone number</td><td>No</td></tr>	
<tr><td>firstName</td><td>String</td><td>First name of the member</td><td>No</td></tr>	
<tr><td>lastName</td><td>String</td><td>Last name of the member</td><td>No</td></tr>	
<tr><td>address</td><td>String</td><td>Address of the member</td><td>No</td></tr>	
<tr><td>postCode</td><td>String</td><td>Areacode of the member</td><td>No</td></tr>	
<tr><td>town</td><td>String</td><td>City of the member</td><td>No</td></tr>	
<tr><td>email</td><td>String</td><td>Members email address</td><td>No</td></tr>	
<tr><td>guuid</td><td>String</td><td>GUID for the member</td><td>Yes</td></tr>	
<tr><td>moMessageId</td><td>String</td><td>Identifier for incoming SMS message</td><td>Yes</td></tr>
<tr><td>memberStatus</td><td>String</td><td>active -> Active Member </br> pending -> Pending confirmation</br>inactive -> Inactive Member</td><td>Yes</td></tr>	
</table>


### Example Request - Push of member data using HTTP(S) GET

http://customer.server-url.com/collect?memberId=5856&activityId=451&serviceId=1111&msisdn=+4799999999&firstname=Ola&lastname=Nordmann&address=Kirkegaten+30&postcode=4878&town=Grimstad&email=demo@test.com&guuid=1554A144-6DFD-2277-5231-F54151232BF9&moMessageId=1a04e02ibw0&memberStatus=active

### Example Request - Push of member data using HTTP(S) POST with JSON

	Content-Type: application/json

	[{
	"memberId": 3830,
	"activityId": 434,
	"serviceId": 2731,
	"msisdn": "+4799999997",
	"guuid": "B6146BA6-0CBC-4174-B253-7BF0C532D477",
	"moMessageId": "7e07a001ae00",
	"memberStatus": "active"
	},
	{
	"memberId": 5853,
	"activityId": 451,
	"serviceId": 2731,
	"msisdn": "+4799999998",
	"firstname": "Ben",
	"lastname": "Harper",
	"address": "Kirkegaten 11",
	"postcode": "4878",
	"town": "Grimstad",
	"email": "ben.harper@test.com",
	"guuid": "7EAF6sD2-6110-4121-ABFB-191424CD17E7",
	"moMessageId": "7g01o02eaa00",
	"memberStatus": "active"
	},
	{
	"memberId": 5856,
	"activityId": 451,
	"serviceId": 2731,
	"msisdn": "+4799999999",
	"firstname": "Geir",
	"lastname": "Hansen",
	"address": "Grillgaten 30A",
	"postcode": "0611",
	"town": "Oslo",
	"guuid": "1554A141-6AFD-4C73-8231-F54159211BF9",
	"moMessageId": "7h04b02ibu00",
	"memberStatus": "active"
	}]

## Implementing the server side

