# Survey Push API

The survey push API is a module in the survey platform that triggers at 5 minutes intervals and sends any new data over to a customer server using HTTP(S) POST with JSON data. If no new data is available, no requests will be sent.

The server side will have to respond with a HTTP 200 ok if the request was successfully received, if any HTTP error codes are returned then the request will be retried on the next trigger. 


## Property list

<table>
<tr><th>Property Name</th><th>Data Type</th><th>Description</th></tr>	
<tr><td>id</td><td>Integer</td><td>Unique integer identifier for survey</td></tr>	
<tr><td>surveyid</td><td>Integer</td><td>Manual survey id</td></tr>		
<tr><td>agentid</td><td>String</td><td>Identifier for agent</td></tr>
<tr><td>queue</td><td>String</td><td>Identifier for queue</td></tr>	
<tr><td>rating</td><td>String</td><td>Enduser's score</td></tr>
<tr><td>response</td><td>String</td><td>Enduser's reply</td></tr>
<tr><td>smsSentDate</td><td>String</td><td>Timestamp of the first SMS sent to the enduser</td>
<tr><td>team</td><td>String</td><td>Identifier for team</td></tr></tr>
<tr><td>follow_up_response</td><td>String</td><td>Enduser's follow up response</td></tr>
<tr><td>name</td><td>String</td><td>Enduser's name</td></tr>
<tr><td>address</td><td>String</td><td>Enduser's address</td></tr>
<tr><td>street</td><td>String</td><td>Enduser's street name</td></tr>
<tr><td>housenumber</td><td>String</td><td>Enduser's housenumber</td></tr>
<tr><td>entry</td><td>String</td><td>Enduser's entry</td></tr>
<tr><td>postnumber</td><td>String</td><td>Enduser's post number</td></tr>	
<tr><td>postArea</td><td>String</td><td>Enduser's post area</td></tr>
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


### Example - Push of survey data using HTTP(S) POST with JSON

	{
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
            "comment": "OK",
      		"updated": "2016-10-21T15:27:04.387+0200"      
        }
    ],
    "manualSurveyList": []
	}
