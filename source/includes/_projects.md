# Projects

Any metric, profile or campaigns belongs to a project, so we need to known which project we want to work with. As our first interaction with the API.

## List all projects

```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}/projects" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 0,
    "name": "Demo",
    "createdAt": "2016-11-17T09:58:51Z",
    "accountId": 790,
    "isDemo": true,
    "brands": [
      ... omitted ...
    ]
  },
  {
    "id": 2,
    "name": "Telecom US Market",
    "createdAt": "2014-10-17T19:18:01Z",
    "accountId": 790,
    "isDemo": false,
    "brands": [
      ... omitted ...
    ]
  }
]
```

This endpoint has a complete list of projects and its profiles.

###HTTP Request

`GET /accounts/<ACCOUNT>/projects`


### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT** | The ID obtained from JWT response: `user.accountId` | 790


### Response

The response contains an array of projects (object) with an **id**, **name** and another array **brands** containing **profiles**:

Field | Description | Example
--------- | ----------- | -----------
**id** | The project ID | 0
**name** | The project name, given by the user | Demo
**brands** | An array containing all profiles belonging to this project |


## Project Detail

```shell
# Selecting the Demo Project (id=0)

curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}/projects/0" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 0,
  "name": "Demo",
  "createdAt": "2016-10-07T22:22:16Z",
  "accountId": 1896,
  "isDemo": true,
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
        "status": "1",
        "icon": "https://pic.socialmetrix.com/twitter/415859364/picture"
      },
      {
        "sourceType": "FACEBOOK",
        "id": "FACEBOOK_15087023444",
        "name": "Nike",
        "source": {
          "kind": "FACEBOOK",
          "id": "15087023444",
          "url": "http://www.facebook.com/nike"
        },
        "nextFetch": 0,
        "crawlingData": {
          "initialCrawlingDate": 1399989600,
          "disabled": false
        },
        "username": "nike",
        "hasParent": false,
        "status": "1",
        "icon": "https://pic.socialmetrix.com/facebook/15087023444/picture"
      },
      {
        "sourceType": "YOUTUBE",
        "id": "YOUTUBE_UCUFgkRb0ZHc4Rpq15VRCICA",
        "name": "Nike",
        "source": {
          "kind": "YOUTUBE",
          "id": "UCUFgkRb0ZHc4Rpq15VRCICA",
          "url": "https://www.youtube.com/channel/UCUFgkRb0ZHc4Rpq15VRCICA"
        },
        "nextFetch": 0,
        "crawlingData": {
          "initialCrawlingDate": 1441304646,
          "disabled": false
        },
        "status": "1",
        "icon": "https://pic.socialmetrix.com/youtube/UCUFgkRb0ZHc4Rpq15VRCICA/picture"
      },
      {
        "sourceType": "INSTAGRAM",
        "id": "INSTAGRAM_13460080",
        "name": "nike",
        "source": {
          "kind": "INSTAGRAM",
          "id": "13460080",
          "url": "https://instagram.com/nike/"
        },
        "nextFetch": 0,
        "crawlingData": {
          "initialCrawlingDate": 1423748093,
          "disabled": false
        },
        "username": "nike",
        "status": "1",
        "icon": "https://pic.socialmetrix.com/instagram/13460080/picture"
      }
  ]
}
```

This endpoint gives you information about the selected project. Including all profiles that belongs to this project. Knowing the `source.id` value is necessary to request metrics.

###HTTP Request

`GET /accounts/<ACCOUNT>/projects/<PROJECT>`


### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT** | The ID obtained from JWT response: `user.accountId` | 790
**PROJECT** | The ID of desired project | 0


### Response

Besides the **id** and **name** of the project, the most relevant part of response is the **brands** array of object which contains **profiles**:


Field | Description | Example
--------- | ----------- | -----------
**id** | A composite ID containing the **source** and its **id** | INSTAGRAM_13460080
**name** | Name of the Social Profile | Nike
**icon** | Social Profile Icon/Photo url | [https://pic.socialmetrix...](https://pic.socialmetrix.com/instagram/13460080/picture)
**username / screenName** | Username or Screen Name for the Profile | nike
**source** | Object containing profile's meta-data |
**crawlingData** | Object containing crawling meta-data |

###Source Object

Field | Description | Example
--------- | ----------- | -----------
**id** | ID on the social network | 13460080
**kind** | Supported social network, currently can be: FACEBOOK, TWITTER, YOUTUBE, INSTAGRAM | INSTAGRAM
**url** | social network's profile url | https://instagram.com/nike/


###crawlingData Object

Field | Description | Example
--------- | ----------- | -----------
**initialCrawlingDate** | [epoch](https://en.wikipedia.org/wiki/Epoch_(reference_date)) representation when data becomes available for this profile | 1423748093
**disabled** | If `true` this profile is not active | false
