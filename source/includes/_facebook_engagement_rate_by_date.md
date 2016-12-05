##fb.Engagement Rate by date 
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/profiles/engagement-rate/date?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/profiles/engagement-rate/date",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "182162001806727"
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
         "id":"182162001806727",
         "data":[  
            5.9432746E-4,
            2.0917857E-4,
            4.2003434E-4,
            8.245044E-5,
            1.19214346E-4,
            3.2866126E-4,
            9.942356E-5,
            8.9561705E-5,
            1.034488E-4,
            1.5490486E-4,
            8.164539E-5,
            1.5222136E-4,
            3.3409535E-5,
            1.6154652E-4,
            3.6790743E-4,
            3.754883E-4,
            3.140362E-4,
            1.7664117E-4,
            6.819436E-4,
            1.9348013E-4,
            2.346718E-4,
            3.4764703E-4,
            2.000547E-4,
            3.8836908E-4,
            1.3518115E-4,
            1.3880388E-4,
            0.0,
            7.73518E-5,
            0.0,
            1.8522837E-4
         ],
         "currentTotal":0.0064468323,
         "previousTotal":0.0067186337
      }
   ]
}
```

This endpoint returns the engagement rate of a Facebook page ordered by day in a selected time period. You can also compare the current total engagement rate with the previous period. 

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/engagement-rate/date`

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

The `results` is array of objects, it contains an `id` field which identifies the **profile id** and the `data` array contains an array with each line representing a day and containing the engagement rate of a Facebook page during the selected period. If you select a month, it will be the previous month, if select you select 15 days *(Jun/16 ~ Jun/30)*, it will be the previous 15 days *(Jun/01 ~ Jun/15)*. 

Field | Description | Example
--------- | ----------- | -----------
**data** | Each line represents the engagement rate of a day within the selected period. | 1.3880388E-4
