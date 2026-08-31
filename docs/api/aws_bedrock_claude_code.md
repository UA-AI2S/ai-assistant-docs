# Using Claude Code with AI-VERDE

Claude Code is Anthropic's official CLI coding assistant. AI-VERDE can serve as the backend for Claude Code, routing requests through AI-VERDE's budget controls and guardrails to Anthropic Claude models hosted on AWS Bedrock.

## Prerequisites

1. Obtain your **AI-VERDE API key** and note the **AI-VERDE base URL**. The base url that will be used in the environment variables will be set with `/bedrock` rather than `/v1`[Instructions can be found here](api-token.md).
2. Note the **Claude model ID** for Opus, Sonnet, and Haiku. [Instructions for listing available models can be found here](api-key-models.md).
3. Install **Claude Code**. Instructions can be found at [https://www.anthropic.com/claude-code](https://www.anthropic.com/claude-code).
4. The remaining instructions assume you have an open terminal with Claude Code installed onlinux or mac terminal.

## 1. Set the Environment Variables

Export the following environment variables before launching claude code.

```bash
export ANTHROPIC_AUTH_TOKEN="<your-ai-verde-api-key>"
export ANTHROPIC_BEDROCK_BASE_URL=https://llm-api.cyverse.ai/bedrock
export CLAUDE_CODE_SKIP_BEDROCK_AUTH=1
export CLAUDE_CODE_USE_BEDROCK=1
export ANTHROPIC_DEFAULT_OPUS_MODEL="<model name for opus>"
export ANTHROPIC_DEFAULT_SONNET_MODEL="<model name for sonnet>"
export ANTHROPIC_DEFAULT_HAIKU_MODEL="<model name for haiku>"
```

For example:

```bash
export ANTHROPIC_AUTH_TOKEN="xyz"
export ANTHROPIC_BEDROCK_BASE_URL=https://llm-api.cyverse.ai/bedrock
export CLAUDE_CODE_SKIP_BEDROCK_AUTH=1
export CLAUDE_CODE_USE_BEDROCK=1
export ANTHROPIC_DEFAULT_OPUS_MODEL="my-team-claude-opus-4-6"
export ANTHROPIC_DEFAULT_SONNET_MODEL="my-team-claude-sonnet-4-6"
export ANTHROPIC_DEFAULT_HAIKU_MODEL="my-team-claude-haiku-4-5"
```

!!! Note

    To obtain the AI-VERDE Bedrock Base URL, simply substitute `/v1` with `/bedrock`.

To obtain the AI-VERDE Bedrock Base URL, simply substitute `/v1` with `/bedrock`.

To avoid re-entering this each session, add the line to your shell profile (e.g. `~/.bashrc` or `~/.zshrc`). Then, you can source your shell profile.

## 2. Launch Claude Code

Start Claude Code:

```bash
claude
```
