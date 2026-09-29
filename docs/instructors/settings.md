# Configuring Your Workspace

The workspace settings page controls model access, active dates, budget, and member roles. Access it by clicking **Details** on your workspace card.

!!! tip
    Set your start date a few days before the semester begins so students can get set up early.

<!-- Screenshot suggestion: the workspace Overview tab showing the settings fields -->

## Models

The models listed on your workspace are what members can access through both the chat interface and the API.

- Models are hosted on **AWS Bedrock** and **on-premise** infrastructure — students never interact with external providers directly.
- To request a specific model, contact **ai-verde-support@cyverse.org**.
- For a full list of currently available models, see [Current Models](../models-current.md).

### Bring Your Own (BYO) Model

You can bring your own commercial or third-party LLM and share access with your workspace members. This is useful if your research or coursework requires a specific model not already on the platform. Reach out to the AI Assistant team to set this up.

## Budget Management

Budgets control how much your workspace can spend on model usage. The budget is set by CyVerse, but you have visibility into how it's being used.

- **Set per-member limits** — Cap how much any single member can spend, preventing one student from consuming a disproportionate share.
- **Request budget increases** — If you're running low before the semester ends, contact **ai-verde-support@cyverse.org**.

!!! note
    You cannot increase the total workspace budget yourself — this requires a request to the CyVerse team.

<!-- Screenshot suggestion: the budget/usage section of the workspace showing per-member usage -->

### Planning Around Your Budget

- **Check usage before big assignments.** If you're assigning a project that requires heavy model usage, verify you have enough budget remaining.
- **Set per-member limits early.** This prevents surprises where a few students exhaust the budget before others get to use it.
- **Monitor mid-semester.** A quick check halfway through the term can catch trends before they become problems.

## Member Roles

| Role | Can Chat | Can Use API Key | Can Manage Members | Can Edit Settings |
|------|----------|-----------------|-------------------|-------------------|
| **Instructor** | Yes | Yes | Yes | Yes |
| **TA** | Yes | Yes | Limited | No |
| **Student** | Yes | Yes | No | No |

## Common Questions

**Can I have multiple instructors on one workspace?**
:   Yes. Add them as members with the **Instructor** role. All instructors have full management access.

**What happens when the end date passes?**
:   Members lose access to the workspace. API keys stop working. The workspace and its data are preserved — you can reactivate it by updating the end date and setting the status back to Active.

**I changed the available models but a student still sees the old list.**
:   Ask the student to sign out and sign back in, or refresh their dashboard. Model changes take effect immediately but may require a page refresh to appear.

**Can I duplicate a workspace for next semester?**
:   Not directly from the dashboard. Contact **ai-verde-support@cyverse.org** and they can set up a new workspace with similar settings.
