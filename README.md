# Pydantic for LLM Applications

1. [Introduction](#1)
2. [Pydantic fundamentals](#2)


## Introduction

- We can use Pydantic to get structured output from an LLM through leveraging data validations that can be used in any software systems. 
- Like we can get output from an LLM in an exact format I need or to validate the LLM response
- In general, LLM produces free-form text but when we build LLM into a larger software system where we have multiple components and we want to pass the data we are getting from LLM to the system's next component in a predictable way --> We need to get the structured output using Pydantic
- So getting the structured output can be very helpful to be able to amke a good decision on  the next good step like for example if the request coming from a user being passed to an LLM, if we have a structured output we may manage the request in a wise way like we can have it as a support ticket that requires a human attention or passing it to another LLM which calls a tool like FAQ lookup tool
- We can use different methods to get structured responses from LLM and also validate those responses
- We can validate data in any software system, like data that can be put into a system by humans or external APIs and data sources or any data that can be passed from one component to another in a software system 

## Why we need Pydantic 

The response from LLM may have additional text like **"Here is the JSON output you requested!"** or it may add some other formatting like **triple backticks markdown formatting** which is really common in LLM responses when we are asking for JSON. Betond these, the LLM response may not contain all the fields we expect or could end up being in a fromat which may not be useable. So these unpredactibality of the response format makes it really hard to rely on LLMs to directly provide us with a structured output. This is Pydantic may come to rescue

- With Pydantic we can define a **Pydantic data model**, that specify the data structure and type we expect like:

![](https://github.com/DanialArab/images/blob/main/Pydantic_for_LLM_applications/pydantic_data_model.png)

With Pydantic data model, we define both field names and data types for each field in the model. We can use this Pydantic data model to validate the LLM response to ensure it matches our expectations. 

We have two ways to get structured outputs from LLM:
1. The simplest way is to prompt the LLM to give us the structured output through giving it an example of the preferred structure in the prompt, and then take that LLM response which we hope to be in JSON fromat and attepmts to craete an instance of the data model like the CustomerQuery data model in the above screenshot. We use LLM response as input like:

    valid_data = CustomerQuery.model_validate_json(JSON_LLM_output)

If the LLM response contains unexpected text or formatting or if the JSON itself is not properly formatted then there would be a failure with validation error. On the other hand, if the JSON format is valid but the data contained int he JSON does not match the model then agin there would eb a failure with Data Validation error. If no error pops in means that data validation is passed and the validated data can be safely passed to the next component in the system. But if there is an error and data is not validated, we can simply catch that validation error and pass it back to the LLm with a follow up request asking to correct the proiblem that caused the error, this opften times works pretty well. We can run through multiple error catching and correction cycles if we don't get good results straight away.

![](https://github.com/DanialArab/images/blob/main/Pydantic_for_LLM_applications/pydantic_error_catchin_correctio_cycle.png)

2. But there is an even more reliable way of doing this. HERE


## Pydantic fundamentals 

- 

Reference: https://www.deeplearning.ai/short-courses/pydantic-for-llm-workflows/
