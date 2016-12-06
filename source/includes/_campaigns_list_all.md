##Campaign List All
```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}\
/projects/${PROJECT}/campaigns" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
[  
   {  
      "id":1019,
      "name":"Campaign Example",
      "accountId":1896,
      "projectId":1,
      "createdTime":"2016-12-05T03:28:29Z"
   }
]
```

This endpoint brings basic information about the campaigns. It shows the names, ids and date of creation of the campaigns on a project. 

### HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>/campaigns`

### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT** | The ID obtained from JWT response: `user.accountId` | 790
**PROJECT** | Current Project | 0

### Query Parameters

No query parameters

### Response

The response is an array of basic information about all the campaigns created on a profile. Each element of the array contains the IDs of the campaign, account and project, alongside with the creation time of each campaign. 

Field | Description | Example
--------- | ----------- | -----------
**id** | The campaign's **id**. | 1019
**name** | The campaign's **name**. | Campaign Example
**accountId** | The account's **id**. | 1896
**projectId** | The project's **id**.  | 1
**createdTime** | The date and time of the creation of a campaign. | "2016-12-05T03:28:29Z"
