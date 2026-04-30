# Aider
You can follow these instructions to use your AI-VERDE API Key after Aider, self-described "AI pair programming in your terminal". More information on installing and using Aider can be found here, https://aider.chat.

## Prerequisites
1. Obtain your AI-VERDE API Key. Instructions can be found here, https://aiverde-docs.cyverse.ai/api/api-token/.
2. Note the model(s) you want to configure for Claude Code. Instructions can be found here, https://aiverde-docs.cyverse.ai/api/api-key-models/.
3. Install Aider. Instructions can be found here, https://aider.chat/#getting-started.
4. The remaining instructions assume you have an open terminal on a Linux system with Aider.

## 1. Configuring Aider

1. Create a `$HOME/.aider.conf.yml` file with the following contents
```
openai-api-key: insert-your-aiverde-api-key
openai-api-base: https://llm-api.cyverse.ai/v1
model: openai/insert-default-model
```
2. Replace `insert-your-aiverde-api-key` with AI-VERDE API Key. 
3. Replace the text `insert-default-model` with the AI-VERDE model. For example, to use `phi4`, the model field would be set to `openai/phi4` or if you were using `nrp/phi4` model, the model field would be set to `openai/nrp/phi4`.

!!! Note
    This is the minimal configuration needed to use Aider. If you want to set other configuration for any models, you add a `$HOME/.aider.model.metadata.json` file. Instructions on the configuration values that can be set in this file can be found here, https://aider.chat/docs/config/adv-model-settings.html. 

## 2. Running Aider
Run Aider with the following command:

```
aider
```

!!! Note
    You may get additional prompts if you're not in a git repo and if you have not configured your model further (see note above). You can also run aider with `aider --no-show-model-warnings` if you prefer to ignore model warnings

If you are successful entering Aider, congratulations! 

