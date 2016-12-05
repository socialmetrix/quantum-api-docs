##Campaigns stat summary
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/campaigns/stat-summary?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/campaigns/stat-summary",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "1019"
         ],
         "since":"2016-11-04",
         "until":"2016-12-03"
      }
   },
   "results":[  
      {  
         "id":"1019",
         "data":{  
            "current":{  
               "newContents":0,
               "newInteractions":0,
               "investment":0
            },
            "previous":{  
               "newContents":0,
               "newInteractions":0,
               "investment":0
            },
            "lifetime":null
         }
      }
   ]
}
```

This endpoint returns information about the new contents, new interactions and investment of each campaign created by a profile during a selected time period. You can also compare the current period with the previous one.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/campaigns/stat-summary`

### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT** | The ID obtained from JWT response: `user.accountId` | 790
**PROJECT** | Current Project | 0

### Query Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ids** | A comma-separated list of profiles ids belonging to the project | 15087023444,182162001806727
**since** | Starting date (inclusive) | 2016-09-09
**until** | Ending date (exclusive) | 2016-10-08
***timezone*** | (Optional): Time-zone that my metrics should be calculated | America/Argentina/Buenos_Aires

### Response

The `results` is array of objects, it contains an `id` field which identifies the **profile id** and the `data` array contains an array with each element representing a campaign, and within each element you can check the number of new contents and new interactions, alongside with the investment. You can also compare the numbers with the previous time period. If you select a month, it will be the previous month, if select you select 15 days *(Jun/16 ~ Jun/30)*, it will be the previous 15 days *(Jun/01 ~ Jun/15)*. 
 

Field | Description | Example
--------- | ----------- | -----------
**newContents** | The number of new **contents**, such as statuses or videos. | 1
**newInteractions** | The number of new **interactions**, such as likes or comments. | 1
**investment** | The total amount of money you have spent on boosting the posts assigned to the campaign that were created in the selected time period. | 0
