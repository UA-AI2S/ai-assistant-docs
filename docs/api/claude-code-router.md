# Claude Code Router (using non-Anthropic Models)
You can follow these instructions to use your AI-VERDE API Key after installing Claude Code and Claude Code Router. More information on installing and using Claude Code Router can be found here, https://github.com/musistudio/claude-code-router.

## Prerequisites
1. Obtain your VERDE API Key. Instructions can be found here, https://aiverde-docs.cyverse.ai/api/api-token/
2. Note the model(s) you want to configure for Claude Code. Instructions can be found here, https://aiverde-docs.cyverse.ai/api/api-key-models/.
3. Install Claude Code. Instructions can be found here, https://www.anthropic.com/claude-code/
4. Install Claude Code Router. Instructions can be found here, https://github.com/musistudio/claude-code-router
5. The remaining instructions assume you have an open terminal on system with Claude Code and bash installed.

## 1. Starting Claude Code Router
This step should only be needed the first time you use Claude Code Router.

In a terminal, enter the command `ccr start`
```
$ ccr start
```

## 2. Configuring Claude Code Router
After running `ccr code`, you will be prompted to enter the minimum configuration to start Claude Code Router. Use the following table for guidance on the values:

| Field | Value or Instructions | Notes |
| ------| --------------------- | ----- |
| Provider Name | `ai-verde` | any string works |
| Provider API KEY | enter your AI-VERDE API key | |
| Provider URL | `https://llm-api.cyverse.ai/v1/chat/completions` | |
| MODEL Name | `<verde model name>` | replace `<verde model name>` with the model you'd like to use |

After entering the MODEL name, you should see text similar to the following:
```
Loaded JSON config from: /root/.claude-code-router/config.json
register transformer: Anthropic (endpoint: /v1/messages)
register transformer: gemini (endpoint: /v1beta/models/:modelAndAction)
register transformer: deepseek (no endpoint)
register transformer: tooluse (no endpoint)
register transformer: openrouter (no endpoint)
register transformer: maxtoken (no endpoint)
providerConfig:  ai-verde undefined
ai-verde provider registered
🚀 LLMs API server listening on http://127.0.0.1:3456
```
Press `ctrl-c` so that you can run Claude Code with Claude Code Router.

## 3. Running Claude Code Router
Running Claude Code with Claude Code Router with the following command:

```
ccr code
```

If you are successful entering Claude Code, congratulations! To use Claude Code with the same settings, you will need to run `ccr code` every time.

## Updating Claude Code Router configuration
At some point, you may want to add other models or add or update configuration options. To do so, you can edit the configuration file found in `~/.claude-code-router/config.json`
