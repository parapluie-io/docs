---
title: Consumer API Key
draft: false
weight: 1
---

Parapluie simplifies the management of your Consumer API keys.

A Consumer API key is a confidential token that is use in all request that are made from Consumer to Parapluie's proxy. [Read more here](/parapluie/how-it-works).


It must be included in every request to Parapluie, formatted as the header: `{ Authorization: Bearer api_key_xxx }`.

You can assign various [rate limits](/parapluie/features/rate-limiting) to yourConsumer API Key. These keys can be distributed to your customers for use with your API, or used directly in your frontend application to safeguard your backend infrastructure.

## Consumer API Key management

**Prerequisite :**
Before performing any of the following action you must have :
- A parapluie [root token](/parapluie/authentication)

{{< callout emoji="🔧" >}}
For sake of documentation's clarity, parapluie's root token has been exported as an environement variable :
 `export PARAPLUIE_ROOT_TOKEN=<root_token_xxx>`
{{< /callout >}}



### Add a Consumer API keys

{{< tabs items="cURL" >}}
  {{< tab >}}
  ```bash
  curl -X POST https://parapluie.io/consumer-api-key/create \ 
    --header '{"Authorization": "Bearer $PARAPLUIE_ROOT_TOKEN"}' \
    --data '{"name":"api key for consumer XYZ"}'
  ```

  The following fields will be computed and returned :

  ```json
{
  "id":"xxx",
  "name":"api key for consumer XYZ",
  "secret":"@Str0nGS€cr3T",
  "createdAt":"2024-07-30 16:20:45"
}
  ```
    {{< /tab >}}



{{< /tabs >}}


### List Consumer API keys

{{< tabs items="cURL" >}}
  {{< tab >}}
  
```bash
  curl -X GET https://parapluie.io/consumer-api-key \ 
    --header '{"Authorization": "Bearer $PARAPLUIE_ROOT_TOKEN"}'
```

This will list the API keys with theirs `id`, `name`, `createdAt` and `lastUpdated` :

  ```json
{
  "apiKeys" : [
      {
      "consumerApiKeyId":"xxx",
      "name":"direct access for consumer XYZ",
      "createdAt":"2024-07-30T16:20:45Z",
      "lastUpdated": "2024-07-31T12:00:00Z",
      },
      {
      "consumerApiKeyId":"abc",
      "name":"Frontend app",
      "createdAt":"2024-07-28T15:42:10Z",
      "lastUpdated": "2024-07-28T15:42:10Z",
      }
    ]
}

  ```
    {{< /tab >}}

{{< /tabs >}}


### Consumer API key details

{{< tabs items="cURL" >}}
  {{< tab >}}
  ```bash
  API_KEY_ID="xxx"
  curl -X GET https://parapluie.io/consumer-api-key/$API_KEY_ID \
    --header '{"Authorization": "Bearer $PARAPLUIE_ROOT_TOKEN"}'
  ```

    The following data should be returned :

  ```json
{
  "consumerApiKeyId":"xxx",
  "name":"Consumer API key",
  "secret":"@Str0nGS€cr3T",
  "createdAt":"2024-07-30T16:20:45Z",
  "lastUpdated": "2024-07-31T12:00:00Z",
  "usage": {
      "totalRequests": 1200,
      "successfulRequests": 1180,
      "failedRequests": 20,
      "rateLimits": {
        "limit": 1000,
        "remaining": 800,
        "resetTime": "2024-08-01T00:00:00Z"
      },
      "endpoints": [
        {
          "endpoint": "/v1/resource1",
          "requests": 600,
          "successful": 590,
          "failed": 10,
          "averageResponseTimeMs": 150
        },
        {
          "endpoint": "/v1/resource2",
          "requests": 600,
          "successful": 590,
          "failed": 10,
          "averageResponseTimeMs": 200
        }
      ],
      "usageByCustomer": [
        {
          "customerId": "customer_123",
          "requests": 500,
          "successful": 495,
          "failed": 5
        },
        {
          "customerId": "customer_456",
          "requests": 700,
          "successful": 685,
          "failed": 15
        }
      ]
    }
}
  ```
    {{< /tab >}}



{{< /tabs >}}

### Delete a Consumer API key

{{< tabs items="cURL" >}}
  {{< tab >}}
  ```bash
  API_KEY_ID="xxx"
  curl -X DELETE https://parapluie.io/consumer-api-key/$API_KEY_ID \
    --header '{"Authorization": "Bearer $PARAPLUIE_ROOT_TOKEN"}'
  ```

A confirmation message will be returned : 

  ```json
{
"consumerApiKeyId":"xxx",
"message":"Consumer API key has been successfully deleted",
}
  ```
  {{< /tab >}}



{{< /tabs >}}
