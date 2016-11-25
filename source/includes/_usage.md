# Usage

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