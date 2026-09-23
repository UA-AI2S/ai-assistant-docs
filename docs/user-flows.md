# AI Assistant User Flows

This page documents the primary user flows in the AI Assistant web interface. These flows cover the features available at launch — the **Settings** and **API Key** workspace tabs, along with login, navigation, and profile management.

---

## Login & Authentication

| # | Flow | Action | Expected Result |
|---|------|--------|-----------------|
| 1 | Visit AI Assistant | Navigate to [chat.cyverse.ai](https://chat.cyverse.ai/) | Public landing page loads with "AI Assistant" branding, Sign In button, Docs link, and light/dark mode toggle |
| 2 | Sign in | Click **Sign In** → select your institution → log in with your NetID credentials | Redirected to the AI Assistant home dashboard |
| 3 | Access without account | Sign in with credentials not associated with any workspace | Dashboard shows "You don't have access yet" with a **Get Access** button and **Contact Support** option |
| 4 | Toggle dark mode (public) | Click the sun/moon icon in the top-right of the public page | Page switches between light and dark color schemes |
| 5 | View documentation (public) | Click **Docs** in the top-right corner | Opens the AI Assistant documentation site in a new tab |

---

## Home Dashboard

| # | Flow | Action | Expected Result |
|---|------|--------|-----------------|
| 1 | View workspaces | After signing in, land on `/home` | Dashboard displays **Recently Visited** section (if any) and **My Workspaces** grid with workspace cards |
| 2 | Search workspaces | Type a workspace name in the search field | Workspace list filters to match the search query |
| 3 | Paginate workspaces | Scroll through workspaces when more than 9 exist | Pagination controls appear; navigate between pages of workspace cards |
| 4 | Open a workspace | Click a workspace card | Navigates into the workspace, landing on the **API Key** tab (or **Settings**, depending on configuration) |
| 5 | View workspace usage | Observe the progress bar on a workspace card | Shows the workspace's current usage relative to its budget allocation |
| 6 | Contact support | Click the support chat icon (bottom-right corner) | Intercom support chat opens for messaging the support team |

---

## Profile Management

| # | Flow | Action | Expected Result |
|---|------|--------|-----------------|
| 1 | Open profile menu | Click your avatar/initials icon in the top-right navigation bar | Dropdown menu appears with your name, email, and options: Your Profile, Dark Mode toggle, Contact Support, Sign Out |
| 2 | View profile | Select **Your Profile** from the dropdown | Profile page loads showing your name, username, email, and organization |
| 3 | Edit profile | On the profile page, click **Edit** | First name and last name fields become editable; username, email, and organization remain read-only |
| 4 | Save profile changes | Edit your name and click **Save** | Name is updated; profile returns to view mode with the new name displayed |
| 5 | Cancel profile edit | Click **Cancel** while editing | Changes are discarded; profile returns to view mode with original values |
| 6 | Switch to dark mode | From the profile dropdown, click **Switch to Dark Mode** | The entire UI switches to a dark color scheme; the toggle label updates to "Switch to Light Mode" |
| 7 | Sign out | From the profile dropdown, click **Sign Out** | You are signed out and returned to the public login page |

---

## Workspace Navigation

| # | Flow | Action | Expected Result |
|---|------|--------|-----------------|
| 1 | Navigate workspace tabs | Inside a workspace, click the tab bar items | Switches between **API Key** and **Settings** tabs |
| 2 | Return home | Click the saguaro cactus icon (top-left) from any workspace page | Returns to the home dashboard |
| 3 | Switch workspaces | Click the workspace name dropdown in the workspace header | Searchable list of your workspaces appears; selecting one navigates directly to that workspace |
| 4 | Search workspace switcher | Type in the workspace switcher dropdown's search field | Workspace list filters to match the search query |
| 5 | Open documentation | Click the **Docs** (book icon) button in the workspace header | Opens the AI Assistant documentation site in a new tab |

---

## API Key

| # | Flow | Action | Expected Result |
|---|------|--------|-----------------|
| 1 | View API key | Navigate to the **API Key** tab in a workspace | Page displays your API key (hidden by default), the Base URL, and a list of available models |
| 2 | Copy API key | Click the **copy** button next to the API key field | API key is copied to your clipboard |
| 3 | Copy Base URL | Click the **copy** button next to the Base URL field | Base URL is copied to your clipboard |
| 4 | Regenerate API key | Click **Regenerate API Key** → confirm in the modal | A new API key is generated and displayed; the previous key is invalidated immediately |
| 5 | View available models | Scroll to the **Available Models** section on the API Key page | Lists all LLM models available for use in the workspace |
| 6 | Access API documentation | Click the API documentation link on the API Key page | Opens the API documentation with integration guides |

---

## Settings — General (All Members)

| # | Flow | Action | Expected Result |
|---|------|--------|-----------------|
| 1 | View workspace details | Navigate to **Settings** → **General Settings** | Displays the workspace name, description, and start/end dates (for team workspaces) |
| 2 | View LLM models | Scroll to the **LLM Models** section on the General Settings page | Lists the models enabled for this workspace and indicates which is set as the default |

---

## Settings — General (Admin Only)

| # | Flow | Action | Expected Result |
|---|------|--------|-----------------|
| 1 | Edit workspace details | On General Settings, click the **Edit** button on the Workspace Details card | Modal opens with editable fields for workspace name, description, and start/end dates |
| 2 | Save workspace edits | Modify fields in the edit modal and click **Apply Changes** | Workspace details are updated; changes reflect immediately on the settings page |
| 3 | Cancel workspace edit | Click the **X** or **Cancel** in the edit modal | Modal closes with no changes applied |
| 4 | Manage LLM models | In the LLM Models section, click to add or remove models | Opens a model selection interface where admins can enable/disable available models for the workspace |
| 5 | Set default model | Click the star icon next to a model in the LLM Models section | That model is marked as the default for new conversations in the workspace |

---

## Settings — Members (Admin Only)

| # | Flow | Action | Expected Result |
|---|------|--------|-----------------|
| 1 | View members | Navigate to **Settings** → **Members** | Displays a table of all workspace members with their name, role, and a member count badge in the header |
| 2 | Search members | Type a name in the search field above the member table | Member list filters to match the query |
| 3 | Filter by role | Use the role dropdown filter (All, Member, Admin) | Member list filters to show only members with the selected role |
| 4 | Add single member | Click **Add Members** → **Add single member** | Modal opens; enter the member's University of Arizona NetID and select a role (Member or Admin), then click **Add Members** |
| 5 | Add members from CSV | Click **Add Members** → **Upload from CSV** | Modal opens with a drag-and-drop upload area; optionally download the **CSV template** first to see the required format, then upload the completed file and click **Add Members** |
| 6 | Edit member role | Click the edit icon next to a member in the table | Modal opens to switch between Member and Admin roles; confirm to save |
| 7 | Remove member | Click the remove icon next to a member | Confirmation dialog appears; confirm to remove the member from the workspace |

---

## Accessibility Notes from Testing

The following accessibility observations were identified during QA testing and are being addressed:

| Area | Issue | Status |
|------|-------|--------|
| Home — Navigation Bar | VoiceOver reads over the page without focusing on the main logo; activates a "skip to main content" dropdown unexpectedly | In progress |
| Home — Workspace Card | When tabbing with VoiceOver, the workspace info tooltip reads as a generic "More Info Group" | In progress |
| Home — Support Button | VoiceOver reads "Contact support group, image image" instead of a descriptive label | In progress |
| API Key — Copy Buttons | No visual indicator that the API key or URL has been copied after clicking copy | Fixed ([PR #201](https://github.com/cyverse/wilma-ui/pull/201)) |
| API Key — Copy Buttons | VoiceOver reads the horizontal splitter image as a decoration rather than skipping it | Fixed ([PR #201](https://github.com/cyverse/wilma-ui/pull/201)) |
| Settings — Edit Workspace | Start Date & End Date calendar is inaccessible via keyboard; calendar modal shifts position when tabbing | Fixed ([PR #193](https://github.com/cyverse/wilma-ui/pull/193)) |
| Settings — Edit Workspace | Workspace name changes don't reflect until page refresh | Fixed ([PR #190](https://github.com/cyverse/wilma-ui/pull/190)) |
| Members — Add Single Member | When the modal opens, keyboard focus does not move into the modal; user must tab through other elements first | Fixed ([PR #203](https://github.com/cyverse/wilma-ui/pull/203)) |
| Members — Add Members | Interface does not indicate whether the member was verified, invited, or granted access immediately | Under review |
| Members — Upload from CSV | Alert says members were added, but they are not visible in the list | Under review |
