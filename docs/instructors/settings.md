# Workspace Settings

The **Settings** page is where you configure how your workspace behaves — which models are available, what dates the workspace is active, and how your budget is allocated across members.

You can access workspace settings by clicking **Details** on your workspace card, then selecting the **Overview** or **Settings** tab.

## Workspace Details

These are the basics of your workspace that you can update at any time:

- **Name** — The display name students see when they log in (e.g., "ISTA 130 — Fall 2026").
- **Description** — A short note explaining the workspace's purpose. Helps students confirm they're in the right place.
- **Start and End Dates** — Controls when members can use the workspace. Students cannot access models or use API keys outside of these dates.
- **Status** — Toggle between **Active** and **Inactive**. Setting a workspace to Inactive temporarily suspends access without deleting anything.

!!! tip
    Set your start date a few days before the semester begins so students can get set up early.

## Model Configuration

Your workspace determines which AI models are available to members. The models listed on the API Keys page come from this configuration.

- Models are hosted on **AWS Bedrock** and **on-premise** infrastructure — students never interact with external providers directly.
- The available model list is managed by the AI Assistant team. If you need a specific model enabled, contact **ai-verde-support@cyverse.org**.

For a full list of currently available models, see [Current Models](../models-current.md).

### Bring Your Own (BYO) Model

Instructors can also bring their own commercial or third-party LLM and share access with their workspace members. This is useful if your research or coursework requires a specific model not already available on the platform. Reach out to the AI Assistant team to set this up.

## Budget Management

Budgets control how much your workspace can spend on model usage. The budget is set by CyVerse, but as an instructor you have visibility into how it's being used.

### What You Can See

- **Total workspace usage** — How much of the budget has been consumed overall.
- **Per-member usage** — How much each individual student or team member has used.

### What You Can Do

- **Set per-member limits** — Cap how much any single member can spend, preventing one student from consuming a disproportionate share.
- **Request budget increases** — If you're running low before the semester ends, contact **ai-verde-support@cyverse.org**.

!!! note
    You cannot increase the total workspace budget yourself — this requires a request to the CyVerse team.

### Planning Around Your Budget

A few practical tips:

- **Check usage before big assignments.** If you're assigning a project that requires heavy model usage, verify you have enough budget remaining.
- **Set per-member limits early.** This prevents surprises where a few students exhaust the budget before others get to use it.
- **Monitor mid-semester.** A quick check halfway through the term can catch trends before they become problems.

## Member Roles

Workspace settings also determine who has management access. There are three roles:

| Role | Can Chat | Can Use API Key | Can Manage Members | Can Edit Settings |
|------|----------|-----------------|-------------------|-------------------|
| **Instructor** | Yes | Yes | Yes | Yes |
| **TA** | Yes | Yes | Limited | No |
| **Student** | Yes | Yes | No | No |

To change a member's role, go to the **Members** tab, find the member, and update their role.

## Common Questions

**Can I have multiple instructors on one workspace?**
:   Yes. Add them as members with the **Instructor** role. All instructors have full management access.

**What happens when the end date passes?**
:   Members lose access to the workspace. API keys stop working. The workspace and its data are preserved — you can reactivate it by updating the end date and setting the status back to Active.

**I changed the available models but a student still sees the old list.**
:   Ask the student to sign out and sign back in, or refresh their dashboard. Model changes take effect immediately but may require a page refresh to appear.

**Can I duplicate a workspace for next semester?**
:   Not directly from the dashboard. Contact **ai-verde-support@cyverse.org** and they can set up a new workspace with similar settings.
