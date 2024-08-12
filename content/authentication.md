---
title: Authentication
weight: 2
breadcrumbs: false
draft: true
---

Parapluie uses two special token called the **Parapluie Root Token** and the **Consumer API Key**.

It is essential to distinguish between the Parapluie Root Token and a Consumer API key, as they serve different purposes and are used in different contexts. You will find [on this page](/parapluie/how-it-works) a sequence datagram showing how those tokens work together.

## Parapluie Root Token

The Parapluie Root Token is used for administrative actions within the Parapluie platform, such as creating or managing resources, like rate limits or Consumer API Keys.

## Consumer API Key

A [Consumer API Key](/parapluie/features/consumer-api-key) is a token that is used between a Consumer (a customer of you or your frontend application) and Parapluie. This Consumer API Key is then processed by Parapluie to understand if the query should be forwarded to your backend API.