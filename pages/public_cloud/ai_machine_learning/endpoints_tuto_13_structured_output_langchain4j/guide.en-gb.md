---
title: AI Endpoints - Using Structured Output with LangChain4j
excerpt: Learn how to use Structured Output with Java, LangChain4j and AI Endpoints
updated: 2025-06-17
---

> [!primary]
>
> AI Endpoints is covered by the **[OVHcloud AI Endpoints Conditions](https://storage.gra.cloud.ovh.net/v1/AUTH_325716a587c64897acbef9a4a4726e38/contracts/48743bf-AI_Endpoints-ALL-1.1.pdf)** and the **[OVHcloud Public Cloud Special Conditions](https://storage.gra.cloud.ovh.net/v1/AUTH_325716a587c64897acbef9a4a4726e38/contracts/d2a208c-Conditions_particulieres_OVH_Stack-WE-9.0.pdf)**.
>

## Objective
Objective: Explain, in a few sentences, the purpose of the guide so that our customers have an overview of its content. It usually ends up with a sentence in bold format, which is one-sentence-description of your guide (It can be the same sentence as your guide's excerpt).

In this tutorial, we will explore how to use **Structured Output** with OVHcloud AI Endpoints.

To do this, we will use **[LangChain4j](https://github.com/langchain4j/langchain4j)**, Java-based framework inspired by [LangChain](https://github.com/langchain-ai/langchain), designed to simplify the integration of LLMs (Large Language Models) into applications. Note that LangChain4j is not officially maintained by the LangChain team, despite the similar name.

Combined with OVHcloud **[AI Endpoints](https://endpoints.ai.cloud.ovh.net/)** which offers both LLM and embedding models, it becomes easy to create advanced, production-ready assistants.

![image](images/parrot.webp){.thumbnail}

## Definition

**Structured Output**: Structured output allows you to format output data in a way that makes it easier for machines to interpret and process.

## Requirements
Requirements: Detail what requirements are mandatory for the customer so that he can apply what's documented on your guide.

TODO java langchain4j JBang

## Instructions
Instructions: This is the main part of your guide's body. It will contain all the steps you will document. Sub-parts are optional but recommended if the guide is long and details several steps.

<!-- Here is an excerpt of code that shows how to define a structured output format for the responses of the language model:

Json schema definition
ResponseFormat responseFormat = ResponseFormat.builder()
         .type(ResponseFormatType.JSON)
         .jsonSchema(JsonSchema.builder()
            .name("Person")
            .rootElement(JsonObjectSchema.builder()
               .addStringProperty("name")
               .addIntegerProperty("age")
               .addNumberProperty("height")
               .addBooleanProperty("married")
               .required("name", "age", "height", "married")
            .build())
         .build())
.build(); -->

<!-- In this example, we define a JSON output format with a schema that specifies the name, age, height, and married properties as required.
Configure the model to use

This example uses the Mistral AI model hosted on OVHcloud AI Endpoints.
To configure the model, you need to set up the API key, base URL, and model name as environment variables.
Fell free to use another model, see AI Endpoints catalog.

You can find your access token, model URL, and model name in the OVHcloud AI Endpoints model dashboard.

Model definition
ChatModel chatModel = MistralAiChatModel.builder()
        .apiKey(System.getenv("OVH_AI_ENDPOINTS_ACCESS_TOKEN"))
        .baseUrl(System.getenv("OVH_AI_ENDPOINTS_MODEL_URL"))
        .modelName(System.getenv("OVH_AI_ENDPOINTS_MODEL_NAME"))
        .logRequests(false)
        .logResponses(false)
.build(); -->

### Calling the language model
<!-- 
Thanks to the JSON mode of the LLM, the response from the language model is received as a JSON string:

Model call with JSON mode
UserMessage userMessage = UserMessage.from("""
        John is 42 years old.
        He stands 1.75 meters tall.
        Currently unmarried.
        """);

ChatRequest chatRequest = ChatRequest.builder()
        .responseFormat(responseFormat)
        .messages(userMessage)
        .build();

ChatResponse chatResponse = chatModel.chat(chatRequest);

String output = chatResponse.aiMessage().text();
System.out.println("Response: \n" + output); 


// Person is a simple record: record Person(String name, int age, double height, boolean married) {}
Person person = new ObjectMapper().readValue(output, Person.class);
System.out.println(person);  -->


### The full source code

```java
///usr/bin/env jbang "$0" "$@" ; exit $?
//JAVA 21+
//PREVIEW
//DEPS dev.langchain4j:langchain4j:1.0.1 dev.langchain4j:langchain4j-mistral-ai:1.0.1-beta6

import com.fasterxml.jackson.databind.ObjectMapper;
import dev.langchain4j.data.message.UserMessage;
import dev.langchain4j.model.chat.request.ChatRequest;
import dev.langchain4j.model.chat.request.ResponseFormat;
import dev.langchain4j.model.chat.request.ResponseFormatType;
import dev.langchain4j.model.chat.request.json.JsonObjectSchema;
import dev.langchain4j.model.chat.request.json.JsonSchema;
import dev.langchain4j.model.chat.response.ChatResponse;
import dev.langchain4j.model.mistralai.MistralAiChatModel;
import dev.langchain4j.model.chat.ChatModel;

record Person(String name, int age, double height, boolean married) {
}

void main() throws Exception {
    ResponseFormat responseFormat = ResponseFormat.builder()
            .type(ResponseFormatType.JSON)
            .jsonSchema(JsonSchema.builder()
                    .name("Person")
                    .rootElement(JsonObjectSchema.builder()
                            .addStringProperty("name")
                            .addIntegerProperty("age")
                            .addNumberProperty("height")
                            .addBooleanProperty("married")
                            .required("name", "age", "height", "married")
                            .build())
                    .build())
            .build();

    UserMessage userMessage = UserMessage.from("""
            John is 42 years old.
            He stands 1.75 meters tall.
            Currently unmarried.
            """);

    ChatRequest chatRequest = ChatRequest.builder()
            .responseFormat(responseFormat)
            .messages(userMessage)
            .build();

    ChatModel chatModel = MistralAiChatModel.builder()
            .apiKey(System.getenv("OVH_AI_ENDPOINTS_ACCESS_TOKEN"))
            .baseUrl(System.getenv("OVH_AI_ENDPOINTS_MODEL_URL"))
            .modelName(System.getenv("OVH_AI_ENDPOINTS_MODEL_NAME"))
            .logRequests(false)
            .logResponses(false)
            .build();

    ChatResponse chatResponse = chatModel.chat(chatRequest);

    System.out.println("Prompt: \n" + userMessage.singleText());
    String output = chatResponse.aiMessage().text();
    System.out.println("Response: \n" + output); 

    Person person = new ObjectMapper().readValue(output, Person.class);
    System.out.println(person); 
}
```

### Running the application

```java
jbang HelloWorld.java
[jbang] Building jar for HelloWorld.java...

Prompt: 
John is 42 years old.
He stands 1.75 meters tall.
Currently unmarried.

Response: 
{"age": 42, "height": 1.75, "married": false, "name": "John"}
Person[name=John, age=42, height=1.75, married=false]
```

This code example uses JBang, a Java-based tool for creating and running Java programs as scripts.
For more information on JBang, please refer to the JBang documentation.

## Conclusion

In this article, we have seen how to use structured output with OVHcloud AI Endpoints with LangChain4J.

You've now created a Retrieval-Augmented Generation (RAG) chatbot using your own documents and the OVHcloud AI Endpoints platform. LangChain’s integration with Chroma and embedding models makes RAG implementation straightforward and even production-ready.

## Go further
Go further: This last sub-part of the guide contains at least a link to the community forum. You can also add links to relevant other guides.

<!-- If you want to have more information on AI Endpoints, please read the following blog post.
You can, also, have a look at our previous blog posts on how use AI Endpoints.

You can find the full code example in the GitHub repository. -->

<!-- If you want to go further and deploy your chatbot in the cloud, making your interface accessible to everyone, refer to the following articles and tutorials:

- [AI Deploy – Tutorial – Build & use a custom Docker image](/pages/public_cloud/ai_machine_learning/deploy_tuto_12_build_custom_image)
- [AI Deploy – Tutorial – Deploy a Gradio app for sketch recognition](/pages/public_cloud/ai_machine_learning/deploy_tuto_05_gradio_sketch_recognition)

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project. -->

## Feedback

Please feel free to send us your questions, feedback, and suggestions regarding AI Endpoints and its features:

- In the #ai-endpoints channel of the OVHcloud [Discord server](https://discord.gg/ovhcloud), where you can engage with the community and OVHcloud team members.

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project.