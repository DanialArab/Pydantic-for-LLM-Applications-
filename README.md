# Pydantic for LLM Applications

- We can use Pydantic to get structured output from an LLM through leveraging data validations that can be used in any software systems. 
- Like we can get output from an LLM in an exact format I need or to validate the LLM response
- In general, LLM produces free-form text but when we build LLM into a larger software system where we have multiple components and we want to pass the data we are getting from LLM to the system's next component in a predictable way --> We need to get the structured output using Pydantic
- So getting the structured output can be very helpful to be able to amke a good decision on  the next good step like for example if the request coming from a user being passed to an LLM, if we have a structured output we may manage the request in a wise way like we can have it as a support ticket that requires a human attention or passing it to another LLM which calls a tool like FAQ lookup tool
- We can use different methods to get structured responses from LLM and also validate those responses
- We can validate data in any software system, like data that can be put into a system by humans or external APIs and data sources or any data that can be passed from one component to another in a software system 


Reference: https://www.deeplearning.ai/short-courses/pydantic-for-llm-workflows/
