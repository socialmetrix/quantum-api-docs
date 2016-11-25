---
title: Quantum API Reference

language_tabs:
  - shell: cURL
  
toc_footers:
  - <a href='https://www.socialmetrix.com/free-trial-quantum-en'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Powered by Slate</a>

includes:
  - projects
  - facebook
  - kittens
  - users
  - usage
  - errors
  - related

search: true
---

# Introduction

Welcome to the **Socialmetrix Quantum API!** Quantum provides relevant information about audience behavior through actionable metrics focused in quantitative analysis, allowing you to designate which actions need to be taken to meet your goals.

This documentation will help you through Quantum API, all its functionalities and endpoints, to make sure you have the best experience with our product.

### URL Structure

Currently our API is on **version 1** and all HTTP requests are made using this base: `https://api.quantum.socialmetrix.com/v1`

### Account Structure

Your account can contains many **Projects**, each project contains many **Profiles**

* Projects
* Social Media Profiles
* Campaigns

# Authentication

This API relies on [Json Web Token (JWT)](https://jwt.io) as autorization/authentication mechanism, to issue a JWT you will need your Quantum API Secret.

## Getting your API Secret

IN order to obtain a


1- Login at [Socialmetrix Quantum](https://quantum.socialmetrix.com) using Facebook or Twitter.

2- After logging-in, go to My Account:

3- Click on My Account:

4- Select option API and copy your API Secret:

<aside class="warning">
Please do not expose your API Secret - if an attacker have control of your API Secret, he/she will be able to delete all your accounts. <b>Keep it safe!</b>
</aside>

## Getting your Json Web Token

You need POST a json containing the `"method": “API-SECRET”` and your `secret`.

```shell
curl -XPOST 'https://api.quantum.socialmetrix.com/login' \ 
  -H "Content-Type: application/json" \ 
  -d '{ "method":"API-SECRET", "secret":"0220a22d27be69e4.........54aa9840e5c4136e"}'
```

> A valid response will contains relevant data of your account:

```json
{
  "jwt": "eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJTTVgiLCJpYXQiOjE0.......zdkOGY5ZDFiMjM0ZiIsIm1ldGhvZCI6IkFwaVNlY3JldExvZ2luIn19.wcHGZaXN.......wMWAC7Vzg3r6I1jREqF_oIV8",
  "user": {
    "id": "806d642b4a6.......937d8f9d1b234f",
    "firstName": "John",
    "lastName": "Smith",
    "email": "jsmith@socialmetrix.com",
    "timezone": "America/New_York",
    "role": "OWNER",
    "facebookAuth": {
      "userId": "557905121"
    },
    "twitterAuth": {
      "userId": "15092087"
    },
    "accountId": 790,
    "projectIds": [],
    "createdAt": "2015-07-23T19:53:13Z",
    "lastLogin": "2016-11-25T01:55:31Z"
  }
}
```

<aside class="success">
**jwt**: This is the JWT authentication header and it **MUST** be used on all requests after authenticating.

**accountId**: Your account Id is used on all requests either.
</aside>

<aside class="notice">
API Secret has an expire of 20 days, you MUST re-authorize at least one time within this period
</aside>
 
