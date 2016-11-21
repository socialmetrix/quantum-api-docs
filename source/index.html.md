---
title: API Reference

language_tabs:
  - shell
  
toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Quantum SocialMetrix API! Quantum presents relevant information about audience behavior through actionable metrics focused in quantitative analysis, allowing you to designate which actions need to be taken to meet your goals.


This documentation will help you through Quantum, all its functionalities and endpoints, to make sure you have the best experience with our product. 

# Facebook

## Project info

 This endpoint gives you information about project $PROJECT. Obtain information about the project $PROJECT (passed as parameter on the URL). This endpoint will provide profiles (Facebook, Twitter, YouTube and Instagram) among with their meta-data.

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

## Users info

 This endpoint lists the project's users, passed as parameter on the URL as $USER. The parameters are: the user id, their first and last name, their email and timezone, and their role in the project, for example OWNER. 

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

## Limits info

 This endpoint details the account's limits according to the user's plan. Here you can see how many campaigns, projects, profiles, swaps, users and fans fans the account currently has. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/limits/available'
```

> The above command returns JSON structured like this:

```json
{
  "campaigns": 0,
  "projects": 1,
  "profiles": 4,
  "swaps": 2,
  "users": 1,
  "fans": 600000
}
```

## Billing info

 This endpoint gives you all the billing information available. Here you can check whether or not the account is on its Trial period, the current billing amount in cents, the current period start and end, when is the next billing, and the plan that is currently active. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/billing-info'
```

> The above command returns JSON structured like this:

```json
{
  "accountId": 1896,
  "isTrial": true,
  "currentBillingAmountInCents": 9900,
  "currentPeriodStart": "2016-10-07T22:22:15Z",
  "currentPeriodEnd": "2016-10-21T22:22:15Z",
  "nextBilling": "2016-10-21T22:22:15Z",
  "plan": {
    "name": "Starter Monthly",
    "priceInCents": 9900,
    "intervalUnit": "month",
    "interval": 1,
    "trialIntervalUnit": "day",
    "trialInterval": 14,
    "limits": {
      "projects": 1,
      "campaigns": 0,
      "profiles": 4,
      "swaps": 2,
      "users": 1,
      "fans": 600000
    },
    "handle": "0-0-0"
  },
  "coupon": null,
  "pendingCancellation": false,
  "nextPlan": null,
  "paymentType": "creditCard"
}
```
## Consumed limits info

 This endpoint details everything that has been consumed by the account. It gives the number of  users, campaigns, swaps, projects, profiles and fans created by the account. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/limits/consumed' 
```

> The above command returns JSON structured like this:

```json
{
  "users": 1,
  "campaigns": 0,
  "swaps": 0,
  "projects": 0,
  "profiles": 0,
  "fans": 0
}
```

## Facebook pages info

 This endpoint brings all the facebook pages that are listed on the project, among with the info about them. Here you can check the total number of fans, new fans, new posts, new interactions and the engagement rate of all the pages that were added to the account. 
 
```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/projects/0/facebook/profiles/stat-summary?ids=15087023444,182162001806727&since=2016-09-09&timezone=America%2FArgentina%2FBuenos_Aires&until=2016-10-08' 
```

> The above command returns JSON structured like this:

```json
"{
  ""query"": {
    ""id"": ""/accounts/1896/projects/0/facebook/profiles/stat-summary"",
    ""filters"": {
      ""timezone"": ""America/Argentina/Buenos_Aires"",
      ""ids"": [
        ""182162001806727"",
        ""15087023444""
      ],
      ""since"": ""2016-09-09"",
      ""until"": ""2016-10-08""
    }
  },
  ""results"": [
    {
      ""id"": ""182162001806727"",
      ""data"": {
        ""current"": {
          ""totalFans"": 22611837,
          ""newFans"": 172184,
          ""newPosts"": 34,
          ""newInteractions"": 94045,
          ""engagementRate"": 0.0041750576
        },
        ""previous"": {
          ""totalFans"": 22439653,
          ""newFans"": 208958,
          ""newPosts"": 29,
          ""newInteractions"": 28519,
          ""engagementRate"": 0.0012755521
        }
      }
    },
    
  ]
}"
```


# Twitter

## Project info

 This endpoint gives you information about project $PROJECT. Obtain information about the project $PROJECT (passed as parameter on the URL). This endpoint will provide profiles (Facebook, Twitter, YouTube and Instagram) among with their meta-data.

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

## Users info

 This endpoint lists the project's users, passed as parameter on the URL as $USER. The parameters are: the user id, their first and last name, their email and timezone, and their role in the project, for example OWNER. 

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

## Limits info

 This endpoint details the account's limits according to the user's plan. Here you can see how many campaigns, projects, profiles, swaps, users and fans fans the account currently has. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/limits/available'
```

