# Using your AI-VERDE API key to integrate with LlamaIndex

## 1. Install LlamaIndex libraries
```bash
pip install llama-index-core llama-index-llms-litellm
```

## 2. Obtain variables to integrate AI-VERDE with LangChain

Obtaining your AI-VERDE API key is outlined [here](/api/api-token.md).


You can obtain a list of the models you have access to with the following command; denoted by "id":
```bash
curl -s -L "https://llm-api.cyverse.ai/v1/models" -H "Authorization: Bearer [AI-VERDE API KEY]" -H 'Content-Type: application/json'|jq 
```

## 3. Write python scripts
```python
from llama_index.llms.litellm import LiteLLM
from llama_index.core.llms import ChatMessage

llm = LiteLLM(
    model="litellm_proxy/[MODEL NAME]",
    api_base="https://llm-api.cyverse.ai",
    api_key="[AI-VERDE API KEY]",)

message = ChatMessage(role="user", content="Hey! how's it going?")
response = llm.chat([message])

print(response)
```

Alternatively, you can include the API key as an environment variable or secret to avoid storing it in plain text:

```python
import getpass
import os

if not os.environ.get("AIVERDE_API_KEY"):
  os.environ["AIVERDE_API_KEY"] = getpass.getpass("Enter AI-VERDE API key: ")
api_key = os.environ["AIVERDE_API_KEY"]

from llama_index.llms.litellm import LiteLLM
from llama_index.core.llms import ChatMessage

llm = LiteLLM(
    model="litellm_proxy/[MODEL NAME]",
    api_base="https://llm-api.cyverse.ai",
    api_key="[AI-VERDE API KEY]",)

message = ChatMessage(role="user", content="Hey! how's it going?")
response = llm.chat([message])

print(response)
```

!!! Note "Llama Index embedding support is outlined [here](https://docs.llamaindex.ai/en/stable/api_reference/embeddings/litellm/#llama_index.embeddings.litellm.LiteLLMEmbedding), but functionality depends on access to an embedding model through AI-VERDE."
