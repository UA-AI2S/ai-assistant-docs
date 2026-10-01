# Using Claude Code with non-Anthropic models

Use AI Assistant's Anthropic-compatible endpoint to connect Claude Code to non-Anthropic models in your workspace. Claude Code sends Anthropic-style requests, which AI Assistant translates for the selected model.

For Claude models hosted on AWS Bedrock, see [Using Claude Code with AI Assistant](api-key-claude.md).

## Prerequisites

1. [Install Claude Code](https://code.claude.com/docs/en/setup#install-claude-code).
2. [Obtain your AI Assistant API key](api-key.md).
3. Confirm with your workspace admin that non-Anthropic models are available through the Anthropic-compatible endpoint.
4. Copy the exact model IDs from your workspace's **Available Models** section. See [Check your available models](api-key.md#5-check-your-available-models).
5. Open a Bash or Zsh terminal on Linux or macOS.

## 1. Configure the Anthropic-compatible endpoint

Replace the placeholders below with your API key and the non-Anthropic model IDs available in your workspace.

```bash
unset CLAUDE_CODE_USE_BEDROCK CLAUDE_CODE_SKIP_BEDROCK_AUTH
unset ANTHROPIC_BEDROCK_BASE_URL ANTHROPIC_AUTH_TOKEN AWS_BEARER_TOKEN_BEDROCK

export ANTHROPIC_BASE_URL="https://ai-assistant.ai2s.org"
export ANTHROPIC_API_KEY="<your-ai-assistant-api-key>"

export ANTHROPIC_DEFAULT_OPUS_MODEL="<opus-tier-model-id>"
export ANTHROPIC_DEFAULT_SONNET_MODEL="<sonnet-tier-model-id>"
export ANTHROPIC_DEFAULT_HAIKU_MODEL="<haiku-tier-model-id>"
export ANTHROPIC_MODEL="$ANTHROPIC_DEFAULT_SONNET_MODEL"
```

If your workspace shows a different AI Assistant base URL, remove its trailing `/v1` for `ANTHROPIC_BASE_URL`.

The three `ANTHROPIC_DEFAULT_*_MODEL` variables map Claude Code's Opus, Sonnet, and Haiku choices to your non-Anthropic models. You can use the same model ID for all three tiers. `ANTHROPIC_MODEL` starts the session with your chosen Sonnet-tier model. See [Claude Code model environment variables](https://code.claude.com/docs/en/model-config#environment-variables) for details.

The `unset` lines clear conflicting Bedrock settings and credentials from your current shell. If you previously configured these variables in a Claude Code settings file, update or remove the overlapping entries in its `env` section too. See [Claude Code settings precedence](https://code.claude.com/docs/en/settings#settings-precedence) to check which configuration applies.

For details on endpoint and credential settings, see [Claude Code gateway connection setup](https://code.claude.com/docs/en/llm-gateway-connect).

## 2. Start and verify Claude Code

Start Claude Code from the same terminal:

```bash
claude
```

Run `/status` and confirm the following:

- The API base URL is `https://ai-assistant.ai2s.org`, or your workspace's corresponding URL.
- The credential source is `ANTHROPIC_API_KEY`.
- The selected model matches the Sonnet-tier model ID you configured.

Send a short prompt, such as `Reply with hello`, and confirm you receive a response.

If the endpoint or credential source differs, check your shell variables and overlapping `env` entries in your Claude Code settings files. If the request fails, confirm your API key and model IDs match those in your workspace and that the models are available through this endpoint.

## 3. Save your configuration

Shell exports apply to the current terminal session and programs started from it. After the test succeeds, add the configuration block from step 1 to `~/.bashrc` for Bash or `~/.zshrc` for Zsh.

Replace any older Claude Code configuration in that file with the block you tested. Reload your shell profile or open a new terminal before launching Claude Code again.

## Update your API key

Replace the value of `ANTHROPIC_API_KEY` in your saved configuration with your new AI Assistant API key. Update any overlapping `ANTHROPIC_API_KEY` entry in a settings file's `env` section too. Reload your configuration, restart Claude Code, and send a short test prompt to verify the new key.