> The above command returns JSON structured like this:

```json
{
  "campaigns": 0,
  "projects": 1,
  "profiles": 4,
  "swaps": 2,
  "users": 1,
  "fans": 600000
}
```

## Billing info

 This endpoint gives you all the billing information available. Here you can check whether or not the account is on its Trial period, the current billing amount in cents, the current period start and end, when is the next billing, and the plan that is currently active. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/billing-info'
```

> The above command returns JSON structured like this:

```json
{
  "accountId": 1896,
  "isTrial": true,
  "currentBillingAmountInCents": 9900,
  "currentPeriodStart": "2016-10-07T22:22:15Z",
  "currentPeriodEnd": "2016-10-21T22:22:15Z",
  "nextBilling": "2016-10-21T22:22:15Z",
  "plan": {
    "name": "Starter Monthly",
    "priceInCents": 9900,
    "intervalUnit": "month",
    "interval": 1,
    "trialIntervalUnit": "day",
    "trialInterval": 14,
    "limits": {
      "projects": 1,
      "campaigns": 0,
      "profiles": 4,
      "swaps": 2,
      "users": 1,
      "fans": 600000
    },
    "handle": "0-0-0"
  },
  "coupon": null,
  "pendingCancellation": false,
  "nextPlan": null,
  "paymentType": "creditCard"
}
```
## Consumed limits info

 This endpoint details everything that has been consumed by the account. It gives the number of  users, campaigns, swaps, projects, profiles and fans created by the account. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/limits/consumed' 
```

> The above command returns JSON structured like this:

```json
{
  "users": 1,
  "campaigns": 0,
  "swaps": 0,
  "projects": 0,
  "profiles": 0,
  "fans": 0
}
```

## Twitter profiles info

 This endpoint brings all the twitter profiles that are listed on the project, among with the info about them. Here you can check the total number of fans, new fans, new posts, new interactions and the engagement rate of all the pages that were added to the account. 
 
```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/projects/0/facebook/profiles/stat-summary?ids=15087023444,182162001806727&since=2016-09-09&timezone=America%2FArgentina%2FBuenos_Aires&until=2016-10-08' 
```

> The above command returns JSON structured like this:

```json
"{
  ""query"": {
    ""id"": ""/accounts/1896/projects/0/facebook/profiles/stat-summary"",
    ""filters"": {
      ""timezone"": ""America/Argentina/Buenos_Aires"",
      ""ids"": [
        ""182162001806727"",
        ""15087023444""
      ],
      ""since"": ""2016-09-09"",
      ""until"": ""2016-10-08""
    }
  },
  ""results"": [
    {
      ""id"": ""182162001806727"",
      ""data"": {
        ""current"": {
          ""totalFans"": 22611837,
          ""newFans"": 172184,
          ""newPosts"": 34,
          ""newInteractions"": 94045,
          ""engagementRate"": 0.0041750576
        },
        ""previous"": {
          ""totalFans"": 22439653,
          ""newFans"": 208958,
          ""newPosts"": 29,
          ""newInteractions"": 28519,
          ""engagementRate"": 0.0012755521
        }
      }
    },
    
  ]
}"
```

# Youtube

## Project info

 This endpoint gives you information about project $PROJECT. Obtain information about the project $PROJECT (passed as parameter on the URL). This endpoint will provide profiles (Facebook, Twitter, YouTube and Instagram) among with their meta-data.

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

## Users info

 This endpoint lists the project's users, passed as parameter on the URL as $USER. The parameters are: the user id, their first and last name, their email and timezone, and their role in the project, for example OWNER. 

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

## Limits info

 This endpoint details the account's limits according to the user's plan. Here you can see how many campaigns, projects, profiles, swaps, users and fans fans the account currently has. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/limits/available'
