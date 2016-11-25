# Facebook

## Facebook Profile Summary 
```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/projects/0/facebook/profiles/stat-summary?ids=15087023444,182162001806727&since=2016-09-09&timezone=America%2FArgentina%2FBuenos_Aires&until=2016-10-08' \
  -H "Content-Type: application/json" \ 
  -d '{ "method":"API-SECRET", "secret":"0220a22d27be69e4.........54aa9840e5c4136e"}'
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
    
  ]
}
```

This endpoint brings all the facebook pages that are listed on the project, among with the info about them. Here you can check the total number of fans, new fans, new posts, new interactions and the engagement rate of all the pages that were added to the account.

### HTTP Request

`GET /accounts/<ACCOUNT_ID>/projects/<PROJECT_ID>/facebook/profiles/stat-summary`

### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT_ID** | The ID obtained from JWT response: `user.accountId` | 790
**PROJECT_ID** | Current Project | 0

### Query Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ids** | A comma-separated list of profiles ids belonging to the project | 15087023444,182162001806727
**since** | Starting date (inclusive) | 2016-09-09
**until** | Ending date (exclusive) | 2016-09-09
*timezone* | (Optional): Time-zone that my metrics should be calculated | America/Argentina/Buenos_Aires

### Response

The response contains to main objects per **id**, `data.current` contains the acutal period and `data.previous` contains the values for the same previous period lenght.

Field | Description | Example
--------- | ----------- | -----------
**totalFans** | The total amount of fans on the period | 22611837
**newFans** | New fans gained/lost in the period | 172184
**newPosts** | New posts published in the period | 34
**newInteractions** | New interactions in the period | 94045
**engagementRate** | Engagement rate generated in the period | 0.0041750576

