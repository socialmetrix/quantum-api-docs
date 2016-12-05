##fb.Post content
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/facebook/profiles/${PROFILE}/posts?\
ids=15087023444,182162001806727&since=2016-09-09&until=2016-10-08" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{  
   "query":{  
      "id":"/accounts/ACCOUNT/projects/PROJECT/facebook/profiles/PROFILE/posts",
      "filters":{  
         "timezone":"America/Argentina/Buenos_Aires",
         "ids":[  
            "1921622154547"
         ],
         "since":"2016-10-30",
         "until":"2016-11-28"
      }
   },
   "results":[  
      {  
         "campaignInfo":null,
         "contentInfo":{  
            "category":"post",
            "id":null,
            "sourceId":null,
            "contentCreatedTime":null
         },
         "id":"182162001806727_1288808291142087",
         "type":247,
         "message":"Find mental strength for the journey ahead. #FindFocus #ZNE",
         "permalink":"http://www.facebook.com/182162001806727/posts/1288808291142087",
         "attachment":"{\"picture\":\"https://scontent.xx.fbcdn.net/v/t1.0-9/s720x720/15241949_1288808291142087_7864157418689005368_n.jpg?oh=4c8a94f25c2ddff3b1cf2a55ccd83102&oe=58D016B5\",\"description\":\"Find mental strength for the journey ahead. #FindFocus #ZNE\",\"name\":\"Timeline Photos\",\"link\":\"https://www.facebook.com/adidas/photos/a.191308754225385.42450.182162001806727/1288808291142087/?type=3\"}",
         "user":{  
            "id":"182162001806727",
            "name":"adidas",
            "comments":0,
            "posts":0
         },
         "pageId":"182162001806727",
         "createdTime":"2016-11-27T05:00:01-03:00",
         "lastInteractionTime":"2016-11-29T00:00:00-03:00",
         "adStatus":"promoted"
      }
   ]
}
```

This endpoint brings information about the content posted on a Facebook page for a selected period. Here you can check, alongside with the status, video, link or photo, the date the post was created, the time of the last interaction on the post, and whether it was promoted or is organic.

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/facebook/profiles/<PROFILE>/posts`

### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT** | The ID obtained from JWT response: `user.accountId` | 790
**PROJECT** | Current Project | 0
**PROFILE** | Current Profile | 192162001806727

### Query Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ids** | A comma-separated list of profiles ids belonging to the project | 15087023444,182162001806727
**since** | Starting date (inclusive) | 2016-09-09
**until** | Ending date (exclusive) | 2016-10-08
***timezone*** | (Optional): Time-zone that my metrics should be calculated | America/Argentina/Buenos_Aires
***owner*** | (Optional): Filter posts only from the page owner `admin` or by the audience `user` | `admin`
***type*** | (Optional): Filter posts by its type:<br />`status`, `link`, `photo`, `video`.<br />If value is missing **all types** will be used | `photo`
***limit***|The limit of posts showed for a selected period.|5 

### Response

The response contains information about the campaign and the content, if it's available, followed by an array with the content posted in the selected time period and according to the limit set in the parameters. Each element contains an `id` and a `type`, a permalink to the original post, the message and attachments of the post, the date the post was created, the time of the last interaction on the post, and whether it was promoted or is organic.

Field | Description | Example
--------- | ----------- | -----------
**message** | The **text** part of the post. | "Find mental strength for the journey ahead. #FindFocus #ZNE"
**permalink** | The **permalink** to the original post. | "http://www.facebook.com/182162001806727/posts/1288808291142087"
**attachment** | The **attachments**, such as pictures or videos, of the post. | "{\"picture\":\"https://scontent.xx.fbcdn.net/v/t1.0-9/s720x720/15241949_1288808291142087_7864157418689005368_n.jpg?oh=4c8a94f25c2ddff3b1cf2a55ccd83102&oe=58D016B5\",\"description\":\"Find mental strength for the journey ahead. #FindFocus #ZNE\",\"name\":\"Timeline Photos\",\"link\":\"https://www.facebook.com/adidas/photos/a.191308754225385.42450.182162001806727/1288808291142087/?type=3\"}"
**createdTime** | **Date and time** of the creation of the post. | "2016-11-27T05:00:01-03:00"
**lastInteractionTime** | **Date and time** of the last interaction on the post. | "2016-11-29T00:00:00-03:00"
**adStatus** | Whether the post is promoted or organic. | promoted
