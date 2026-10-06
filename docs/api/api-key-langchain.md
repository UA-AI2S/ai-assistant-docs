# Using your AI Assistant API key to integrate with LangChain

## 1. Install LangChain Python libraries
```bash
pip install langchain-litellm
```

See the [LangChain LiteLLM integration guide](https://docs.langchain.com/oss/python/integrations/chat/litellm) for details on this package.

## 2. Obtain variables to integrate the AI Assistant with LangChain

Obtaining your AI Assistant API key is outlined [here](api-key.md).


You can obtain a list of the models you have access to with the following command; denoted by "id":
```bash
curl -s -L "https://ai-assistant.responsibleai.arizona.edu/v1/models" -H "Authorization: Bearer [AI Assistant API KEY]" -H 'Content-Type: application/json'|jq
```
## 3. Create Python scripts
```python
from langchain_litellm import ChatLiteLLM

llm = ChatLiteLLM(
    model="litellm_proxy/[MODEL NAME]",
    api_key="[AI Assistant API KEY]",
    api_base="https://ai-assistant.responsibleai.arizona.edu/v1")

print (llm.invoke("Hello, world!"))
```


Alternatively, you can include the API key as an environment variable or secret to avoid storing it in plain text:

```python
import getpass
import os

if not os.environ.get("AI_ASSISTANT_API_KEY"):
	os.environ["AI_ASSISTANT_API_KEY"] = getpass.getpass("Enter AI Assistant API key: ")
api_key = os.environ["AI_ASSISTANT_API_KEY"]

from langchain_litellm import ChatLiteLLM

llm = ChatLiteLLM(
    model="litellm_proxy/[MODEL NAME]",
    api_key=api_key,
    api_base="https://ai-assistant.responsibleai.arizona.edu/v1")

print (llm.invoke("Hello, world!"))
```
