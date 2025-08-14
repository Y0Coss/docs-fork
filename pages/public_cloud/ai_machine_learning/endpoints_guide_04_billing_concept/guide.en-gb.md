---
title: AI Endpoints - Billing and lifecycle
excerpt: Learn how we bill AI Endpoints
updated: 2025-07-31
---

> [!primary]
>
> AI Endpoints is covered by the **[OVHcloud AI Endpoints Conditions](https://storage.gra.cloud.ovh.net/v1/AUTH_325716a587c64897acbef9a4a4726e38/contracts/48743bf-AI_Endpoints-ALL-1.1.pdf)** and the **[OVHcloud Public Cloud Special Conditions](https://storage.gra.cloud.ovh.net/v1/AUTH_325716a587c64897acbef9a4a4726e38/contracts/d2a208c-Conditions_particulieres_OVH_Stack-WE-9.0.pdf)**.
>

## Introduction

[AI Endpoints](https://endpoints.ai.cloud.ovh.net/) is a serverless platform provided by OVHcloud that offers easy access to a selection of world-renowned, pre-trained AI models. The platform is designed to be simple, secure, and intuitive, making it an ideal solution for developers who want to enhance their applications with AI capabilities without extensive AI expertise or concerns about data privacy.

## Objective

This documentation provides an overview of the billing and lifecycle management of various AI model categories offered on [AI Endpoints](https://endpoints.ai.cloud.ovh.net/). We will cover the cost structure for Large Language Models (LLM), Audio models, Image models, Embedding models, and more. Additionally, we will explain the lifecycle of our models, including model decommissioning and redirecting, ensuring that you have all the necessary information to effectively manage your AI Endpoints.

## AI Endpoints model lifecycle

OVHcloud AI Endpoints follows a model lifecycle process to ensure a seamless experience for our customers. This process includes the following steps:

- **Track model usage metrics**: We continuously monitor the usage of each model on our platform to identify underutilized or obsolete models that may no longer serve the needs of our customers.
- **Decommissioning decision**: Once a model is identified as a candidate for decommissioning, we make a decision to retire the model. At this point, we communicate the decision to our customers through official deprecation notices on our website and the #ai-endpoints channel of the OVHcloud [Discord server](https://discord.gg/ovhcloud).
- **Grace period**: After the deprecation notice is published, a grace period of 30 days is provided for all models except embedding models, which will have a grace period of 3 months. This period allows customers to transition to an alternative model. During this time, we offer guidance on recommended replacements and migration steps to ensure a smooth transition.
- **Removal from active deployment**: Once the grace period ends, the model is removed from active deployment. However, to ensure continuity, we may redirect API calls to the replacement model (if applicable) with a 10-second delay before the decommissioned model responds, signaling to users that the model is no longer in active use.
- **AI Endpoints changelog**: Decommissionings are highlighted in the [AI Endpoints Changelog](https://endpoints.ai.cloud.ovh.net/changelog), ensuring that customers are informed about the changes in the platform.

By following this model lifecycle process, OVHcloud ensures that customers are well-informed and prepared for any changes, while also maintaining a lean and up-to-date selection of AI models.

## Billing principles

Here is the model billing overview for AI Endpoints models:

| Category                   | Model                      | Input Price (\$) | Output Price (\$) | Input Price (€) | Output Price (€) | Unit Price                        |
| -------------------------- | -------------------------- | ---------------- | ----------------- | --------------- | ---------------- | --------------------------------- |
| Large Language Model (LLM) | Llama 3.3 70B Instruct     | 0.74                | 0.74                | 0.67               | 0.67               | Per 1 million tokens |
| Large Language Model (LLM) | Llama 3.1 70B Instruct     | 0.74                | 0.74                | 0.67               | 0.67               | Per 1 million tokens |
| Large Language Model (LLM) | Mixtral 8x7B Instruct v0.1 | 0.70                | 0.70                | 0.63               | 0.63               | Per 1 million tokens |
| Large Language Model (LLM) | Mistral Nemo Instruct 2407     | 0.14                | 0.14                | 0.13               | 0.13               | Per 1 million tokens |
| Large Language Model (LLM) | Llama 3.1 8B Instruct     | 0.11                | 0.11                | 0.10               | 0.10               | Per 1 million tokens |
| Large Language Model (LLM) | Mistral 7B Instruct v0.3 | 0.11                | 0.11                | 0.10               | 0.10               | Per 1 million tokens |
| Reasoning LLM | Gpt Oss 120B     | 0.00                | 0.00                | 0.00               | 0.00               | Per 1 million tokens |
| Reasoning LLM | Gpt Oss 20B     | 0.00                | 0.00                | 0.00               | 0.00               | Per 1 million tokens |
| Reasoning LLM | Qwen 3 32B     | 0.09                | 0.25                | 0.08               | 0.23               | Per 1 million tokens |
| Reasoning LLM | DeepSeek R1 Distill Llama 70B     | 0.74                | 0.74                | 0.67               | 0.67               | Per 1 million tokens |
| Code LLM | Qwen 2.5 Coder 32B Instruct | 0.96                | 0.96                | 0.87               | 0.87               | Per 1 million tokens |
| Code LLM | Mamba Codestral 7B v0.1     | 0.21                | 0.21                | 0.19               | 0.19               | Per 1 million tokens |
| Visual LLM | Mistral Small 3.2 24B Instruct 2506     | 0.10                | 0.31                | 0.09               | 0.28               | Per 1 million tokens |
| Visual LLM | Qwen 2.5 VL 72B Instruct     | 1.01                | 1.01                | 0.91               | 0.91               | Per 1 million tokens |
| Visual LLM | Llava Next Mistral 7B | 0.32                | 0.32                | 0.29               | 0.29               | Per 1 million tokens |
| Embeddings | BGE Multilingual Gemma2     | 0.01                | 0.01                | Free               | Free               | Per 1 million tokens |
| Embeddings | BGE M3 | 0.01                | 0.01                | Free               | Free               | Per 1 million tokens |
| Embeddings | BGE Base EN v1.5     | 0.01                | 0.01                | Free               | Free               | Per 1 million tokens |
| Natural Language Processing (NLP) | Roberta Base Go Emotions     | Free                | Free                | Free               | Free               | Per 1 million characters |
| Natural Language Processing (NLP) | Bert Base Multilingual uncased sentiment | Free                | Free                | Free               | Free               | Per 1 million characters |
| Natural Language Processing (NLP) | Bert Base NER     | Free                | Free                | Free               | Free               | Per 1 million characters |
| Natural Language Processing (NLP) | Bart Large CNN     | Free                | Free                | Free               | Free               | Per 1 million characters |
| Image generation | Stable Diffusion XL     | Free                | Free                | Free               | Free               | Per image |
| Audio Analysis | Whisper Large V3 Turbo | 0.00001413468                | Free                | 0.00001278               | Free               | Per second |
| Audio Analysis | Whisper Large V3 | 0.00004515798                | Free                | 0.00004083               | Free               | Per second |
| Audio Analysis | RIVA Text-to-Speech     | Free                | Free                | Free               | Free               | Per second |
| Translation | T5-Large     | Free                | Free                | Free               | Free               | Per 1 million characters |
| Computer vision | YOLOv11 Object Detection     | Free                | Free                | Free               | Free               | Per image |
| Computer vision | YOLOv11 Image Segmentation | Free                | Free                | Free               | Free               | Per image |

## Feedback

Please send us your questions, feedback and suggestions to improve the service:

- On the OVHcloud [Discord server](https://discord.gg/ovhcloud)

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project.