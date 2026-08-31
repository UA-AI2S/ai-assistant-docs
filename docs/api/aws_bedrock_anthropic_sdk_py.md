# Using Anthropic Python SDK with AI-VERDE

[Anthropic Python SDK](https://github.com/anthropics/anthropic-sdk-python) is Anthropic's official Python SDK for interacting with Claude models. AI-VERDE can serve as the backend for the Anthropic Python SDK, routing requests through AI-VERDE's budget controls and guardrails to Anthropic Claude models hosted on AWS Bedrock.
    
## Prerequisites

1. Obtain your **AI-VERDE API key** and note the **AI-VERDE base URL**. The base url that will be used in the script need to be strip of the `/v1` suffix if present [Instructions can be found here](api-token.md).
2. Note the **Claude model ID** for Opus, Sonnet, and Haiku. [Instructions for listing available models can be found here](api-key-models.md).
3. Install **Anthropic Python SDK**. Instructions can be found at [https://github.com/anthropics/anthropic-sdk-python](https://github.com/anthropics/anthropic-sdk-python).

## Example Python script using Anthropic Python SDK with AI-VERDE

Export the following environment variables for your script.

```bash
export ANTHROPIC_API_KEY="<your-ai-verde-api-key>"
```

For example:

```bash
export ANTHROPIC_API_KEY="sk-xyz"
```

Example script
```
import os
from anthropic import Anthropic

client = Anthropic(
    base_url="https://llm-api.cyverse.ai", # Replace with the AI-VERDE base URL if different
    api_key=os.environ.get("ANTHROPIC_API_KEY"),
)

message = client.messages.create(
    max_tokens=128,
    messages=[
        {
            "role": "user",
            "content": "Hello, Claude",
        }
    ],

    model="<model name for opus>", # Replace with the model name for Opus, Sonnet, or Haiku as needed
)

print(message.content)
```

!!! Note

    To obtain the AI-VERDE Anthropic Base URL, strip `/v1` suffix if present.
