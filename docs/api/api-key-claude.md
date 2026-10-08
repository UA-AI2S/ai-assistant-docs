# Using Claude Code with AI Assistant

Claude Code is Anthropic's coding assistant. Use the Bedrock setup below to access Claude models hosted on AWS Bedrock through AI Assistant.

AI Assistant handles AWS authentication and workspace budgets. You only need your AI Assistant API key and access to the models in your workspace.

For the VS Code extension setup, see [Using Claude Code in VS Code with AI Assistant](api-key-claude-vscode.md).

## Prerequisites

1. [Install Claude Code](https://code.claude.com/docs/en/setup#install-claude-code).
2. [Obtain your AI Assistant API key](api-key.md).
3. In your workspace's **API Key** tab, copy the exact model IDs from **Available Models** for the Opus, Sonnet, and Haiku models you will use. See [Check Your Available Models](api-key.md#5-check-your-available-models) for details.
4. Open a Bash or Zsh terminal on Linux or macOS.

## 1. Configure Bedrock

Replace the placeholders below with your API key and the model IDs from your workspace.

```bash
unset ANTHROPIC_BASE_URL ANTHROPIC_API_KEY AWS_BEARER_TOKEN_BEDROCK

export ANTHROPIC_AUTH_TOKEN="<your-ai-assistant-api-key>"
export ANTHROPIC_BEDROCK_BASE_URL="https://ai-assistant.ai2s.org/bedrock"
export CLAUDE_CODE_SKIP_BEDROCK_AUTH=1
export CLAUDE_CODE_USE_BEDROCK=1

export ANTHROPIC_DEFAULT_OPUS_MODEL="<opus-model-id>"
export ANTHROPIC_DEFAULT_SONNET_MODEL="<sonnet-model-id>"
export ANTHROPIC_DEFAULT_HAIKU_MODEL="<haiku-model-id>"
export ANTHROPIC_MODEL="$ANTHROPIC_DEFAULT_SONNET_MODEL"
```

If your workspace shows a different AI Assistant base URL, replace its trailing `/v1` with `/bedrock`.

The three `ANTHROPIC_DEFAULT_*_MODEL` variables map Claude Code's model choices to models available in your workspace. `ANTHROPIC_MODEL` starts the session with your chosen Sonnet model. See [Claude Code model environment variables](https://code.claude.com/docs/en/model-config#environment-variables) for details on these model settings.

The `unset` line clears conflicting credentials and endpoint settings from your current shell. If you previously configured these variables in a Claude Code settings file, update or remove the overlapping entries in its `env` section too. See [Claude Code settings precedence](https://code.claude.com/docs/en/settings#settings-precedence) to check which configuration applies.

For more details on the Bedrock flags and gateway credentials, see [Claude Code gateway configuration](https://code.claude.com/docs/en/llm-gateway-connect#amazon-bedrock).

## 2. Start and verify Claude Code

Start Claude Code from the same terminal:

```bash
claude
```

Run `/status` and confirm the following:

- The API provider is **Amazon Bedrock**.
- The Bedrock base URL is `https://ai-assistant.ai2s.org/bedrock`, or your workspace's corresponding URL.
- AWS authentication is skipped.
- The selected model matches the Sonnet model ID you configured.

Send a short prompt, such as `Reply with hello`, and confirm you receive a response.

If the provider or endpoint differs, check your shell variables and any overlapping `env` entries in your Claude Code settings files. If the request fails, confirm your API key and model IDs match those in your workspace.

## 3. Save your configuration

After the test succeeds, add the configuration block from step 1 to `~/.bashrc` for Bash or `~/.zshrc` for Zsh.

Replace any older Claude Code configuration in that file with the block you tested. Reload your shell profile or open a new terminal before launching Claude Code again.

### Turn off telemetry

To turn off telemetry and other nonessential background traffic in Claude Code CLI, add `"CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1"` to the `env` section of `~/.claude/settings.json`:

```json
{
	"env": {
		"CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1"
	}
}
```

If the file already contains settings, merge this entry into its existing `env` section. Restart Claude Code after saving the file.

For shell-based configuration, add the following line to your shell profile instead:

```bash
export CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC=1
```

This setting also disables automatic updates. [Update Claude Code manually](https://code.claude.com/docs/en/setup#update-manually) when using it. See [Claude Code's nonessential traffic settings](https://code.claude.com/docs/en/llm-gateway-connect#turn-off-traffic-outside-the-gateway-path) for details.

See the [Claude Code environment variable reference](https://code.claude.com/docs/en/env-vars#variables) for `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC`.

## Update your API key

Replace the value of `ANTHROPIC_AUTH_TOKEN` in your saved configuration with your new AI Assistant API key. Reload the configuration and restart Claude Code.

## Alternative Anthropic-compatible endpoint

??? note "Use the Anthropic-compatible endpoint"

    Use this configuration when the AI Assistant support team directs you to AI Assistant's Anthropic-compatible endpoint. For the initial Bedrock-hosted models, use the main setup above.

    This endpoint uses your AI Assistant API key and the base URL `https://ai-assistant.ai2s.org`. Replace the placeholders with the exact model IDs available through this endpoint in your workspace.

    ```bash
    unset CLAUDE_CODE_USE_BEDROCK CLAUDE_CODE_SKIP_BEDROCK_AUTH
    unset ANTHROPIC_BEDROCK_BASE_URL ANTHROPIC_AUTH_TOKEN AWS_BEARER_TOKEN_BEDROCK

    export ANTHROPIC_BASE_URL="https://ai-assistant.ai2s.org"
    export ANTHROPIC_API_KEY="<your-ai-assistant-api-key>"

    export ANTHROPIC_DEFAULT_OPUS_MODEL="<opus-model-id>"
    export ANTHROPIC_DEFAULT_SONNET_MODEL="<sonnet-model-id>"
    export ANTHROPIC_DEFAULT_HAIKU_MODEL="<haiku-model-id>"
    export ANTHROPIC_MODEL="$ANTHROPIC_DEFAULT_SONNET_MODEL"
    ```

    If your workspace shows a different AI Assistant base URL, remove its trailing `/v1` for `ANTHROPIC_BASE_URL`.

    For details on endpoint and credential settings, see [Claude Code gateway connection setup](https://code.claude.com/docs/en/llm-gateway-connect).

    Update or remove overlapping `env` entries in Claude Code settings files when switching endpoints. Start Claude Code from the same terminal and run `/status`. Confirm it shows your Anthropic base URL and `ANTHROPIC_API_KEY` as the credential source, then send a short test prompt.

    After the test succeeds, save this block in your shell profile in place of the Bedrock block. When your API key changes, update `ANTHROPIC_API_KEY`, reload the configuration, and restart Claude Code.

For non-Anthropic models, see [Using Claude Code with non-Anthropic models](api-key-claude-non-anthropic.md).
