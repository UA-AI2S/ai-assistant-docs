# Managing a Workspace

This page covers everything you can do from the workspace details page — general settings, members, budget, and API keys.

## Settings

The **Settings** tab contains the workspace's general configuration. Under **General Settings** you can view and edit the workspace name, description, and active dates.

<!-- IMAGE NEEDED: General Settings page showing workspace name, description, start/end dates -->

## Members

Under **Settings > Members**, you can add and remove members and assign roles.

<!-- IMAGE NEEDED: Members page showing the member list with roles -->

### Roles

| Role | Can Chat | Can Use API Key | Can Manage Members | Can Edit Settings |
|------|----------|-----------------|-------------------|-------------------|
| **Admin** | Yes | Yes | Yes | Yes |
| **Member** | Yes | Yes | No | No |

### Adding Members Individually

Click **Add Member**, enter their NetID, and select a role. The default role is **Member**.

### Bulk Upload via CSV

For adding many members at once, upload a CSV file. A downloadable template is provided in the upload dialog.

The CSV format is:

```csv
UA NetID,role
jdoe,member
asmith,admin
```

- **UA NetID** is the only required column.
- **role** is optional — valid values are `admin` or `member`. If omitted or unrecognized, it defaults to `member`.

After uploading, a preview table shows who will be added and their roles before you confirm.

### Removing Members

Select a member from the list and remove them. Removing a member revokes their access to the workspace and invalidates their API key.

## API Keys

The **API Key** tab shows the member's API key for this workspace. Each member gets their own key — there is no shared key. All usage is tracked per member and counts against the workspace budget.

<!-- IMAGE NEEDED: API Key tab -->

!!! tip
    Members do not need accounts with OpenAI, Anthropic, or any other provider. The AI Assistant API key is all they need.

Members can find their key on the API Key tab and regenerate it if needed. For setup instructions, see [Obtaining Your API Key](../api/api-token.md).

## Models

The models listed on your workspace are what members can access through both the chat interface and the API. The model list is configured under **General Settings**.

- Models are hosted on **AWS Bedrock** and **on-premise** infrastructure — members never interact with external providers directly.
- To request a specific model, contact **ai-verde-support@cyverse.org**.
- For a full list of currently available models, see [Current Models](../models-current.md).

### Bring Your Own (BYO) Model

You can bring your own commercial or third-party LLM and share access with your workspace members. This is useful if your research or coursework requires a specific model not already on the platform. Reach out to the AI Assistant team to set this up.

## Budget

Under **Settings > Budget**, you can monitor spending and control how your budget is distributed.

<!-- IMAGE NEEDED: Budget page showing total spend vs. max budget and per-member usage table -->

### Workspace Usage

The budget page shows total workspace spend against the allocated maximum. Below that, a per-member usage table breaks down how much each individual has consumed.

!!! note
    You cannot increase the total workspace budget yourself — this requires a request to the AI2S team. Contact **ai-verde-support@cyverse.org** to request an increase.

### Per-Member Limits

You can cap how much any single member can spend. There are two ways to do this:

- **Default per-member budget** — Applies to all members. Set this to divide your budget evenly.
- **Custom member budget** — Override the default for specific members from the per-member usage table.

!!! warning
    If your workspace budget is exhausted, API keys and chat will stop working until the budget is replenished. Plan ahead for heavy-usage assignments.

### Planning Tips

- **Check usage before big assignments.** Verify you have enough budget remaining before assigning work that requires heavy model usage.
- **Set per-member limits early.** This prevents a few members from exhausting the budget before others get to use it.
- **Monitor mid-semester.** A quick check halfway through the term can catch trends before they become problems.

## Troubleshooting

**A member says their API key isn't working — what should I check?**

1. Confirm the member is listed on the **Members** page.
2. Verify the workspace budget hasn't been exceeded.
3. Make sure they are using the correct base URL: `https://ai-assistant.ai2s.org/`.

## Common Questions

**Can I have multiple admins on one workspace?**
:   Yes. Add them as members with the **Admin** role. All admins have full management access.

**Can I create a shared API key for the whole workspace?**
:   No. Each member has their own key so that usage can be tracked individually and per-member limits can be enforced.

**Do API keys expire?**
:   Keys remain active as long as the member is enrolled in the workspace. Once the workspace end date passes or a member is removed, their key stops working.

**What happens when the end date passes?**
:   Members lose access to the workspace. API keys stop working. The workspace and its data are preserved — you can reactivate it by updating the end date.

**I changed the available models but a member still sees the old list.**
:   Ask them to sign out and sign back in, or refresh their dashboard. Model changes take effect immediately but may require a page refresh to appear.

**Can I duplicate a workspace for next semester?**
:   Not directly from the dashboard. Contact **ai-verde-support@cyverse.org** and they can set up a new workspace with similar settings.
