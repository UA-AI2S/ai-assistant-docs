# Claude Code (using non-Anthropic Models)

You can follow these instructions to use your VERDE API Key after installing Claude Code. More information on using Claude Code can be found here, https://docs.anthropic.com/en/docs/intro.

!!! Note

    These instructions assume you are using a space that is connected to non-Anthropic models. Even though Claude Code is using non-Anthropic models, the API it uses is still Anthropic-style, instead the API is translated by Verde's LiteLLM into OpenAI-compatible or other supported formats.

## Prerequisites

1. Your VERDE course or team must be configured to use Anthropic models (see instructor or team lead)
2. Obtain your VERDE API Key. [Instructions can be found here](api-token.md)
3. Install Claude Code. Instructions can be found here, https://www.anthropic.com/claude-code/
4. The remaining instructions assume you have an open terminal on system with Claude Code and bash installed.

## 1. Set the Environment Variables

Export the following environment variables before launching claude code. Note that you can use the same model for all tiers (Opus/Sonnet/Haiku) or you can use different models for each tier. The model names must match the exact model name in LiteLLM.

```bash
export ANTHROPIC_API_KEY="<your-ai-verde-api-key>"
export ANTHROPIC_BASE_URL="https://llm-api.cyverse.ai"
export ANTHROPIC_DEFAULT_OPUS_MODEL="<model name for opus-tier model>"
export ANTHROPIC_DEFAULT_SONNET_MODEL="<model name for sonnet-tier model>"
export ANTHROPIC_DEFAULT_HAIKU_MODEL="<model name for haiku-tier model>"
export ANTHROPIC_MODEL="<model name for primary model>"
```

For example:

```bash
export ANTHROPIC_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxx"
export ANTHROPIC_BASE_URL="https://llm-api.cyverse.ai"
export ANTHROPIC_DEFAULT_OPUS_MODEL="gpt-oss-120b"
export ANTHROPIC_DEFAULT_SONNET_MODEL="gemma-4-26b-a4b"
export ANTHROPIC_DEFAULT_HAIKU_MODEL="gemma-4-26b-a4b"
export ANTHROPIC_MODEL="gpt-oss-120b"
```

!!! Note

    To obtain the AI-VERDE Anthropic Base URL, simply remove `/v1` (e.g. `https://llm-api.cyverse.ai/v1` => `https://llm-api.cyverse.ai`).

To avoid re-entering this each session, add the line to your shell profile (e.g. `~/.bashrc` or `~/.zshrc`). Then, you can source your shell profile.


## 2. Start Claude Code

You can then run Claude Code.
```
claude
```
After initially launching Claude Code, claude will write the variables into a `~/.claude/settings.json` file. You do not need to repeat step #1 again for future sessions.

## If you need to change your `ANTHROPIC_API_KEY`

If for some reason you need to change your VERDE API Key, you can use the slash command `/logout` in claude or delete your `~/.claude/settings.json`; then, repeat steps 1-2.
