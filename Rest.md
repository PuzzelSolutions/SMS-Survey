# Survey REST API

The Survey REST API lets you retrieve survey data.
This section describes how to integrate towards the survey REST API.  


# How to connect

The API uses [Auth0](https://auth0.com/) for authentication and you will need to set up an [account](Authentication.md)

### Definitions
<table>
<tr><th>Description</th><th>Value</th></tr>	
<tr><td>Method</td><td>GET</td></tr>	
<tr><td>URL</td><td>https://server-url/survey/ws/service/serviceId?surveytype={int}&from={}</td></tr>
<tr><td>serviceId</td><td>The id of your service</td></tr>	
<tr><td>surveytype</td><td>Callcenter solution=1, Manual survey solution=2, both solutions=3</td></tr>	
<tr><td>from</td><td>Timestamp (format: YYYY-MM-DDTHH:MM:SS.SSS) </td></tr>	
</table>


### Request Example
https://<server-url>/survey/ws/service/35?surveytype=1&from=2016-05-08T00:00:00.000 

### JSON Response Example

	{
		"timestamp": "2016-10-14T10:52:44.564",
		"callcenterSurveyList": [
    		{
				"id": 4483,
		      	"surveyid": 0,
		      	"msisdn": "+4712345678",
		      	"agentid": "agent1",
		      	"queue": "queue1",
		      	"rating": "8",
		      	"response": "5 abc",
		      	"smsSentDate": "2016-10-06T14:39:32.603",
		      	"team": "team1",
		      	"follow_up_response": null,
		      	"name": "Minh Do Le",
		      	"address": "address",
		      	"postArea": null,
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
		      	"processed": false,
		      	"updated": "2016-10-06T15:03:00.293"      
			}
	  	],
		"manualSurveyList": []
	}

