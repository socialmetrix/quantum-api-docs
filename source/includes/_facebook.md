# Facebook

## Facebook Profile Summary 
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/0/facebook/profiles/stat-summary?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{
  "query": {
    "id": "/accounts/1896/projects/0/facebook/profiles/stat-summary",
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
      "id": "182162001806727",
      "data": {
        "current": {
          "totalFans": 22611837,
          "newFans": 172184,
          "newPosts": 34,
          "newInteractions": 94045,
          "engagementRate": 0.0041750576
        },
        "previous": {
          "totalFans": 22439653,
          "newFans": 208958,
          "newPosts": 29,
          "newInteractions": 28519,
          "engagementRate": 0.0012755521
        }
      }
    },
    {
      "id": "15087023444",
      "data": {
        "current": {
          "totalFans": 27003826,
          "newFans": 289127,
          "newPosts": 1,
          "newInteractions": 8833,
          "engagementRate": 0.0003281974
        },
        "previous": {
          "totalFans": 26722160,
          "newFans": 1844729,
          "newPosts": 16,
          "newInteractions": 447742,
          "engagementRate": 0.017771263
        }
      }
    }
  ]
}
```

This endpoint brings all the facebook pages that are listed on the project, among with the info about them. Here you can check the total number of fans, new fans, new posts, new interactions and the engagement rate of all the pages that were added to the account.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/stat-summary`

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
**totalFans** | Number of fans (net) at the end of the selected period | 22611837
**newFans** | Number of fans gained in the selected period | 172184
**newPosts** | Posts created during the selected period. It is the sum of Admin and User Posts | 34
**newInteractions** | Sum of likes, comments and shares generated during the selected period | 94045
**engagementRate** | This indicator measures what portion of the page's audience, engaged with the published content | 0.0041750576

