### Post counter by date  
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/profiles/posts/count/date?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/1896/projects/0/facebook/profiles/posts/count/date",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "182162001806727"
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
         "id":"182162001806727",
         "data":[  
            1,
            1,
            1,
            1,
            1,
            2,
            1,
             ... omitted ...
         ],
         "currentTotal":26,
         "previousTotal":30
      }
   ]
}
```

This endpoint gives information about the quantity of posted content from a Facebook page in a given period,   day by day, comparing them with the previous period. The analysis can be refined using four filters (statuses, links, videos or photos) that give you the exact number of posts of that type each day, and the total count during the current and previous periods.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/posts/count/date`

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
**currentTotal** | Total posts created during the current period. | 26
**previousTotal** | Total posts created during the previous period. | 20

### Filters

This endpoint allows you to sellect four additional filters. Each of them returns the number of statuses, links, videos or photos posted during the current and previous periods. 

Field | Description | Example
--------- | ----------- | -----------
**statuses** | Current or previously posted statuses. | 18
**links** | Current or previously posted links. | 20
**videos** | Current or previously posted videos. | 15
**photos** | Current or previously posted photos. | 12
 
