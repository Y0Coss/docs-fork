---
title: AI Endpoints - Structured Output
excerpt: Learn how to use Structured Output with AI Endpoints
updated: 2025-04-28
---

> [!primary]
>
> AI Endpoints is covered by the **[OVHcloud AI Endpoints Conditions](https://storage.gra.cloud.ovh.net/v1/AUTH_325716a587c64897acbef9a4a4726e38/contracts/48743bf-AI_Endpoints-ALL-1.1.pdf)** and the **[OVHcloud Public Cloud Special Conditions](https://storage.gra.cloud.ovh.net/v1/AUTH_325716a587c64897acbef9a4a4726e38/contracts/d2a208c-Conditions_particulieres_OVH_Stack-WE-9.0.pdf)**.
>

## Introduction

[AI Endpoints](https://endpoints.ai.cloud.ovh.net/) is a serverless platform provided by OVHcloud that offers easy access to a selection of world-renowned, pre-trained AI models. The platform is designed to be simple, secure, and intuitive, making it an ideal solution for developers who want to enhance their applications with AI capabilities without extensive AI expertise or concerns about data privacy.

## Objective

This documentation provides an overview on how to use structured outputs with the various AI models offered on [AI Endpoints](https://endpoints.ai.cloud.ovh.net/). 
We will e.
The examples provided in this guide will be using the [Llama 3.3 70b model](https://endpoints.ai.cloud.ovh.net/models/c968b503-27fa-451d-b59d-1b0ff91d304d)

Visit our [Catalog](https://endpoints.ai.cloud.ovh.net/catalog) to find out which models are compatible with Structured Output.
The output formats managed by each model are defined in the Response Format section:
![Model Specs](images/image.png)

## Requirements
Requirements: Detail what requirements are mandatory for the customer so that he can apply what's documented on your guide.

The examples provided during this guide can be used with the following environments:

### Python

A [Python](https://www.python.org/) environment with the [openai client](https://pypi.org/project/openai/) and the pydantic library installed.
```sh
pip install openai pydantic
```

### Javascript

A [Node.js](https://nodejs.org/en) environment with the [request](https://www.npmjs.com/package/request) library.
Request can be installed using [NPM](https://www.npmjs.com/):
```sh
npm install request
```

### Curl

A standard terminal, with [curl](https://curl.se/) installed on the system.

### Authentication & rate limiting

All the examples provided in this guide are using the anynomous authentication which makes it simpler to use but may cause rate limiting issues.
If you wish to enable authentication using your own token, simply specify your API key within the requests.
Follow the following instructions in the [AI Endpoints - Getting Started](/pages/public_cloud/ai_machine_learning/endpoints_guide_01_getting_started) for more information on authentication.

## Instructions

Structured output is a very powerful feature that allows...

Under the hood, structured output is usually made possible with combination of:
- specific examples used during model training
- runtime guided decoding, with backend such as [outlines](https://github.com/dottxt-ai/outlines), [xgrammar](https://github.com/mlc-ai/xgrammar), or [lm-format-enforcer](https://github.com/noamgat/lm-format-enforcer)
TODO: link literature ?


### How to use

The `response_format` parameter of the Chat Completion API allows us to enable and configure the Structured Output features.
Models that support structured output can manage the three following modes:

- `{"type": "text"}`
The default textual format. This is the same as specifying no `response_format`.

- `{"type": "json_object"}`
The JSON object format is a legacy format that was introduced with the first iteration of Structured Outputs.
This mode is non-deterministic and allows the model to output a JSON object without strict validation.

- `{"type": "json_schema", "json_schema": .. }`
[JSON schema](https://json-schema.org/) is a very powerful tool used to specify and validate a JSON data structure.
This latest kind of response_format allows us to enforce custom output formats in LLM outputs using this specification and ensure consistency and interoperability with a variety of platforms and applications.
When using the JSON schema mode, outputs are deterministic and will always adhere to the schema specified.

We recommend using JSON schema over JSON object whenever possible.

### JSON schema

The following code samples provide a simple example on how to specify a JSON schema, using the `response_format` parameter.

> [!tabs]
> **Python**
>> For this example, we can use the openai Python library, combined with pydantic for powerful JSON schema management. 
>>
>> ```python
>> from pydantic import BaseModel
>> import json
>> import openai
>> import os
>> 
>> # Define the prompts
>> messages = [
>>     { "content": "You are a helpful assistant that help users rank different things. You always answer in JSON format.", "role": "system" },
>>     { "content": "What are the top 3 most popular programming languages ?", "role": "user" }
>> ]
>> 
>> # Define the data model
>> class Language(BaseModel):
>>     name: str
>>     website: str
>>     ranking: int
>> 
>> class LanguageRankings(BaseModel):
>>     languages: list[Language]
>> 
>> # Initialise the client
>> api_key = os.environ['AI_ENDPOINT_API_KEY'] # Assuming your API key is available in this environment variable (export AI_ENDPOINT_API_KEY='your_api_key')
>> openai_client = openai.OpenAI(
>>     base_url='https://llama-3-3-70b-instruct.endpoints.kepler.ai.cloud.ovh.net/api/openai_compat/v1',
>>     api_key=api_key
>> )
>> 
>> # Optionally, print the json schema infered from the pydantic model
>> print(f'JSON schema: {LanguageRankings.model_json_schema()}')
>> 
>> # Run the query
>> response = openai_client.beta.chat.completions.parse(
>>     model='Meta-Llama-3_3-70B-Instruct',
>>     messages=messages,
>>     response_format=LanguageRankings,
>>     temperature=0 # Ensure deterministic output for this guide's purpose
>> )
>> 
>> # Print the parsed response
>> language_rankings = response.choices[0].message.parsed
>> for language in language_rankings.languages:
>>     print(f"{language.name} is the n°{language.ranking} language ({language.website})")
>> ```
>>
>> Output:
>> ```sh
>> JSON schema: {'$defs': {'Language': {'properties': {'name': {'title': 'Name', 'type': 'string'}, 'website': {'title': 'Website', 'type': 'string'}, 'ranking': {'title': 'Ranking', 'type': 'integer'}}, 'required': ['name', 'website', 'ranking'], 'title': 'Language', 'type': 'object'}}, 'properties': {'languages': {'items': {'$ref': '#/$defs/Language'}, 'title': 'Languages', 'type': 'array'}}, 'required': ['languages'], 'title': 'LanguageRankings', 'type': 'object'}
>> JavaScript is the n°1 language (https://www.javascript.com/)
>> Python is the n°2 language (https://www.python.org/)
>> Java is the n°3 language (https://www.java.com/)
>> ```
>>
>> NOTE: this example is using `openai_client.beta.chat.completions.parse` to leverage automatic parsing with pydantic, but it is also possible to use `openai_client.chat.completions.create`, by using the `response_format` parameter and specifying the JSON schema manually.
>>
> **Curl**
>>
>> Input query:
>> ```sh
>> curl -X POST "https://llama-3-3-70b-instruct.endpoints.kepler.ai.cloud.ovh.net/api/openai_compat/v1/chat/completions" \
>>     -H 'accept: application/json'\
>>     -H 'content-type: application/json' \
>>     -d '{
>>         "max_tokens":100,
>>         "messages": [
>>             { "content": "You are a helpful assistant that help users rank different things. You always answer in JSON format.", "role": "system" },
>>             { "content": "What are the top 3 most popular programming languages ?", "role": "user" }
>>         ],
>>         "response_format": {
>>             "type":"json_schema",
>>             "json_schema": {
>>                 "name": "LanguageRankings",
>>                 "schema": {
>>                     "$defs": {},
>>                     "properties": {
>>                         "languages": {
>>                             "title": "Languages",
>>                             "type": "array",
>>                             "items": {
>>                                 "type": "object",
>>                                 "properties": {
>>                                     "name": {
>>                                         "title": "Name",
>>                                         "type": "string"
>>                                     },
>>                                     "website": {
>>                                         "title": "Website",
>>                                         "type": "string"
>>                                     },
>>                                     "ranking": {
>>                                         "title": "Ranking",
>>                                         "type": "number"
>>                                     }
>>                                 },
>>                                 "required": ["name", "website", "ranking"]
>>                             }
>>                         }
>>                     },
>>                     "required": ["languages"],
>>                     "title": "LanguageRankings",
>>                     "type": "object"
>>                 }
>>             }
>>         },
>>         "temperature": 0
>>     }' 
>> ```
>>
>> Output response:
>> ```sh
>> {"id":"chatcmpl-9276e3e305e04c73bd05224abcb7532b","object":"chat.completion","created":1750772047,"model":"Meta-Llama-3_3-70B-Instruct","choices":[{"index":0,"message":{"role":"assistant","content":"{\"languages\": [\n    {\"name\": \"JavaScript\", \"ranking\": 1, \"website\": \"https://www.javascript.com/\"},\n    {\"name\": \"Python\", \"ranking\": 2, \"website\": \"https://www.python.org/\"},\n    {\"name\": \"Java\", \"ranking\": 3, \"website\": \"https://www.java.com/\"}\n]}"},"finish_reason":"stop","logprobs":null}],"usage":{"prompt_tokens":65,"completion_tokens":80,"total_tokens":145}}
>> ```
>>
>> As we can see, the response is matching the expected JSON schema, and OVHcloud is the n°1 European cloud provider! 
>>
> **Javascript**
>>
>> ```javascript
>> const request = require('request');
>> const fs = require('fs');
>> 
>> // Define the prompts
>> const messages = [
>>     { content: "You are a helpful assistant that help users rank different things. You always answer in JSON format.", role: "system" },
>>     { content: "What are the top 3 most popular programming languages ?", role: "user" }
>> ];
>> 
>> // Define the JSON schema
>> const jsonSchema = {
>>     "name": "LanguageRankings",
>>     "schema": {
>>         "$defs": {},
>>         "properties": {
>>             "languages": {
>>                 "title": "Languages",
>>                 "type": "array",
>>                 "items": {
>>                     "type": "object",
>>                     "properties": {
>>                         "name": {
>>                             "title": "Name",
>>                             "type": "string"
>>                         },
>>                         "website": {
>>                             "title": "Website",
>>                             "type": "string"
>>                         },
>>                         "ranking": {
>>                             "title": "Ranking",
>>                             "type": "number"
>>                         }
>>                     },
>>                     "required": ["name", "website", "ranking"]
>>                 }
>>             }
>>         },
>>         "required": ["languages"],
>>         "title": "LanguageRankings",
>>         "type": "object"
>>     }
>> };
>> 
>> // Initialise the client
>> const apiKey = process.env.AI_ENDPOINT_API_KEY; // Assuming your API key is available in this environment variable (export AI_ENDPOINT_API_KEY='your_api_key')
>> const options = {
>>     url: 'https://llama-3-3-70b-instruct.endpoints.kepler.ai.cloud.ovh.net/api/openai_compat/v1/chat/completions',
>>     headers: {
>>         'Content-Type': 'application/json',
>>         'Authorization': `Bearer ${apiKey}`
>>     },
>>     json: true,
>>     body: {
>>         messages: messages,
>>         response_format: {
>>             type: 'json_schema',
>>             json_schema: jsonSchema
>>         },
>>         temperature: 0
>>     }
>> };
>> 
>> // Run the query
>> request.post(options, (error, response, body) => {
>>     if (!error && response.statusCode == 200) {
>>         const languageRankigs = body.choices[0].message.content;
>>         console.log(languageRankigs)
>>         const parsedLanguageRankings = JSON.parse(languageRankigs);
>>         parsedLanguageRankings.languages.forEach(language => {
>>             console.log(`${language.name} is the n°${language.ranking} most popular language (${language.website})`);
>>         });
>>     } else {
>>         console.error('Error:', error);
>>         console.error('Response:', response.body);
>>     }
>> });
>> ```
>>
>> Output:
>> ```sh
>> {"languages": [
>>     {"name": "JavaScript", "ranking": 1, "website": "https://www.javascript.com/"},
>>     {"name": "Python", "ranking": 2, "website": "https://www.python.org/"},
>>     {"name": "Java", "ranking": 3, "website": "https://www.java.com/"}
>> ]}
>> JavaScript is the n°1 most popular language (https://www.javascript.com/)
>> Python is the n°2 most popular language (https://www.python.org/)
>> Java is the n°3 most popular language (https://www.java.com/)
>> ```
>>
>> This example shows us how to use the JSON schema response format with Javascript.

### JSON object

TODO

### Tips and best practices

This section contains useful tips that may improve the performance of Structured Output queries.

#### Streaming

All kinds of response_format are compatible with streaming. To enable streaming, simply use `"streaming": true"` in your request's body and process the streaming response appropriately.

TODO example queries

#### Schema definition

key ordering -> equation example
subset of json schema specs, anyof, etc... -> not all of them - limitation
required fields
additional properties: false
We encourage users to experiment with different variations of their JSON schemas to reach the best performance.

#### Refusal management

Some models may refusal (TODO: can we manage this?)

#### Prompting & additional parameters

-> generally better to ask for json in both json modes
-> Tend to perform better with lower temperature (and top_p ? <- verify this)
-> check model specifics TODO huggingface example


## Conclusion

In this guide, we have explained how to use Structured Output with the [AI Endpoints](https://endpoints.ai.cloud.ovh.net/) models.
We have provided a comprehensive overview of the feature which can help you perfect your integration of LLM for your own application.

## Go further

Browse the full [AI Endpoints documentation](/products/public-cloud-ai-and-machine-learning-ai-endpoints) to further understand the main concepts and get started.

To discover how to build complete and powerful applications using AI Endpoints, explore our dedicated [AI Endpoints guides](/products/public-cloud-ai-and-machine-learning-ai-endpoints).

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project.

## Feedback

Please send us your questions, feedback and suggestions to improve the service:

- On the OVHcloud [Discord server](https://discord.gg/ovhcloud)

