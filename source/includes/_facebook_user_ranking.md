##fb.User Ranking

```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/users/ranking/comments?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/users/ranking/comments",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "1822115806727"
         ],
         "since":"2016-10-30",
         "until":"2016-11-28"
      }
   },
   "results":[  
      {  
         "id":"1822115806727",
         "data":[  
            {  
               "id":"413531845481303",
               "name":"Juan Perez",
               "comments":11,
               "posts":0
            },
            {  
               "id":"1775081599427091",
               "name":"Maria Gonzalez",
               "comments":9,
               "posts":0
            },
{  
               "id":"1439934276307218",
               "name":"Diego Lopez",
               "comments":4,
               "posts":0
            }
         ]
      }
   ]
}
```

This endpoint returns a ranking of the most active users on a Facebook page, bringing the number of comments and posts they've created in a selected time period, alongside with their `name` and `ID`.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/users/ranking/comments`

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

The response contains a `results` array of objects, which one profile `id` per element. The array `data` contains values representing the name, number of posts and number of comments made by the most active users of the page during the selected time period, starting from the date selected in `since` and ending the date selected in `until`. 

Field | Description | Example
--------- | ----------- | -----------
**id** | The user's **ID**. | 413531845481303
**name** | The user's **name** | Maria Gonzalez
**comments** | The number of **comments** that the user has posted on the page. | 9
**posts** | The number of **posts** that the user has created on the page. | 0

