# Projects

All information metrics are organized inside Projects, naturally this will be the first request you need to make.

## List all projects

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/projects' \
  -H "Content-Type: application/json" \ 
  -d '{ "method":"API-SECRET", "secret":"0220a22d27be69e4.........54aa9840e5c4136e"}'
```

> The above command returns JSON structured like this:

```json
{
  TODO TODO TODO TODO TODO TODO TODO
  TODO TODO TODO TODO TODO TODO TODO
  TODO TODO TODO TODO TODO TODO TODO 
}
```

One of the first requests you probably will do is get a list of all your active projects.


###HTTP Request

`GET /accounts/<ACCOUNT>/projects`


### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT** | The ID obtained from JWT response: `user.accountId` | 790



## Project Detail



```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/projects/0' 
```

> The above command returns JSON structured like this:

```json
{
  "id": 0,
  "name": "Demo",
  "createdAt": "2016-10-07T22:22:16Z",
  "brands": [
    {
      "sourceType": "TWITTER",
      "id": "TWITTER_415859364",
      "name": "Nike",
      "source": {
        "kind": "TWITTER",
        "id": "415859364",
        "url": "http://twitter.com/Nike"
      },
      "nextFetch": 0,
      "crawlingData": {
        "initialCrawlingDate": 1415119279,
        "disabled": false
      },
      "screenName": "Nike",
      "icon": "https://pic.socialmetrix.com/twitter/415859364/picture",
      "status": "1"
    },
    ...
  ],
  "accountId": 1896,
  "isDemo": true
}
```

This endpoint gives you information about project $PROJECT. Obtain information about the project $PROJECT (passed as parameter on the URL). This endpoint will provide profiles (Facebook, Twitter, YouTube and Instagram) among with their meta-data.