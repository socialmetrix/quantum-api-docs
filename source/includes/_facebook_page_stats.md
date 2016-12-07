##fb.Page Stats
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/profiles/interactions/count/date?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/profiles/interactions/count/date",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "182162001806727"
         ],
         "since":"2016-11-04",
         "until":"2016-12-03"
      },
      "period":{  
         "id":"1d",
         "duration":86400
      }
   },
   "results":[  
      {  
         "id":"182162001806727",
         "data":[  
            {  
               "likes":7643,
               "comments":158,
               "shares":1058,
               "engagementRate":5.9432746E-4,
               "interactions":8859
            },
            {  
               "likes":2617,
               "comments":55,
               "shares":446,
               "engagementRate":2.0917857E-4,
               "interactions":3118
   ],
         "currentTotal":{  
            "likes":80050,
            "comments":2062,
            "shares":13984,
            "engagementRate":0.0064468323,
            "interactions":96096
         },
         "previousTotal":{  
            "likes":135410,
            "comments":2262,
            "shares":14724,
            "engagementRate":0.0067186337,
            "interactions":152396
         }
      }
   ]
}
```

This endpoint returns information about the number of interactions (likes, shares, comments) and the engagement rate for a Facebook page grouped by day in a selected time period. You can also compare the current total interactions with the previous period. 

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/interactions/count/date`

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

The response contains an array with each element representing a day of the selected period and containing the number of interactions separated by type, alongside with the engagement rate of each day, followed by a `currentTotal`, with the sum of the interactions of all posts within the period and a `previousTotal`, with the same information regarding the previous period. If you select a month, it will be the previous month, if select you select 15 days *(Jun/16 ~ Jun/30)*, it will be the previous 15 days *(Jun/01 ~ Jun/15)*. 

Field | Description | Example
--------- | ----------- | -----------
**likes** | Sum of **likes** over posts in the selected period. | 83275
**comments** | Sum of **comments** over posts in the selected period. | 2519
**shares** | Sum of **shares** over posts in the selected period. | 3314
**interactions** | Sum of likes, comments and shares generated during the selected period. | 94045
**engagementRate** | The **engagement rate** of the post. | 2.7721157E-6



