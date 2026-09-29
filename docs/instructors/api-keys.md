# Managing Student API Access

Each workspace member gets their own API key for connecting to AI models from external tools — IDEs, CLI assistants, notebooks, and libraries. All usage is tracked per member and counts against your workspace budget.

!!! tip
    Students do not need to create accounts with OpenAI, Anthropic, or any other provider. The AI Assistant API key is all they need.

Students can generate their key and find setup instructions at [Obtaining Your API Key](../api/api-token.md).

<!-- Screenshot suggestion: the instructor's view of the API Keys tab showing member key status -->

## Budget and Usage

API key usage counts against the workspace budget. You can:

- View per-member usage on the **Members** tab.
- Monitor total workspace usage to plan assignments around available resources.
- Contact **ai-verde-support@cyverse.org** to request budget adjustments.

!!! warning
    If your workspace budget is exhausted, API keys will stop working until the budget is replenished. Plan ahead for heavy-usage assignments like final projects.

<!-- Screenshot suggestion: the Members tab showing per-member usage -->

## Troubleshooting

**A student says their key isn't working — what should I check?**

1. Confirm the student is listed on the **Members** tab.
2. Check that the workspace is set to **Active**.
3. Verify the workspace budget hasn't been exceeded.
4. Make sure the student is using the correct base URL: `https://ai-assistant.ai2s.org/`.

**Can I create a shared API key for the whole class?**
:   No. Each member has their own key so that usage can be tracked individually and budget limits can be enforced per person.

**Do API keys expire?**
:   Keys remain active as long as the workspace is active and the member is enrolled. Once the workspace end date passes or a member is removed, their key stops working.
