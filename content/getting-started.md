---
title: Getting Started
weight: 3
next: features
breadcrumbs: false
draft: false
---

## Quick Start 

{{% steps %}}

### Create a Parapluie account

[🌐 You can register by clicking here ↗](#)

### Retrieve your Root Token

[🌐 You can get your token here ↗](#)

### Define your backend address

```bash
curl -X POST https://parapluie.io/some_resource \ 
  --header '{"Authorization": "Bearer $CUSTOMER_API_KEY"}' \
```

[🌐 Click here to learn more ↗](/docs/features/consumer-api-key/)



### Create a Customer API Key

```bash
curl -X POST https://parapluie.io/some_resource \ 
  --header '{"Authorization": "Bearer $CUSTOMER_API_KEY"}' \
```

[🌐 Click here to learn more ↗](/docs/features/consumer-api-key/)


### Call Parapluie endpoint

  ```bash
  curl -X POST https://parapluie.io/some_resource \ 
    --header '{"Authorization": "Bearer $CUSTOMER_API_KEY"}' \
  ```

Parapluie will decode the `$CUSTOMER_API_KEY` token and forward the request to `https://your-api.com/some_resource`.
{{% /steps %}}