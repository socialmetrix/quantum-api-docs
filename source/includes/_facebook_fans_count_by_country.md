##fb.Fans count by country  
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/fans/count/country/date?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/fans/count/country/date",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "444462001806727"
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
            {  
               "id":"DE",
               "data":[  
                  {  
                     "newFans":149,
                     "uniqueUsers":686
                  },
                  {  
                     "newFans":32,
                     "uniqueUsers":593
                  },
                   ... omitted ...
                ]
      {
    ]
}
```

This endpoint brings information about new fans and unique users of a Facebook page on a selected period according to their country. Every country has an ID and the array on data field contains the values of our Time Series, for each day of the selected period, so the first element is the value for date passed as `since` and the last element is the value for `until`. You probably want to use these information together to generate a table o chart.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/fans/count/country/date`

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
**newFans** | Number of **new fans** on the selected date. | 32
**uniqueUsers** | Number of **unique users** on the selected date. | 593
