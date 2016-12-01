##fb.Post count by weekday by hour

```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/profiles/posts/count/weekday/hour?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/profiles/posts/count/weekday/hour",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "18216234235326727"
         ],
         "since":"2016-10-30",
         "until":"2016-11-28"
      }
   },
   "results":[  
      {  
         "id":"18216234235326727",
         "data":[  
            [  
               0,
               0,
              ... omitted ...
            ],
            [  
               0,
               1,
               ... omitted ...
            ],
            [  
               0,
               0,               
               ... omitted ...
            ],
            [  
               0,
               0,
               ... omitted ...
            ],
            [  
               0,
               1,
               ... omitted ...
            ],
            [  
               0,
               0,
              ... omitted ...
            ],
            [  
               0,
               0,
               ... omitted ...
            ]
         ]
      }
   ]
}
```

This endpoint gives information about the quantity of posted content from a Facebook page for each day of the week, each hour of the day. The array on data field contains the values of our Time Series, for each day of the selected period, so the first element is the value for date passed as `since` and the last element is the value for `until`. You probably want to use these information together to generate a table o chart.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/posts/count/weekday/hour`

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
**Arrays** | Each array stands for one day of the week. |  [0,0,0,0,0,0,0,0,0,0,0,0,0,1...]
**Lines** | Each line stands for one hour of the day. |  1
