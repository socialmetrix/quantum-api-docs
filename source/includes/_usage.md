
# Usage

## Limits info

```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}/limits/available" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
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

This endpoint details the account's limits according to the user's plan. Here you can see how many campaigns, projects, profiles, swaps, users and fans fans the account currently has. 


### HTTP Request

`GET '/accounts/<ACCOUNT>/limits/available'`

### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT** | The ID obtained from JWT response: `user.accountId` | 790
**PROJECT** | Current Project | 0

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
**users** | Number of **users** in the selected period. | 2
**campaigns** | Number of **campaigns** in the selected period. | 2
**projects** | Number of **projects** in the selected period. | 172184
**profiles** | Number of **profiles** in the selected period. | 6
**swaps** | Number of profile changes that can be done on the project. Each account has a swaps limit per month. | 2
**fans** |  Number of **fans** in the selected period. | 65000



## Billing info


```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}/billing-info" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
```

> The above command returns JSON structured like this:

```json
{   
  "accountId": ACCOUNT,
  "isTrial": true,
  "currentBillingAmountInCents": 9900,
  "currentPeriodStart": "2016-10-07T22:22:15",
  "currentPeriodEnd": "2016-10-21T22:22:15",
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

 This endpoint gives you all the billing information available. Here you can check whether or not the account is on its Trial period, the current billing amount in cents, the current period start and end, when is the next billing, and the plan that is currently active. 
 
 
### HTTP Request

`GET '/accounts/<ACCOUNT>/billing-info'`

### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT** | The ID obtained from JWT response: `user.accountId` | 790
**PROJECT** | Current Project | 0

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
**isTrial** | Whether the account is it's **trial** period. | True/False
**currentBillingAmountInCents** | The current **billing amount** showed in cents. | 9900
**currentPeriodStart** | **Starting date** of the current payment period. | 2016-10-07T22:22:15
**currentPeriodEnd** | **Ending date** of the current payment period.  | 2016-10-07T22:22:15
**coupon** | Available **coupons** for the account. | 0.0041750576
**pendingCancellation** | Whether there is a pending **cancellation request** waiting to be completed. | True/False
**nextPlan** | Downgrades or upgrades of the account | Upgrade
**paymentType** | **Payment Type** selected for the account. | Credit Card

 
 
## Consumed limits info



```shell
curl -XGET "https://api.quantum.socialmetrix.com/v1/accounts/${ACCOUNT}/limits/consumed" \
  -H "Content-Type: application/json" \
  -H "X-Auth-Token: ${JWT}"
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

 This endpoint details everything that has been consumed by the account. It gives the number of  users, campaigns, swaps, projects, profiles and fans created by the account.  
 
 
### HTTP Request

`GET '/accounts/<ACCOUNT>/limits/consumed'`

### URL Parameters

Parameter | Description | Example
--------- | ----------- | -----------
**ACCOUNT** | The ID obtained from JWT response: `user.accountId` | 790
**PROJECT** | Current Project | 0

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
**users** | Number of **users** in the selected period. | 2
**campaigns** | Number of **campaigns** in the selected period. | 2
**projects** | Number of **projects** in the selected period. | 172184
**profiles** | Number of **profiles** in the selected period. | 6
**swaps** | Number of profile changes that can be done on the project. Each account has a swaps limit per month. | 2
**fans** |  Number of **fans** in the selected period. | 65000
 

