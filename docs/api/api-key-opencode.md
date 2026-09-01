# OpenCode

[OpenCode](https://github.com/anomalyco/opencode) is an open-source command-line interface (CLI) for interacting with large language models (LLMs). It provides a simple and flexible way to use LLMs for various tasks, such as text generation, code completion, and more.

## Prerequisites

1. Your AI Assistant course or team must be configured to use Anthropic models (see instructor or team lead)
2. Obtain your AI Assistant API Key. [Instructions can be found here](api-token.md)
3. Install OpenCode. Instructions can be found here, https://opencode.ai/
4. The remaining instructions assume you have an open terminal on system with OpenCode and bash installed.

## 1. Setup the opencode configuration file

OpenCode uses a configuration file to define custom providers and models. The configuration file is located at either of the following locations:
- (Mac/Linux) `~/.config/opencode/opencode.json`
- (Mac/Linux)`~/.config/opencode/opencode.jsonc` (`jsonc` is a superset of `json` that allows comments)

Here is an example configuration file for OpenCode that uses the AI Assistant provider and models:
```jsonc
{
  "provider": {
    "litellm": { // this is identifier for the provider, you can choose any name you like, need to be unique in the provider list
      "name": "AI Assistant", // this is the display name of the provider (what is shown by the `/model` command), you can choose any name you like
      "npm": "@ai-sdk/openai-compatible", // this is the npm package that provides the provider's API, use `@ai-sdk/openai-compatible` unless you know what you are doing
      "models": {
        "gpt-oss-120b": { // this is the model name shown in the AI Assistant
            "name": "my-gpt-oss-120b" // this is the display name of the model (what is shown by the `/model` command), you can choose any name you like
        },
        "gemma-4-26b-a4b": {
            "name": "my-gemma-4-26b-a4b"
        }
      },
      "options": {
        "apiKey": "sk-xxxxxxxxxxxxxxxxxxxxxx", // replace this with your AI Assistant API Key
        "baseURL": "https://llm-api.cyverse.ai/v1", // this is the base URL for the AI Assistant, copy-paste from the same page where you got your API Key
        "timeout": 600000 // optional, this is the timeout in milliseconds for API requests, default is 600000 (10 minutes)
      }
    }
  },
  "$schema": "https://opencode.ai/config.json"
}
```

## 2. Start OpenCode

You can then run OpenCode.
```
opencode
```

Use `/model` command to select the model you want to use. You can also use `/model <model-name>` to switch models on the fly.

## If you need to change your API Key

If for some reason you need to change your AI Assistant API Key, you can simply replace your api key in the configuration file in step 1.