```

> The above command returns JSON structured like this:

```json
{
  "campaigns": 0,
  "projects": 1,
  "profiles": 4,
  "swaps": 2,
  "users": 1,
  "fans": 600000
}
```

## Billing info

 This endpoint gives you all the billing information available. Here you can check whether or not the account is on its Trial period, the current billing amount in cents, the current period start and end, when is the next billing, and the plan that is currently active. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/billing-info'
```

> The above command returns JSON structured like this:

```json
{
  "accountId": 1896,
  "isTrial": true,
  "currentBillingAmountInCents": 9900,
  "currentPeriodStart": "2016-10-07T22:22:15Z",
  "currentPeriodEnd": "2016-10-21T22:22:15Z",
  "nextBilling": "2016-10-21T22:22:15Z",
  "plan": {
    "name": "Starter Monthly",
    "priceInCents": 9900,
    "intervalUnit": "month",
    "interval": 1,
    "trialIntervalUnit": "day",
    "trialInterval": 14,
    "limits": {
      "projects": 1,
      "campaigns": 0,
      "profiles": 4,
      "swaps": 2,
      "users": 1,
      "fans": 600000
    },
    "handle": "0-0-0"
  },
  "coupon": null,
  "pendingCancellation": false,
  "nextPlan": null,
  "paymentType": "creditCard"
}
```
## Consumed limits info

 This endpoint details everything that has been consumed by the account. It gives the number of  users, campaigns, swaps, projects, profiles and fans created by the account. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/limits/consumed' 
```

> The above command returns JSON structured like this:

```json
{
  "users": 1,
  "campaigns": 0,
  "swaps": 0,
  "projects": 0,
  "profiles": 0,
  "fans": 0
}
```

## Youtube channels info

 This endpoint brings all the Youtube channels that are listed on the project, among with the info about them. Here you can check the total number of fans, new fans, new posts, new interactions and the engagement rate of all the pages that were added to the account. 
 
```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/projects/0/facebook/profiles/stat-summary?ids=15087023444,182162001806727&since=2016-09-09&timezone=America%2FArgentina%2FBuenos_Aires&until=2016-10-08' 
```

> The above command returns JSON structured like this:

```json
"{
  ""query"": {
    ""id"": ""/accounts/1896/projects/0/facebook/profiles/stat-summary"",
    ""filters"": {
      ""timezone"": ""America/Argentina/Buenos_Aires"",
      ""ids"": [
        ""182162001806727"",
        ""15087023444""
      ],
      ""since"": ""2016-09-09"",
      ""until"": ""2016-10-08""
    }
  },
  ""results"": [
    {
      ""id"": ""182162001806727"",
      ""data"": {
        ""current"": {
          ""totalFans"": 22611837,
          ""newFans"": 172184,
          ""newPosts"": 34,
          ""newInteractions"": 94045,
          ""engagementRate"": 0.0041750576
        },
        ""previous"": {
          ""totalFans"": 22439653,
          ""newFans"": 208958,
          ""newPosts"": 29,
          ""newInteractions"": 28519,
          ""engagementRate"": 0.0012755521
        }
      }
    },
    
  ]
}"
```

# Instagram

## Project info

 This endpoint gives you information about project $PROJECT. Obtain information about the project $PROJECT (passed as parameter on the URL). This endpoint will provide profiles (Facebook, Twitter, YouTube and Instagram) among with their meta-data.

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

## Users info

 This endpoint lists the project's users, passed as parameter on the URL as $USER. The parameters are: the user id, their first and last name, their email and timezone, and their role in the project, for example OWNER. 

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

## Limits info

 This endpoint details the account's limits according to the user's plan. Here you can see how many campaigns, projects, profiles, swaps, users and fans fans the account currently has. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/limits/available'
```

> The above command returns JSON structured like this:

```json
{
  "campaigns": 0,
  "projects": 1,
  "profiles": 4,
  "swaps": 2,
  "users": 1,
  "fans": 600000
}
```

## Billing info

 This endpoint gives you all the billing information available. Here you can check whether or not the account is on its Trial period, the current billing amount in cents, the current period start and end, when is the next billing, and the plan that is currently active. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/billing-info'
