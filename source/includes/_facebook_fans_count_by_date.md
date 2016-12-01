##fb.Fans count by date

```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/fans/count/date?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/fans/count/date",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "182162321546727"
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
         "id":"182162321546727",
         "data":[  
            7259,
            6056,
            3488,
            -8587420,
            -2861409
           ... omitted ...
           
         ],
         "currentTotal":-11343999,
         "previousTotal":188739
      }
   ]
}
```

This endpoint gives the number of fans of a Facebook page for each day of the selected period. The array on data field contains the values of our Time Series, for each day of the selected period, so the first element is the value for date passed as `since` and the last element is the value for `until`. You probably want to use these information together to generate a table o chart.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/fans/count/date`

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

The response contains a `data` object per each profile `id`, inside `data.current` is contained the acutal date period and `data.previous` contains the values for the same previous period. If you select a month, it will be the previous month, if select you select 15 days *(Jun/16 ~ Jun/30)*, it will be the previous 15 days *(Jun/01 ~ Jun/15)*. 

Field | Description | Example
--------- | ----------- | -----------
**Lines** | Each line stands for the number of fans on a **date** of the selected period. | 7259

