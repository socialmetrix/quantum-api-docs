##Campaign Interaction by Date
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/campaigns/interactions/count/date?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/campaigns/interactions/count/date",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "1019"
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
         "id":"1019",
         "data":[  
            {  
               "likes":0,
               "comments":0,
               "shares":0,
               "interactions":0
            },
            {  
               "likes":0,
               "comments":0,
               "shares":0,
               "interactions":0
            }
         ],
         "currentTotal":{  
            "likes":0,
            "comments":0,
            "shares":0,
            "interactions":0
         },
         "previousTotal":{  
            "likes":0,
            "comments":0,
            "shares":0,
            "interactions":0
         }
      }
   ]
}
```

This endpoint gives the number of likes, comments, shares, interactions and the engagement rate of a campaign for each day of the selected period. The array on data field contains the values of our Time Series, for each day of the selected period, so the first element is the value for date passed as `since` and the last element is the value for `until`. You probably want to use these information together to generate a table o chart.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/campaigns/interactions/count/date`

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

The response contains a `results` array of objects, which one profile `id` per element. The array `data` contains values representing a [Time Series](https://en.wikipedia.org/wiki/Time_series) with an element for each day of the selected period, so the first element is the value for date passed as since and the last element is the value for until.
 

Field | Description | Example
--------- | ----------- | -----------
**likes** | The number of **likes** in a date of the selected period. | 111616
**comments** | The number of **comments** in a date of the selected period. |  2606
**shares** | The number of **shares** in a date of the selected period. |  19102
**interactions** | Sum of **likes, comments and shares** generated during a date of the selected period. |  133324
