---
title: AI Endpoints - Function Calling
excerpt: Learn how to use Function Calling with OVHcloud AI Endpoints
updated: 2025-07-16
---

> [!primary]
>
> AI Endpoints is covered by the **[OVHcloud AI Endpoints Conditions](https://storage.gra.cloud.ovh.net/v1/AUTH_325716a587c64897acbef9a4a4726e38/contracts/48743bf-AI_Endpoints-ALL-1.1.pdf)** and the **[OVHcloud Public Cloud Special Conditions](https://storage.gra.cloud.ovh.net/v1/AUTH_325716a587c64897acbef9a4a4726e38/contracts/d2a208c-Conditions_particulieres_OVH_Stack-WE-9.0.pdf)**.
>

## Introduction

[AI Endpoints](https://endpoints.ai.cloud.ovh.net/) is a serverless platform provided by OVHcloud that offers easy access to a selection of world-renowned, pre-trained AI models. The platform is designed to be simple, secure, and intuitive, making it an ideal solution for developers who want to enhance their applications with AI capabilities without extensive AI expertise or concerns about data privacy.

**Function Calling**, also named tool calling, is a feature that enables a large language model (LLM) to trigger user-defined functions (also named tools). These tools are defined by the developer and implement specific behaviors such as calling an API, fetching data or calculating values, which extends the capabilities of the LLM.

The LLM will identify which tool(s) to call and the arguments to use.
This feature can be used to develop assistants or agents for instance.

## Objective

This documentation provides an overview on how to use function calling with the AI models offered on [AI Endpoints](https://endpoints.ai.cloud.ovh.net/).
The examples provided in this guide will be using the [Mistral-Nemo-Instruct-2407](https://endpoints.ai.cloud.ovh.net/models/mistral-nemo-instruct-2407) model.

Visit our [Catalog](https://endpoints.ai.cloud.ovh.net/catalog) to find out which models are compatible with Function Calling.

## Requirements

We use Python for the examples provided through this guide.

Make sure you have a [Python](https://www.python.org/) environment configurer, and install the [openai client](https://pypi.org/project/openai/).
```sh
pip install openai
```

### Authentication & rate limiting

All the examples provided in this guide are using the anonymous authentication which makes it simpler to use but may cause rate limiting issues.
If you wish to enable authentication using your own token, simply specify your API key within the requests.
Follow the following instructions in the [AI Endpoints - Getting Started](/pages/public_cloud/ai_machine_learning/endpoints_guide_01_getting_started) for more information on authentication.

## Function Calling overview

The workflow to use function calling is described below:
1. **Define tools**: tell the model what tools it can use, with a JSON schema for each tool
2. **Process tools calls**: for each tool calls eventually returned by the model, execute the actual implementation of the tool in your code, using the name and arguments provided
3. **Final response**: call the model with the updated conversation, containing the results of the tools calls, so that the model can generate a final answer

![Function calling workflow](images/function_calling_workflow.png)

## Example: a time-tracking assistant

To illustrate the use of function calling and progressively introduce the important notions related to this feature, we are going to develop a time-tracking assistant, step-by-step.

The assistant will be able to:
* log time spent on a task
* generate a time report

Each task has a name, category and total duration in minutes. Categories are a fixed list of strings, for example "Code" or "Meetings".
A time report can be generated for a category of task.

The user will be able to interact with the assistant to log time and get information about how time was spent.

### Define tools

Our time-tracking assistant will use two tools :
* `log_work`: log time spent on a task. Take the name of the task, category, duration and unit (minutes or hours).
For example, to log 2 hours on documentation writing, you would call `log_work("User guide", "Documentation", 2, "hours")`
* `time_report`: get a JSON with data about all tasks of a given category, and the total duration, in a given time unit (minutes or hours).
For example, to get the breakdown on time spent on coding tasks, in hours, you would call `time_report("Code", "hours")`

To get the LLM to use those tools, first we have to declare them with JSON schemas, in a `tools` list that we will pass to the chat completion API.

```python
# TOOLS DECLARATION (JSON SCHEMA)
# Possible Categories (we'll reuse this later)
CATEGORIES = ["Code", "Meetings", "Documentation", "Other"]

# Define the tool specification
TOOLS = [
    {
        "type": "function",
        "function": {
            "name": "log_work",
            "description": "Logs a work session for a specific task by providing a start and end datetime.",
            "parameters": {
                "type": "object",
                "properties": {
                    "task_name": {
                        "type": "string",
                        "description": "The name of the task to log work for."
                    },
                    "task_category": {
                        "type": "string",
                        "enum": CATEGORIES,
                        "description": "The category of the task to log work for."
                    },
                    "duration": {
                        "type": "number",
                        "description": "The duration to log work for."
                    },
                    "unit": {
                        "type": "string",
                        "enum": ["minutes", "hours"],
                        "description": "The time unit to log work in."
                    }
                },
                "required": ["task_name", "task_category", "duration", "unit"]
            }
        }
    },
    {
        "type": "function",
        "function": {
            "name": "time_report",
            "description": "Output a JSON with the breakdown of time spent by each task of a given category, returned in a given time unit.",
            "parameters": {
                "type": "object",
                "properties": {
                    "category": {
                        "type": "string",
                        "description": "The name of the category to get the report for."
                    },
                    "unit": {
                        "type": "string",
                        "enum": ["minutes", "hours"],
                        "description": "The time unit to return the result in."
                    }
                },
                "required": ["category", "unit"]
            }
        }
    }
]
```

### Generate tool calls

With our tools ready, we can now try to call the model and see if it understands our tools definition.
We use the OpenAI Python SDK to call the ``/v1/chat/completions`` route on the endpoint, passing the tools definition in the `tools` parameter.

Let's send a simple user message: `log 1 hour team meeting` and see what the model answers.

```python
import os
from openai import OpenAI

MODEL_NAME = "Mistral-Nemo-Instruct-2407"
API_KEY = os.environ.get("OVH_AI_ENDPOINTS_API_KEY")

# Initialize the OpenAI client
client = OpenAI(
    base_url="https://oai.endpoints.kepler.ai.cloud.ovh.net/v1",
    api_key=API_KEY
)

messages = [
    {"role": "user", "content": "log 1 hour team meeting"}
]
response = client.chat.completions.create(
    model=MODEL_NAME,
    messages=messages,
    tools=TOOLS,
    tool_choice="auto",
    temperature=0.15
)

print(response.choices[0].message.to_json())
```

Output:
```json
{
  "role": "assistant",
  "tool_calls": [
    {
      "id": "wuvyeH6fR",
      "function": {
        "arguments": "{\"task_name\": \"team meeting\", \"task_category\": \"Meetings\", \"duration\": 1, \"unit\": \"hours\"}",
        "name": "log_work"
      },
      "type": "function"
    }
  ]
}
```

The `tool_calls` output list contains the tool calls the model generated in response to our user message.
We see that the model has successfully understood our query and generated the appropriate tool call.
The `name` and `arguments` fields tells us which tool to call and which parameters to pass to the function.
The `id` is an unique identifier for this tool call, that we will need later on.

Under the hood, the model has recognized that the user intent was related to the set of tools given, and generated a sequence of specific tokens that were post-processed to create a tool call object.

About the `tool_choice` parameter:
You've noticed that we used the `auto` mode in our request to the endpoint.
Here are the available values for this parameter and the impact on the output.

| `tool_choice` value | Effect                                                                                                                                                                                                              |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `auto`              | Default mode when tools are defined, the model generates 0 to N tool calls.                                                                                                                                         |
| `required`          | Force the model to generate at least 1 tool call, using structured outputs.                                                                                                                                         |
| named function      | Force the model to generate at least 1 tool call to the given function.<br/>For example, to force the model to call the `log_work` tool:<br/>`tool_choice = {"type": "function", "function": {"name": "log_work"}}` |
| `none`              | No tool calls generated.                                                                                                                                                                                            |


### Process tools calls

Now that we see that the model is able to generate tool calls, we need to code the actual Python implementation of the tools, so that we can process the tool calls the LLM will generate.
Each task is stored in a dict, with the name as key.
Categories are a fixed list.

```python
# TOOLS IMPLEMENTATION

import json
import os
from dataclasses import dataclass

# We store tasks by their names
TASKS_BY_NAME = {}

# A task has a name, category, and total duration in minutes
# When we log a new work entry for a task, we add to this total duration
@dataclass
class Task:
    name: str
    category: str
    duration_minutes: float = 0.0

    def add_entry(self, duration:float, unit:str):
        self.duration_minutes += to_minutes(duration, unit)

    def __str__(self):
        return json.dumps({"name": self.name, "category": self.category, "total_duration": self.duration_minutes})


# TOOL 1 : log a work entry (task name, category, duration and unit = minutes or hours)
def log_work(task_name: str, task_category: str, duration: float, unit: str):
    # we create a new task if the name doesn't exist yet
    if task_name not in TASKS_BY_NAME:
        TASKS_BY_NAME[task_name] = Task(task_name, task_category)

    task = TASKS_BY_NAME.get(task_name)
    task.add_entry(duration=float(duration), unit=unit)

    # the tool returns the data for the created or updated task, so that the model can use this information if needed
    return {"task": task.name, "task_category": task_category, "total_duration": convert(task.duration_minutes, unit)}

# TOOL 2 : get JSON data about a tasks in a given category, and total duration (category, unit = minutes or hours)
def time_report(category: str, unit: str):
    data = [{"name":t.name, "total_duration":convert(t.duration_minutes, unit)} for t in TASKS_BY_NAME.values() if t.category == category]
    data.append({"total_duration_for_category": sum([x["total_duration"] for x in data])})
    return data

# Utilities function: convert to and from minutes and hours
def convert(duration_min: float, unit: str) -> float:
    if unit == "minutes":
        return duration_min
    elif unit == "hours":
        return duration_min / 60
    else:
        raise ValueError("Invalid unit. Must be 'minutes', or 'hours'.")

def to_minutes(duration: float, unit: str) -> float:
    if unit == "minutes":
        return duration
    elif unit == "hours":
        return duration * 60
    else:
        raise ValueError("Invalid unit. Must be 'minutes', or 'hours'.")
```


### Final response

The following code samples provide a simple example on how to specify a JSON schema, using the `response_format` parameter.

> [!tabs]
> **Python**
>> For this example, we can use the openai Python library, combined with pydantic for powerful JSON schema management. 
>>
>> ```python
>> from pydantic import BaseModel
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
>>         const languageRankings = body.choices[0].message.content;
>>         console.log(languageRankings)
>>         const parsedLanguageRankings = JSON.parse(languageRankings);
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

The following code samples provide a simple example on how to use the legacy JSON object mode, using the `response_format` parameter.
Note that when using the JSON object mode, we cannot explicitly specify the schema of the output.

> [!tabs]
> **Python**
>>
>> ```python
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
>> # Initialise the client
>> api_key = os.environ['AI_ENDPOINT_API_KEY'] # Assuming your API key is available in this environment variable (export AI_ENDPOINT_API_KEY='your_api_key')
>> openai_client = openai.OpenAI(
>>     base_url='https://llama-3-3-70b-instruct.endpoints.kepler.ai.cloud.ovh.net/api/openai_compat/v1',
>>     api_key=api_key
>> )
>> 
>> # Run the query
>> response = openai_client.chat.completions.create(
>>     model='Meta-Llama-3_3-70B-Instruct',
>>     messages=messages,
>>     response_format={
>>         "type": "json_object",
>>     },
>>     temperature=0 # Ensure deterministic output for this guide's purpose
>> )
>> 
>> # Print the response
>> output = json.loads(response.choices[0].message.content)
>> print(json.dumps(output, indent=2))
>> ```
>>
>> Output:
>> ```sh
>> {
>>   "rank": [
>>     {
>>       "position": 1,
>>       "language": "JavaScript",
>>       "popularity": "94.5%"
>>     },
>>     {
>>       "position": 2,
>>       "language": "HTML/CSS",
>>       "popularity": "83.6%"
>>     },
>>     {
>>       "position": 3,
>>       "language": "Python",
>>       "popularity": "78.9%"
>>     }
>>   ]
>> }
>> ```
>>
> **Curl**
>>
>> Input query:
>> ```sh
>> curl -X POST "https://llama-3-3-70b-instruct.endpoints.kepler.ai.cloud.ovh.net/api/openai_compat/v1/chat/completions" \
>>     -H 'accept: application/json' \
>>     -H 'content-type: application/json' \
>>     -d '{
>>         "model": "Meta-Llama-3_3-70B-Instruct",
>>         "max_tokens": 100,
>>         "messages": [
>>             { "content": "You are a helpful assistant that help users rank different things. You always answer in JSON format.", "role": "system" },
>>             { "content": "What are the top 3 most popular programming languages ?", "role": "user" }
>>         ],
>>         "response_format": {
>>             "type": "json_object"
>>         },
>>         "temperature": 0
>>     }'
>> ```
>>
>> Output:
>> ```sh
>> {"id":"chatcmpl-dfdbf074ab864199bac48ec929179fed","object":"chat.completion","created":1750773314,"model":"Meta-Llama-3_3-70B-Instruct","choices":[{"index":0,"message":{"role":"assistant","content":"{\"rank\": [\n    {\"position\": 1, \"language\": \"JavaScript\", \"popularity\": \"94.5%\"},\n    {\"position\": 2, \"language\": \"HTML/CSS\", \"popularity\": \"93.2%\"},\n    {\"position\": 3, \"language\": \"Python\", \"popularity\": \"87.3%\"}\n]}"},"finish_reason":"stop","logprobs":null}],"usage":{"prompt_tokens":65,"completion_tokens":77,"total_tokens":142}}%
>> ```
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
>>             type: 'json_object',
>>         },
>>         temperature: 0
>>     }
>> };
>> 
>> // Run the query
>> request.post(options, (error, response, body) => {
>>     if (!error && response.statusCode == 200) {
>>         const languages = body.choices[0].message.content;
>>         const parsedData = JSON.parse(languages);
>>         console.log(parsedData)
>>     } else {
>>         console.error('Error:', error);
>>         console.error('Response:', response.body);
>>     }
>> });
>> ```
>>
>> Output:
>> ```sh
>> {
>>   rank: [
>>     { position: 1, language: 'JavaScript', popularity: '94.5%' },
>>     { position: 2, language: 'HTML/CSS', popularity: '87.4%' },
>>     { position: 3, language: 'Python', popularity: '83.8%' }
>>   ]
>> }
>> ```

### Tips and best practices

This section contains additional tips that may improve the performance of Structured Output queries.

#### Streaming

All kinds of response_format are compatible with streaming. To enable streaming, simply use `"streaming": true` in your request's body and process the stream accordingly.

Example with python:
```python
from pydantic import BaseModel
import openai
import os

# Define the prompts
messages = [
    { "content": "You are a helpful assistant that help users rank different things. You always answer in JSON format.", "role": "system" },
    { "content": "What are the top 3 most popular programming languages ?", "role": "user" }
]

# Define the data model
class Language(BaseModel):
    name: str
    website: str
    ranking: int

class LanguageRankings(BaseModel):
    languages: list[Language]

# Initialise the client
api_key = os.environ['AI_ENDPOINT_API_KEY'] # Assuming your API key is available in this environment variable (export AI_ENDPOINT_API_KEY='your_api_key')
openai_client = openai.OpenAI(
    base_url='https://llama-3-3-70b-instruct.endpoints.kepler.ai.cloud.ovh.net/api/openai_compat/v1',
    api_key=api_key
)

# Run the query
with openai_client.beta.chat.completions.stream(
    model='Meta-Llama-3_3-70B-Instruct',
    messages=messages,
    response_format=LanguageRankings,
    temperature=0,
) as stream:
    for event in stream:
        if event.type == "response.refusal.delta":
            print(event.delta, end="")
        elif event.type == "response.output_text.delta":
            print(event.delta, end="")
        elif event.type == "response.error":
            print(event.error, end="")
        elif event.type == "response.completed":
            print("Completed")
        elif event.type == "chunk":
            if len(event.chunk.choices):
                print(event.chunk.choices[0].delta.content, end="")

    response = stream.get_final_completion()

# Print the parsed response
language_rankings = response.choices[0].message.parsed
for language in language_rankings.languages:
    print(f"{language.name} is the n°{language.ranking} language ({language.website})")
```

Streamed output response:
```sh
{"languages": [
    {"name": "JavaScript", "ranking": 1, "website": "https://www.javascript.com/"},
    {"name": "Python", "ranking": 2, "website": "https://www.python.org/"},
    {"name": "Java", "ranking": 3, "website": "https://www.java.com/"}
]}
JavaScript is the n°1 language (https://www.javascript.com/)
Python is the n°2 language (https://www.python.org/)
Java is the n°3 language (https://www.java.com/)
```

#### Schema definition

Some considerations about the JSON schema definition:
- Structured output currently supports a subset of the [JSON schema specification](https://json-schema.org/specification). Some features may not be compatible.
- The models will generate the output following alphabetical order of the JSON schema keys. It may be useful to rename your fields to enforce a specific order during generation.
- To avoid divergence, we recommend setting [additional properties](https://json-schema.org/understanding-json-schema/reference/object#additionalproperties) to `false` and explicity setting the [required fields](https://json-schema.org/learn/getting-started-step-by-step#define-required-properties)

Don't hesitate to experiment with different variations of your JSON schemas to reach the best performance!

#### Prompting & additional parameters

Some additional considerations regarding prompts and model parameters:
- Even though the response_format can be used to enable structured outputs, models can generally perform better when asked to produce json outputs within the prompt (`messages` field).
- Most models tend to perform better when using lower temperature for structured outputs.
- Some model providers may recommend specific system prompts and parameters to use for structured outputs and function calling. Don't hesitate to visit the model pages to dive deeper into model specifics ([example for Llama 3.3 on HuggingFace](https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct)).

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

