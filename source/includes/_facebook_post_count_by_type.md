##fb.Post Count by Type  
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/profiles/posts/count/type?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/posts/count/type",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "32654646532"
         ],
         "since":"2016-10-30",
         "until":"2016-11-28"
      }
   },
   "results":[  
      {  
         "id":"182162001806727",
         "data":{  
            "current":{  
               "statuses":0,
               "links":0,
               "videos":8,
               "photos":18
            },
            "previous":{  
               "statuses":0,
               "links":0,
               "videos":13,
               "photos":17
            }
         }
      }
   ]
}
```

This endpoint gives information about the quantity of current and previously posted content from a Facebook page according to their type: statuses, links, videos or photos.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/posts/count/type`

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
**statuses** | Current or previously posted statuses. | 18
**links** | Current or previously posted links. | 20
**videos** | Current or previously posted videos. | 15
**photos** | Current or previously posted photos. | 12

 
