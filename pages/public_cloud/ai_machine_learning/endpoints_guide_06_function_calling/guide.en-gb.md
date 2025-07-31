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

To get the LLM to use those tools, first we have to declare them with JSON schemas, in a `tools` list that we will pass to the chat completion API.

Our time-tracking assistant will use two tools :
* `log_work`: log time spent on a task. Take the name of the task, category, duration and unit (minutes or hours).
  For example, to log 2 hours on documentation writing, you would call `log_work("User guide", "Documentation", 2, "hours")`
* `time_report`: get JSON data about all tasks of a given category, and the total duration, in a given time unit (minutes or hours).
  For example, to get the breakdown on time spent on coding tasks, in hours, you would call `time_report("Code", "hours")`

Here is how the tools can be declared in Python:

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

assistant_response = response.choices[0].message
print(assistant_response.to_json())
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

Now that we see that the model is able to generate tool calls, we need to code the Python implementation of the tools, so that we can process the tool calls the LLM will generate and actually start to log time!
Each task is stored in a dict, with the name as key.
Categories are a fixed list.

We define the two functions, `log_work` and `time_report`, in the Python code below:

```python
# TOOLS IMPLEMENTATION

import json
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

Now, let's see how we can process tool calls generated by the model.


```python
# this map allows us to know which Python function for a given tool
FUNCTION_MAP = {
    "log_work": log_work,
    "time_report": time_report
}

# if there are tool calls in the assistant generated response
if assistant_response.tool_calls:
    print(f"<\t{len(assistant_response.tool_calls)} tool(s) to call")
    
    # we can have several tool calls
    for tool_call in assistant_response.tool_calls:

        # The tool name should be associated with a Python function
        if tool_call.function.name in FUNCTION_MAP.keys():
            # the arguments provided by the model should be a valid JSON (in production code, this should be checked)
            function_args = json.loads(tool_call.function.arguments)
            print(f">\t\tExecute tool {tool_call.function.name} with arguments {function_args}")
            
            # execute the tool
            function_response = FUNCTION_MAP[tool_call.function.name](**function_args)

            print(function_response)
```

Output:
```
<	1 tool(s) to call
>		Execute tool log_work with arguments {'task_name': 'team meeting', 'task_category': 'Meetings', 'duration': 1, 'unit': 'hours'}
{'task': 'team meeting', 'task_category': 'Meetings', 'total_duration': 1.0}
```

We see that we successfully created a task called "team meeting", in the "Meetings" category with a total duration of 1 hour.

### Final response

### Add a system prompt

### Putting it all together

## Tips and best practices

This section contains additional tips that may improve the performance of Function Calling queries.

### Streaming

### Parallel tool calls

### Prompting

## Conclusion

In this guide, we have explained how to use Function Calling with the [AI Endpoints](https://endpoints.ai.cloud.ovh.net/) models.
We have provided a comprehensive overview of the feature which can help you perfect your integration of LLM for your own application.

## Go further

Browse the full [AI Endpoints documentation](/products/public-cloud-ai-and-machine-learning-ai-endpoints) to further understand the main concepts and get started.

To discover how to build complete and powerful applications using AI Endpoints, explore our dedicated [AI Endpoints guides](/products/public-cloud-ai-and-machine-learning-ai-endpoints).

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project.

## Feedback

Please send us your questions, feedback and suggestions to improve the service:

- On the OVHcloud [Discord server](https://discord.gg/ovhcloud)

