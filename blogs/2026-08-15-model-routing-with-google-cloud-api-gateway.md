---
title: "Model routing with Google Cloud API Gateway"
url: "https://developers.googleblog.com/a-unified-api-for-ai-model-routing/"
date: "2026-08-15"
feed_url: "https://developers.googleblog.com/feed/"
---
Google Cloud API Gateway now offers a model routing feature in Public Preview, allowing developers to dynamically route traffic to models like Gemini, Claude, or OpenAI OSS-GPT without hardcoding endpoints or managing open-source proxies. Developers can easily configure these routing rules directly within their OpenAPI 3.x specifications by mapping virtual model names to specific backend targets on a shared host. Once deployed, the Gateway acts as a serverless ingress layer that accepts standard OpenAI-compatible requests, automatically transcodes the payload to the native schema of the target
