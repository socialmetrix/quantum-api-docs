##fb.Post Interactions by Date

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
      "id":"/accounts/1896/projects/0/facebook/profiles/interactions/count/date",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "1842342346727"
         ],
         "since":"2016-10-30",
         "until":"2016-11-28"
      },
      "period":{  
         "id":"1d",
         "duration":86400
      }
   },
   "results":[  
      {  
         "id":"1842342346727",
         "data":[  
            {  
               "likes":22336,
               "comments":297,
               "shares":3209,
               "engagementRate":0.0015449481,
               "interactions":25842
            },
            {  
               "likes":2537,
               "comments":64,
               "shares":621,
               "engagementRate":1.9262529E-4,
               "interactions":3222
            },
            {  
               "likes":4207,
               "comments":132,
               "shares":591,
               "engagementRate":2.9473702E-4,
               "interactions":4930
            },           
            {  
               "likes":1799,
               "comments":24,
               "shares":192,
               "engagementRate":1.20465535E-4,
               "interactions":2015
            }
         ],
         "currentTotal":{  
            "likes":111616,
            "comments":2606,
            "shares":19102,
            "engagementRate":0.007970693,
            "interactions":133324
         },
         "previousTotal":{  
            "likes":101317,
            "comments":1710,
            "shares":9532,
            "engagementRate":0.004969201,
            "interactions":112559
         }
      }
   ]
}
```

This endpoint gives the number of likes, comments, shares, interactions and the engagement rate of a Facebook page for each day of the selected period. The array on data field contains the values of our Time Series, for each day of the selected period, so the first element is the value for date passed as `since` and the last element is the value for `until`. You probably want to use these information together to generate a table o chart.

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
**owner** | Owner of the project | admin
***timezone*** | (Optional): Time-zone that my metrics should be calculated | America/Argentina/Buenos_Aires

### Response

The response contains a `data` object per each profile `id`, inside `data.current` is contained the acutal date period and `data.previous` contains the values for the same previous period. If you select a month, it will be the previous month, if select you select 15 days *(Jun/16 ~ Jun/30)*, it will be the previous 15 days *(Jun/01 ~ Jun/15)*. 

Field | Description | Example
--------- | ----------- | -----------
**likes** | The number of **likes** in a date of the selected period. | 111616
**comments** | The number of **comments** in a date of the selected period. |  2606
**shares** | The number of **shares** in a date of the selected period. |  19102
**engagementRate** | The **engagement rate** of the page in a date of the selected period. |  0.007970693
**interactions** | Sum of **likes, comments and shares** generated during a date of the selected period. |  133324

