##fb.Post stats
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/profiles/posts-interactions/count/date?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json

{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/profiles/posts-interactions/count/date",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "182162001806727_1288061994550050",
            "182162001806727_1286728351350081",
            "182162001806727_1290535470969369",
            "182162001806727_1288060071216909",
            "182162001806727_1288808291142087"
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
         "id":"182162001806727_1286728351350081",
         "data":[  
            {  
               "likes":0,
               "comments":0,
               "shares":0,
               "engagementRate":0.0,
               "interactions":0
            },
                  ...ommitted...
            {  
               "likes":35,
               "comments":1,
               "shares":10,
               "engagementRate":2.7721157E-6,
               "interactions":46
            }
         ],
         "currentTotal":{  
            "likes":1512,
            "comments":41,
            "shares":147,
            "engagementRate":1.0244775E-4,
            "interactions":1700
         },
         "previousTotal":{  
            "likes":0,
            "comments":0,
            "shares":0,
            "engagementRate":0.0,
            "interactions":0
         }      
            ...ommitted...
      }
   ]
}
```

This endpoint returns information about the number of interactions (likes, shares, comments) and the engagement rate for different posts of a Facebook page in a selected period. You can also compare the current total interactions with the previous period. 

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/posts-interactions/count/date`

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

The response contains an array with each element representing a post of the selected period and containing the number of interactions separated by type, alongside with the engagement rate of each post, followed by a `currentTotal`, with the sum of the interactions of all posts within the period and a `previousTotal`, with the same information regarding the previous period. If you select a month, it will be the previous month, if select you select 15 days *(Jun/16 ~ Jun/30)*, it will be the previous 15 days *(Jun/01 ~ Jun/15)*. 

Field | Description | Example
--------- | ----------- | -----------
**likes** | Sum of **likes** over posts in the selected period. | 83275
**comments** | Sum of **comments** over posts in the selected period. | 2519
**shares** | Sum of **shares** over posts in the selected period. | 3314
**interactions** | Sum of likes, comments and shares generated during the selected period. | 94045
**engagementRate** | The **engagement rate** of the post. | 2.7721157E-6



