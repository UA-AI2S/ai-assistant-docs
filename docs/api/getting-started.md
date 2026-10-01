# Introduction to the AI Assistant API

The AI Assistant exposes an OpenAI-compatible API, so any tool or library that supports OpenAI can connect to it using your AI Assistant API key.

## Getting Started

1. **Obtain your API key** — Sign in at [ai-assistant.ai2s.org](https://ai-assistant.ai2s.org), open your workspace, and copy the key from the **API Key** tab. See [Obtaining Your API Key](api-key.md) for step-by-step instructions.
2. **Know which models are available** — Your available models are listed on the same API Key page.

## Base URL and Authentication

All AI Assistant API endpoints use the same base URL and bearer-token authentication pattern as OpenAI. When configuring a client, set:

- **Base URL**: `https://ai-assistant.ai2s.org/v1` (or the URL shown in your workspace)
- **API Key**: the key you copied from the AI Assistant dashboard
