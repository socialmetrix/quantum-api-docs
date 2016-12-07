##fb.Activity Count by Weekday  
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/activity/count/weekday/hour?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/activity/count/weekday/hour",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "182162001806727"
         ],
         "since":"2016-11-04",
         "until":"2016-12-03"
      }
   },
   "results":[  
      {  
         "id":"182162001806727",
         "data":[  
            [  
               {  
                  "posts":6,
                  "comments":0,
                  "total":6
               },
               {  
                  "posts":4,
                  "comments":0,
                  "total":4
               },
               {  
                  "posts":7,
                  "comments":0,
                  "total":7
               },
               {  
                  "posts":3,
                  "comments":0,
                  "total":3
               }
            ]
         ]
      }
   ]
}
```

This endpoint returns information about the number of posts and comments made by a Facebook page, grouped by weekday in a selected period. 

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/activity/count/weekday/hour`

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

The `results` is array of objects, it contains an `id` field which identifies the **profile id** and the `data` array contains an array with each element representing a weekday and containing the number of posts and comments made by a page during the selected period. If you select a month, it will be the previous month, if select you select 15 days *(Jun/16 ~ Jun/30)*, it will be the previous 15 days *(Jun/01 ~ Jun/15)*. 

Field | Description | Example
--------- | ----------- | -----------
**posts** | Sum of **posts**  in the selected period. | 4
**comments** | Sum of **comments** over posts in the selected period. | 0
**total** | Sum of **shares** over posts in the selected period. | 4
