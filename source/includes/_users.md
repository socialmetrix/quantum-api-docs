# Users

## User Detail
```shell
curl -XGET 'https://quantum.socialmetrix.com/api/v1/accounts/${ACCOUNT}/users/${USER}'\
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{
  "id": "68a3450f0f2b20e8ab6ec2e2838b532b",
  "firstName": "John",
  "lastName": "Smith",
  "email": "johnsmith@johnsmith.com",
  "timezone": "America/Argentina/Buenos_Aires",
  "role": "OWNER",
  "facebookAuth": {
    "userId": "936995519724667",
    "token": "EAAGZBqihd9k8BAORbA6EAlpOx32348J1PdwECGuKkhxDutmdqkskJb07DxLunw76kDeSN7lsBYqHTULVroMQhSvjjtgXntPybMDoJxYzUFU4Hho7d3jgCaJJSLtyz5EiWNYRPf5yZACwhhqypMRhheWZBp4q50ZD"
  },
  "twitterAuth": null,
  "accountId": ACCOUNT ID,
  "projectIds": [
    
  ],
  "createdAt": "2016-10-07T22:22:16Z",
  "lastLogin": "2016-10-09T17:02:32Z"
}
```


This endpoint lists the project's users, passed as parameter on the URL as $USER. The parameters are: the user id, their first and last name, their email and timezone, and their role in the project, for example OWNER. 


### HTTP Request

`GET /accounts/<ACCOUNT>/users/<USER>`

### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT** | The ID obtained from JWT response: `user.accountId` | 790
**USER** | Current user | 68a3450f0f2b20e8ab6ec2e2838b532b

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
**firstName** | User's **first name**. | John
**lastName** |  User's **last name**. | Smith
**email** | User's **email**. | johnsmith@johnsmith.com
**role** | User's **role** in the project. | OWNER


