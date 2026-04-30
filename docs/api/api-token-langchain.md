# Using your AI-VERDE API key to integrate with LangChain

## 1. Install LangChain python libraries
```bash 
pip install langchain_community 
```

## 2. Obtain variables to integrate AI-VERDE with LangChain

Obtaining your AI-VERDE API key is outlined [here](/api/api-token/).


You can obtain a list of the models you have access to with the following command; denoted by "id":
```bash
curl -s -L "https://llm-api.cyverse.ai/v1/models" -H "Authorization: Bearer [AI-VERDE API KEY]" -H 'Content-Type: application/json'|jq 
```
## 3. Create python scripts
```python
from langchain_community.chat_models import ChatLiteLLM

llm = ChatLiteLLM(
    model="litellm_proxy/[MODEL NAME]",
    api_key="[AI-VERDE API KEY]",
    api_base="https://llm-api.cyverse.ai")

print (llm.invoke("Hello, world!"))
```


Alternatively, you can include the API key as an environment variable or secret to avoid storing it in plain text:

```python
import getpass
import os

if not os.environ.get("AIVERDE_API_KEY"):
  os.environ["AIVERDE_API_KEY"] = getpass.getpass("Enter AI-VERDE API key: ")
api_key = os.environ["AIVERDE_API_KEY"]

from langchain_community.chat_models import ChatLiteLLM

llm = ChatLiteLLM(
    model="litellm_proxy/[MODEL NAME]",
    api_key=api_key,
    api_base="https://llm-api.cyverse.ai")

print (llm.invoke("Hello, world!"))
```