##fb.Profile Post Ranking by Interactions 
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/0/facebook/profiles/posts/ranking/interactions?\
ids=15087023444&since=2016-09-09&until=2016-10-08&owner=admin" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{
  "query": {
    "id": "/accounts/790/projects/0/facebook/profiles/posts/ranking/interactions",
    "filters": {
      "timezone": "America/Argentina/Buenos_Aires",
      "ids": [
        "15087023444"
      ],
      "since": "2016-09-09",
      "until": "2016-10-08"
    }
  },
  "results": [
    {
      "id": "15087023444",
      "data": [
        {...},
        {...},
        {...},
        {
          "campaignInfo": null,
          "contentInfo": {
            "category": "post",
            "id": null,
            "sourceId": null,
            "contentCreatedTime": null
          },
          "id": "15087023444_10154080895133445",
          "type": 247,
          "message": "Brilliant as individuals. Unstoppable as a nation. Unlimited Together. #justdoit",
          "permalink": "http://www.facebook.com/15087023444/posts/10154080895133445",
          "attachment": "{\"picture\":\"https://scontent.xx.fbcdn.net/v/t1.0-9/s720x720/14022109_10154080895133445_9205327802348821423_n.jpg?oh=50a3f784512782346243c4eab8eb473a&oe=5845ACE9\",\"description\":\"Brilliant as individuals. Unstoppable as a nation. Unlimited Together. #justdoit\",\"name\":\"Timeline Photos\",\"link\":\"https://www.facebook.com/nike/photos/a.440612488444.242105.15087023444/10154080895133445/?type=3\"}",
          "user": {
            "id": "15087023444",
            "name": "Nike",
            "comments": 0,
            "posts": 0
          },
          "pageId": "15087023444",
          "createdTime": "2016-08-20T20:12:36-03:00",
          "lastInteractionTime": null,
          "stats": {
            "likes": 374,
            "comments": 24,
            "shares": 43,
            "engagementRate": 1.6385718e-05,
            "interactions": 441
          },
          "adStatus": "promoted"
        },
        {...},
        {...},
        {...},
        {...},
        {...},
        {...}
      ]
    }
  ]
}
```

This endpoint brings the **top ten posts** with the most interactions in the selected period (regardless if the post was created on the selected range).

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/posts/ranking/interactions`

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
**owner** | Filter the creators of posts, you can see Page's Admin (`admin`) or Page's Audience (`user`) | user
***timezone*** | (Optional): Time-zone that my metrics should be calculated | America/Argentina/Buenos_Aires

### Response

The `results` is array of objects, it contains an `id` field which identifies the **profile id** and the `data` array contains a top 10 ordered list from the most popular to least popular by the number of interactions. The conten fields are related to [Facebook Post official doc.](https://developers.facebook.com/docs/graph-api/reference/v2.8/post)

Field | Description | Example
--------- | ----------- | -----------
**id** | Post Id on the social network | 15087023444_10154216095368445
**type** | Kind of posts. `link`, `status`, `photo`, `video` | 247
**message** | Text of the original post | Brilliant as individuals. Unstoppable as a nation. Unlimited Together. #justdoit
**permalink** | The permanent link to Facebook | [http://www.facebook.com/...](http://www.facebook.com/15087023444/posts/10154080895133445)
**attachment** | An object containing meta-data of the post. It includes picture, link to the photo, etc |
**user** | Contains information about the post's owner. Like `Id` and `Name` | `"name": "Nike"`
**pageId** | The page Id where this post belongs | 15087023444
**createdTime** | Date and Time of the post creation. Adjusted to your Time-zone | 2016-08-20T20:12:36-03:00
**adStatus** | Automatic detection of the kind of posts `organic` or `promoted`| promoted
**stats** | Object containing the interactions for the post, that occurred on the selected period | 

### stats object

Field | Description | Example
--------- | ----------- | -----------
**likes** | Sum of **Likes** of the post in the selected period | 374
**comments** | Sum of **Comments** of the post in the selected period | 24
**shares** | Sum of **Shares** of the post in the selected period | 43
**engagementRate** | **Engagement Rate** of the post in the selected period | 1.6385718e-05
**interactions** | Sum of **interactions** of the post in the selected period | 441
