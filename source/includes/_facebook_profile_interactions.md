##fb.Profile Interactions 
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/0/facebook/profiles/interactions/count/interaction-type?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{
  "query": {
    "id": "/accounts/790/projects/0/facebook/profiles/interactions/count/interaction-type",
    "filters": {
      "timezone": "America/Argentina/Buenos_Aires",
      "ids": [
        "182162001806727",
        "15087023444"
      ],
      "since": "2016-09-09",
      "until": "2016-10-08"
    }
  },
  "results": [
    {
      "id": "15087023444",
      "data": {
        "current": {
          "likes": 6920,
          "comments": 655,
          "shares": 1258,
          "interactions": 8833
        },
        "previous": {
          "likes": 291808,
          "comments": 8313,
          "shares": 147621,
          "interactions": 447742
        }
      }
    },
    {
      "id": "182162001806727",
      "data": {
        "current": {
          "likes": 83275,
          "comments": 2519,
          "shares": 8251,
          "interactions": 94045
        },
        "previous": {
          "likes": 24525,
          "comments": 680,
          "shares": 3314,
          "interactions": 28519
        }
      }
    }
  ]
}
```

This endpoint gives a sum of all interactions metrics (likes, shares, comments) that belongs to the selected profiles.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/interactions/count/interaction-type`

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
**likes** | Sum of **likes** over posts in the selected period | 83275
**comments** | Sum of **comments** over posts in the selected period | 2519
**shares** | Sum of **shares** over posts in the selected period | 3314
**interactions** | Sum of likes, comments and shares generated during the selected period | 94045

