# Introduction to the AI Assistant API

The AI Assistant exposes an OpenAI-compatible API, so any tool or library that supports OpenAI can connect to it using your AI Assistant API key. This section explains how to get your key and use it across a range of environments.

## Getting Started

Before using the API you will need to:

1. **Obtain your API key** — Sign in at [chat.cyverse.ai](https://chat.cyverse.ai), open your course or team details, and copy the key from the **API Key** tab. See [Obtaining your AI Assistant API Key](api-token.md) for step-by-step instructions.
2. **Know which models are available** — Your available models are listed on the same API Key page. You can also retrieve them programmatically; see [Getting a List of Models](api-key-models.md).

## What's in This Section

| Section                                              | What it covers                                                             |
| ---------------------------------------------------- | -------------------------------------------------------------------------- |
| [Using Your API Key in Code](api-token-langchain.md) | Python integration with LangChain and LlamaIndex                           |
| [Using CLI Coding Assistants](claude-code-router.md) | Terminal-based AI coding tools: Claude Code Router, Aider, and Claude Code |
| [Using IDEs](api-token-vscode.md)                    | Editor integrations for VSCode and Jupyter                                 |
| [Using Desktop Clients](chatboxai.md)                | GUI chat clients such as ChatboxAI                                         |

## Base URL and Authentication

All AI Assistant API endpoints use the same base URL and bearer-token authentication pattern as OpenAI. When configuring a client, set:

- **Base URL**: `https://api.cyverse.ai/` (or the URL shown in your course details)
- **API Key**: the key you copied from the AI Assistant dashboard
