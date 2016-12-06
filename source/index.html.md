---
title: WIP - Quantum API Reference

language_tabs:
  - shell: cURL
  
toc_footers:
  - <a href='https://www.socialmetrix.com/free-trial-quantum-en'>Sign Up to Quantum</a>

includes:
  - projects
  - facebook
  - facebook_profile_summary
  - facebook_profile_interactions
  - facebook_profile_posts_ranking_interactions
  - facebook_post_count_by_date
  - facebook_post_count_by_type
  - facebook_post_count_by_weekday_by_hour
  - facebook_post_interactions_count_by_date
  - facebook_fans_count_by_date
  - facebook_fans_count_by_country
  - facebook_user_ranking
  - facebook_profile_interactions
  - facebook_post_content
  - facebook_post_stats
  - facebook_profile_posts_ranking_interactions
  - facebook_activity_count_by_weekday
  - facebook_page_stats
  - facebook_engagement_rate_by_date
  - campaigns
  - campaigns_stats
  - campaigns_interaction_count_by_date
  - campaigns_post_count_by_type
  - campaigns_post_count_by_date
  - users
  - usage
  - others
  - errors
  - related

search: true
---

# Introduction

<aside class="warning">
This documentation is a work-in-progress, we're working hard to complete it the next weeks. If you have specific questions, please reach us <b>info [at] socialmetrix.com</b> so we can give you a properly answer.
</aside>


Welcome to the **Socialmetrix Quantum API!** Quantum provides relevant information about audience behavior through actionable metrics focused in quantitative analysis, allowing you to designate which actions need to be taken to meet your goals.

This documentation will help you through Quantum API, all its functionalities and endpoints, to make sure you have the best experience with our product.

### Understand Information Organization

Your **Account** is the top element on the structure, as an [Account Owner](#roles) you can create all elements 

Accessing your [account](#roles), you can create several [projects](#projects), on each project you can load profiles for [Facebook](#facebook), [Twitter](#twitter), [YouTube](#youtube) and [Instagram](#instagram), on each profile you can query specific metrics for the Social Network, also you can add content to a [campaign](#campaign) and access those as consolidate metrics.

![Quantum API Structure](/images/api-structure.png)

### URL Structure

Currently our API is on **version 1** and all HTTP requests are made using this base: `https://api.quantum.socialmetrix.com/v1`.

# Authentication

This API relies on [Json Web Token (JWT)](https://jwt.io) as autorization/authentication mechanism, to issue a JWT you will need your Quantum API Secret.

## Getting your API Secret

Follow these steps to obtain your API secret:

1) Login at [Socialmetrix Quantum](https://quantum.socialmetrix.com) using Facebook or Twitter and go to **Settings**:

![Quantum Settings](quantum-settings.png)

2) Select the **API tab** and copy your API Secret:

![Quantum API Secret](quantum-settings-api-secret.png)


<aside class="warning">
Please do not expose your API Secret - if an attacker have control of your API Secret, he/she will be able to delete all your accounts. <b>Keep it safe!</b>
</aside>

## Issuing a Json Web Token

You need POST a json containing the `"method": “API-SECRET”` and your `secret`.

```shell
curl -XPOST 'https://api.quantum.socialmetrix.com/login' \
  -H "Content-Type: application/json" \
  -d '{ "method":"API-SECRET",
  "secret":"0220a22d27be69e4.........54aa9840e5c4136e"}'
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

### Response

From the response json you'll receive a lot information about the user, for authentication purposes, the most important values are:

Field | Description | Example
--------- | ----------- | -----------
**accountId** | All requests originates from an account | 790
**jwt** | The authentication token | eyJhbGc...


<aside class="notice">
The JWT issued has a lifetime of 20 days. Please login again periodically.
</aside>

<br />
### Storing JWT for convenience 
Store the value of `jwt` on a variable, so you can follow along all the next examples without having to constantly edit each line:

<code>
export <b>JWT</b>='eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJTTVgiLCJpYXQiOjE0....'<br />
export <b>ACCOUNT</b>=790
</code>
