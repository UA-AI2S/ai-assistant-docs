# Using the AI Assistant with AWS Bedrock

AWS Bedrock is Amazon's fully managed service for accessing foundation models from leading AI providers. The AI Assistant allows users to use AWS Bedrock-provided Anthropic Claude models with coding agents such as Claude Code and third-party AI applications.

!!! Note

    Currently, the subsequent instructions focus on using Anthropic Claude models from AWS Bedrock. As other models are provided, the instructions will be updated.

## Prerequisites

Before connecting the AI Assistant to AI applications, you will need:

- An **AI Assistant API key** — sign in at [chat.cyverse.ai](https://chat.cyverse.ai), open your course or team details, and copy the key from the **API Key** tab. See [Obtaining your AI Assistant API Key](api-token.md) for step-by-step instructions.
- The **AI Assistant base URL**: `https://api.cyverse.ai/` (or the URL shown in your course details).

## How It Works

The AI Assistant acts as a proxy between your application and the underlying model. When you send a request to the AI Assistant endpoint, it authenticates the request against your team or course budget, applies any configured guardrails, then forwards the request to the appropriate model — which may be hosted on AWS Bedrock. This means you interact with a single, consistent OpenAI-compatible endpoint regardless of which cloud provider is serving the model.
