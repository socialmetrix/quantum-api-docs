# Users

##User Detail

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/users/68a3450f0f2b20e8ab6ec2e2838b532b' 
```

> The above command returns JSON structured like this:

```json
{
  "id": "68a3450f0f2b20e8ab6ec2e2838b532b",
  "firstName": "John",
  "lastName": "Smith",
  "email": "johnsmitha@johnsmith.com",
  "timezone": "America/Argentina/Buenos_Aires",
  "role": "OWNER",
  "facebookAuth": {
    "userId": "936995519724667",
    "token": "EAAGZBqihd9k8BAORbA6EAlpOx32348J1PdwECGuKkhxDutmdqkskJb07DxLunw76kDeSN7lsBYqHTULVroMQhSvjjtgXntPybMDoJxYzUFU4Hho7d3jgCaJJSLtyz5EiWNYRPf5yZACwhhqypMRhheWZBp4q50ZD"
  },
  "twitterAuth": null,
  "accountId": 1896,
  "projectIds": [
    
  ],
  "createdAt": "2016-10-07T22:22:16Z",
  "lastLogin": "2016-10-09T17:02:32Z"
}
```

This endpoint lists the project's users, passed as parameter on the URL as $USER. The parameters are: the user id, their first and last name, their email and timezone, and their role in the project, for example OWNER. 
