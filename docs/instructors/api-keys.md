# API Keys

The **API Keys** page in your workspace lets you generate and manage the keys your students and team members use to connect to the AI Assistant from external tools — IDEs, CLI assistants, notebooks, and more.

You can find the API Keys page by clicking **Details** on your workspace card, then selecting the **API Key** tab.

## What Is an API Key?

An API key is a unique credential that lets a student (or any workspace member) send requests to the AI models available in your workspace. Each member gets their own key, and all usage is tracked back to them individually.

!!! tip
    Students do not need to create accounts with OpenAI, Anthropic, or any other provider. The API key from AI Assistant is all they need.

## Generating and Viewing Keys

- Each workspace member can generate their own API key from their dashboard.
- As an instructor, you can view whether members have active keys from the workspace management page.
- Keys follow the OpenAI-compatible format, so they work with any tool that accepts an OpenAI API key.

## What Students Do with Their Key

Once a student has their API key, they can use it in a variety of tools:

| Tool Type | Examples |
|-----------|---------|
| CLI Coding Assistants | Claude Code, Aider |
| Desktop Clients | ChatboxAI |
| Libraries | LangChain, LlamaIndex |

For step-by-step setup guides for each tool, see the [Using Your API Key](../api/api-key-claude.md) section.

## Available Models

The API Keys page also shows which models are available in your workspace. The model list is determined by your workspace settings — see [Workspace Settings](settings.md) for details on how to configure this.

Students can only access models that are enabled for the workspace. If a student reports that a model isn't working, check the workspace settings to confirm it is listed as available.

## Key Limits and Budget

API key usage counts against the workspace budget. As an instructor, you can:

- View how much each member has consumed on the **Members** tab.
- Monitor total workspace usage to plan assignments around available resources.
- Contact **ai-verde-support@cyverse.org** to request budget adjustments.

!!! warning
    If your workspace budget is exhausted, API keys will stop working until the budget is replenished. Plan ahead for heavy-usage assignments like final projects.

## Revoking or Regenerating Keys

If a key is compromised or a student leaves the course:

- Remove the member from the workspace to revoke their access.
- Members can regenerate their own key at any time from the dashboard, which invalidates the old one.

## Common Questions

**Can I create a shared API key for the whole class?**
:   No. Each member has their own key so that usage can be tracked individually and budget limits can be enforced per person.

**Do API keys expire?**
:   Keys remain active as long as the workspace is active and the member is enrolled. Once the workspace end date passes or a member is removed, their key stops working.

**A student says their key isn't working — what should I check?**
:   1. Confirm the student is listed on the **Members** tab.
    2. Check that the workspace is set to **Active**.
    3. Verify the workspace budget hasn't been exceeded.
    4. Make sure the student is using the correct base URL: `https://ai-assistant.ai2s.org/`.
