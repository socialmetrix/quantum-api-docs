##fb.Campaign Posts by Date
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/campaigns/posts/count/date?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08&\
owner=admin&type=link" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/1896/projects/1/facebook/campaigns/posts/count/date",
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
               "statuses":0,
               "links":0,
               "videos":0,
               "photos":0
            },
            {  
               "statuses":0,
               "links":0,
               "videos":0,
               "photos":0
            },
            {  
               "statuses":0,
               "links":0,
               "videos":0,
               "photos":0
            }
         ],
         "currentTotal":{  
            "statuses":0,
            "links":0,
            "videos":0,
            "photos":0
         },
         "previousTotal":{  
            "statuses":0,
            "links":0,
            "videos":0,
            "photos":0
         }
      }
   ]
}
```

This endpoint gives information about the quantity of posted content (statuses, links, videos and photos) from a campaign in a given period day by day, it also provides a sum of current period activity and previous period activity. 

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/campaigns/posts/count/date`

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
**statuses** | Current or previously posted statuses. | 18
**links** | Current or previously posted links. | 20
**videos** | Current or previously posted videos. | 15
**photos** | Current or previously posted photos. | 12
