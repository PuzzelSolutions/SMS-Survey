# Survey REST API

The Survey REST API lets you retrieve Survey data.
This section describes how to integrate towards the Survey REST API.  

# How to connect

The API uses [Auth0](https://auth0.com/) for authentication and you will need to set up an [account](Authentication.md)

### Definitions
<table>
<tr><th>Description</th><th>Value</th></tr>	
<tr><td>Method</td><td>GET</td></tr>	
<tr><td>URL</td><td>https://{survey-host}/survey/rs/service/serviceId?from={}
<br/><p><i>Please contact Intelcom Support for the correct {survey-host}.</p></td></tr>
<tr><td>serviceId</td><td>The id of your service</td></tr>	
<tr><td>from</td><td>Timestamp (format: YYYY-MM-DDTHH:MM:SS.SSSZ) </td></tr>	
</table>

### Request Example
https://{survey-host}/survey/rs/service/35?from=2016-05-08T00:00:00.000%2B0200 

## Property list

<table>
<tr><th>Property Name</th><th>Data Type</th><th>Description</th></tr>	
<tr><td>id</td><td>Integer</td><td>Unique integer identifier for Survey</td></tr>	
<tr><td>Surveyid</td><td>Integer</td><td>Manual Survey id</td></tr>		
<tr><td>agentid</td><td>String</td><td>Identifier for agent</td></tr>
<tr><td>queue</td><td>String</td><td>Identifier for queue</td></tr>	
<tr><td>rating</td><td>String</td><td>End user's score</td></tr>
<tr><td>response</td><td>String</td><td>End user's reply</td></tr>
<tr><td>smsSentDate</td><td>String</td><td>Timestamp of the first SMS sent to the enduser</td>
<tr><td>team</td><td>String</td><td>Identifier for team</td></tr></tr>
<tr><td>follow_up_response</td><td>String</td><td>End user's follow up response</td></tr>
<tr><td>name</td><td>String</td><td>End user's name</td></tr>
<tr><td>address</td><td>String</td><td>End user's address</td></tr>
<tr><td>street</td><td>String</td><td>End user's street name</td></tr>
<tr><td>housenumber</td><td>String</td><td>End user's housenumber</td></tr>
<tr><td>entry</td><td>String</td><td>End user's entry</td></tr>
<tr><td>postnumber</td><td>String</td><td>End user's post number</td></tr>	
<tr><td>postArea</td><td>String</td><td>End user's post area</td></tr>
<tr><td>extraParamName1</td><td>String</td><td>1. extra parameter name</td></tr>
<tr><td>extraParamName2</td><td>String</td><td>2. extra parameter name</td></tr>
<tr><td>extraParamName3</td><td>String</td><td>3. extra parameter name</td></tr>
<tr><td>extraParamName4</td><td>String</td><td>4. extra parameter name</td></tr>
<tr><td>extraParamName5</td><td>String</td><td>5. extra parameter name</td></tr>
<tr><td>extraParamValue1</td><td>String</td><td>1. extra value</td></tr>
<tr><td>extraParamValue2</td><td>String</td><td>2. extra value</td></tr>
<tr><td>extraParamValue3</td><td>String</td><td>3. extra value</td></tr>
<tr><td>extraParamValue4</td><td>String</td><td>4. extra value</td></tr>
<tr><td>extraParamValue5</td><td>String</td><td>5. extra value</td></tr>
<tr><td>comment</td><td>String</td><td>Your comment</td>
<tr><td>updated</td><td>String</td><td>Last modified</td>
</table>


### JSON Response Example

	{
		"timestamp": "2016-11-22T09:46:46.040+0100",
		"callcenterSurveyList": [
    		{
				"id": 4483,
		      	"surveyid": 0,
		      	"msisdn": "+4712345678",
		      	"agentid": "agent1",
		      	"queue": "queue1",
		      	"rating": "8",
		      	"response": "5 abc",
		      	"smsSentDate": "2016-10-21T15:23:43.423+0200",
		      	"team": "team1",
		      	"follow_up_response": null,
		      	"name": "Minh Do Le",
		      	"address": "Brynsveien 13 ; 0667 Oslo",
				"street": "Brynsveien",
		      	"housenumber": "13",
				"entry": null,
		      	"postnumber": "0667",
		      	"postArea": "Oslo",
		      	"extraParamName1": "waitingTime",
		      	"extraParamName2": "callDuration",
		      	"extraParamName3": null,
		      	"extraParamName4": null,
		      	"extraParamName5": null,
		      	"extraParamValue1": "01:12:50",
		      	"extraParamValue2": "01:12:50",
		      	"extraParamValue3": null,
		      	"extraParamValue4": null,
		      	"extraParamValue5": null,
		      	"comment": null,
		      	"updated": "2016-10-21T15:27:04.387+0200"      
			}
	  	],
		"manualSurveyList": []
	}

