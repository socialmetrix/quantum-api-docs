##fb.Post Count by Date
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/profiles/posts/count/date?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08&\
owner=admin&type=link" \
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

This endpoint gives information about the quantity of posted content from a Facebook page in a given period day by day, it also provides a sum of current period activity and previous period activity. The analysis can be filtered by whom created the content **owner** and by content **type**.

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
***timezone*** | (Optional): Time-zone that my metrics should be calculated | America/Argentina/Buenos_Aires
***owner*** | (Optional): Filter posts only from the page owner `admin` or by the audience `user` | `admin`
***type*** | (Optional): Filter posts by its type:<br />`status`, `link`, `photo`, `video`.<br />If value is missing **all types** will be used | `photo`

### Response

The response contains a `results` array of objects, which one profile `id` per element. The array `data` contains values representing a [Time Series](https://en.wikipedia.org/wiki/Time_series) with an element for each day of the selected period, so the first element is the value for date passed as since and the last element is the value for until.

Field | Description | Example
--------- | ----------- | -----------
**id** | ID of the social profile | 182162001806727
**data** | Daily variations of posts published, each element represents a day | [1,1,2,1,3,3]
**currentTotal** | Total posts published during the current period | 26
**previousTotal** | Total posts published during the previous period | 20


 