```

> The above command returns JSON structured like this:

```json
{
  "accountId": 1896,
  "isTrial": true,
  "currentBillingAmountInCents": 9900,
  "currentPeriodStart": "2016-10-07T22:22:15Z",
  "currentPeriodEnd": "2016-10-21T22:22:15Z",
  "nextBilling": "2016-10-21T22:22:15Z",
  "plan": {
    "name": "Starter Monthly",
    "priceInCents": 9900,
    "intervalUnit": "month",
    "interval": 1,
    "trialIntervalUnit": "day",
    "trialInterval": 14,
    "limits": {
      "projects": 1,
      "campaigns": 0,
      "profiles": 4,
      "swaps": 2,
      "users": 1,
      "fans": 600000
    },
    "handle": "0-0-0"
  },
  "coupon": null,
  "pendingCancellation": false,
  "nextPlan": null,
  "paymentType": "creditCard"
}
```
## Consumed limits info

 This endpoint details everything that has been consumed by the account. It gives the number of  users, campaigns, swaps, projects, profiles and fans created by the account. 

```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/limits/consumed' 
```

> The above command returns JSON structured like this:

```json
{
  "users": 1,
  "campaigns": 0,
  "swaps": 0,
  "projects": 0,
  "profiles": 0,
  "fans": 0
}
```

## Instagram accounts info

 This endpoint brings all the Instagram accounts that are listed on the project, among with the info about them. Here you can check the total number of fans, new fans, new posts, new interactions and the engagement rate of all the pages that were added to the account. 
 
```shell
curl 'https://quantum.socialmetrix.com/api/v1/accounts/1896/projects/0/facebook/profiles/stat-summary?ids=15087023444,182162001806727&since=2016-09-09&timezone=America%2FArgentina%2FBuenos_Aires&until=2016-10-08' 
```

> The above command returns JSON structured like this:

```json
"{
  ""query"": {
    ""id"": ""/accounts/1896/projects/0/facebook/profiles/stat-summary"",
    ""filters"": {
      ""timezone"": ""America/Argentina/Buenos_Aires"",
      ""ids"": [
        ""182162001806727"",
        ""15087023444""
      ],
      ""since"": ""2016-09-09"",
      ""until"": ""2016-10-08""
    }
  },
  ""results"": [
    {
      ""id"": ""182162001806727"",
      ""data"": {
        ""current"": {
          ""totalFans"": 22611837,
          ""newFans"": 172184,
          ""newPosts"": 34,
          ""newInteractions"": 94045,
          ""engagementRate"": 0.0041750576
        },
        ""previous"": {
          ""totalFans"": 22439653,
          ""newFans"": 208958,
          ""newPosts"": 29,
          ""newInteractions"": 28519,
          ""engagementRate"": 0.0012755521
        }
      }
    },
    
  ]
}"
```

# Authentication

All methods in the API need to be authenticated with Json Web Token (JWT), in order to obtain your JWT you need to:

- Get your API Secret
- Submit a request to /login with your API Secret
- Read the response and store your JWT for less than 20 days

## Getting your API Secret

1- Login at Socialmetrix Quantum using Facebook or Twitter.

2- After logging-in, go to My Account:

3- Click on My Account:

4- Select option API and copy your API Secret:

<aside class="success">
IMPORTANT: Please do not expose your API Secret - if an attacker have control of your API Secret, he/she will be able to delete all your accounts. Keep it safe!
</aside>

## Getting your Json Web Token

You need POST a json containing the method (“API-SECRET”) and your secret. As show below:

`-curl -XPOST 'https://api.quantum.socialmetrix.com/login' \ -H "Content-Type: application/json" \ -d '{ "method":"API-SECRET", "secret":"0220a22d27be69e4.........54aa9840e5c4136e"}'`

If everything is OK, the response contains two important fields that will be used on subsequent requests jwt and accountId.

<aside class="success">
IMPORTANT: API Secret has an expire of 20 days, you MUST re-authorize at least one time within this period
</aside>
 
## Requesting your current projects

One of the first requests you probably will do is get a list of all your active projects.

The endpoint to access is: `GET https://api.quantum.socialmetrix.com/v1/accounts/YOUR_ACCOUNT_ID/projects`

A sample request is:

`curl -XGET 'https://api.quantum.socialmetrix.com/v1/accounts/790/projects' \   -H "Content-Type: application/json" \   -H "X-Auth-Token: eyJhbGciOiJIUzI1NiJ9.eyJpc3M.........Xl294h4pM7FSLkpq2nUE5_VSgt5KoYIo" `

<aside class="success">
That’s all! Next time, we will get more information to understand specific aspects from the social profiles.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

