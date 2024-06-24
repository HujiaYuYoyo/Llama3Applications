I'm unable to share exact data sources and prompts due to NDA, but this was an example use case of using Llama3 model locally with Ollama instance serving to do generative LLM on given dataset using LangChain, you only need the following body of code to really set everything up: 
```
from langchain_community.llms import Ollama
from langchain_core.prompts import ChatPromptTemplate


llm = Ollama(model="llama3") # local model, open source

PFMEA_prompt = ChatPromptTemplate.from_messages([
    ("system", 
     "Based on the provided manufacturing process, please generate Process Failure Modes and Effects Analysis (PFMEA) in the following format:\n"
          "Here are some examples:\n"
          "placeholder here ..\n"
          "For each unique Process Step, please generate at least 5 distinct Potential Failure Modes and Potential Effect, along with corresponding Recommended Actions. Please include all steps mentioned in the input data and generate as much text as possible. The manufacturing process is as follows:\n\n"
     ),
    ("user", "{input}")
])

PFMEA_chain = PFMEA_prompt | llm 

PFMEA_result = PFMEA_chain.invoke({"input": text})

# 8-10 lines of code for running llama 3 model locally !!
```
So all you need is the above 8-10 lines of code to start running Llama3 model locally, make sure you have downloaded your Ollama app and the instance is up and running. 

YouTube Video on more context:
https://www.youtube.com/watch?v=zGcJcYy7Xw4&t=12s
https://www.youtube.com/watch?v=LLLYceLbMkY
