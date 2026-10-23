# Using Claude for Outlook with AI Assistant

**Claude for Outlook** is Anthropic's add-in for Microsoft Outlook. It adds a Claude sidebar to Outlook so you can triage emails, draft replies, summarize threads, and read attachments. Configure it to connect through the AI Assistant gateway using your API key instead of signing in with an Anthropic account.

## Prerequisites

1. [Obtain your AI Assistant API key](api-key.md).
2. Access to Outlook on desktop (Windows or Mac) or on the web.
3. Your University of Arizona Microsoft account to sign in to Microsoft Marketplace and acquire the add-in.

## 1. Install the add-in

1. Go to the [Claude for Outlook add-in](https://marketplace.microsoft.com/en-us/product/wa200010724) on Microsoft Marketplace (by **Claude by Anthropic for Office**) and click **Get it now**.

    ![Claude for Outlook listing on Microsoft Marketplace with the Get it now button](../assets/claude_outlook_marketplace_product_dark.png#only-dark){: style="width:100%; height:auto;"}
    ![Claude for Outlook listing on Microsoft Marketplace with the Get it now button](../assets/claude_outlook_marketplace_product.png#only-light){: style="width:100%; height:auto;"}

2. Sign in to Microsoft Marketplace with your University of Arizona Microsoft account.

    ![Sign in to Microsoft Marketplace dialog](../assets/claude_outlook_marketplace_signin_dark.png#only-dark){: style="width:100%; height:auto;"}
    ![Sign in to Microsoft Marketplace dialog](../assets/claude_outlook_marketplace_signin.png#only-light){: style="width:100%; height:auto;"}

3. On the launch page, click **Open in Outlook Web**. The add-in is now installed for your University of Arizona Microsoft account and available the next time you open Outlook.

    ![Claude for Outlook launch page with Open Outlook Web button](../assets/claude_outlook_store_launch_dark.png#only-dark){: style="width:100%; height:auto;"}
    ![Claude for Outlook launch page with Open Outlook Web button](../assets/claude_outlook_store_launch.png#only-light){: style="width:100%; height:auto;"}

## 2. Open Claude in Outlook

### Desktop (Windows or Mac)
 Click the **...** (See more items) button near the right edge of the ribbon and select **Claude** from the **Claude** group at the bottom of the menu.

![Outlook desktop ribbon overflow menu showing the Claude group](../assets/claude_outlook_desktop_ribbon_overflow_dark.png#only-dark){: style="width:100%; height:auto;"}
![Outlook desktop ribbon overflow menu showing the Claude group](../assets/claude_outlook_desktop_ribbon_overflow.png#only-light){: style="width:100%; height:auto;"}

!!! tip
    You can pin the Claude app to your toolbar for easier access.

    To do this, first click the **...** (See more items) button near the right edge of the ribbon and select "Customize toolbar".

    ![Outlook desktop ribbon overflow menu showing the customize toolbar button](../assets/claude_outlook_desktop_customize_toolbar_dark.png#only-dark){: style="width:100%; height:auto;"}
    ![Outlook desktop ribbon overflow menu showing the customize toolbar button](../assets/claude_outlook_desktop_customize_toolbar.png#only-light){: style="width:100%; height:auto;"}

    Then, in the dialog that opens, click and hold the Claude app and drag it up to the toolbar preview at the top of the dialog to pin the app to the toolbar.
    ![Dragging Claude app into toolbar in outlook desktop](../assets/claude_outlook_desktop_customize_toolbar_drag_dark.png#only-dark){: style="width:100%; height:auto;"}
    ![Dragging Claude app into toolbar in outlook desktop](../assets/claude_outlook_desktop_customize_toolbar_drag.png#only-light){: style="width:100%; height:auto;"}

    You should now have the Claude app in your toolbar.
    ![Claude app in toolbar in outlook desktop](../assets/claude_outlook_desktop_toolbar_with_claude_dark.png#only-dark){: style="width:100%; height:auto;"}
    ![Claude app in toolbar in outlook desktop](../assets/claude_outlook_desktop_toolbar_with_claude.png#only-light){: style="width:100%; height:auto;"}



### Web (Outlook on the web)

To access Claude, first, click the "Enhance Outlook with Apps" button (looks like a waffle)

![Enhance Outlook with Apps button in Outlook web](../assets/claude_outlook_web_enhance_outlook_button_dark.png#only-dark){: style="width:100%; height:auto;"}
![Enhance Outlook with Apps button in Outlook web](../assets/claude_outlook_web_enhance_outlook_button.png#only-light){: style="width:100%; height:auto;"}

Then, click the "Claude for Outlook" button in the menu that appears
![Claude for Outlook in Outlook web button](../assets/claude_outlook_web_button_dark.png#only-dark){: style="width:100%; height:auto;"}
![Claude for Outlook in Outlook web button](../assets/claude_outlook_web_button.png#only-light){: style="width:100%; height:auto;"}

!!! tip
    You can pin the Claude app to your toolbar for easier access.

    To do this, right click on the "Claude for Outlook" button and select "pin" in the menu that appears

    ![Outlook web pin Claude for outlook button](../assets/claude_outlook_web_pin_button_dark.png#only-dark){: style="width:100%; height:auto;"}
    ![Outlook web pin Claude for outlook button](../assets/claude_outlook_web_pin_button.png#only-light){: style="width:100%; height:auto;"}


    You should now have the Claude app in your toolbar and the top right corner of your messages.
    ![Claude app in toolbar and top right of messages in outlook web](../assets/claude_outlook_web_in_toolbar_dark.png#only-dark){: style="width:100%; height:auto;"}
    ![Claude app in toolbar and top right of messages in outlook web](../assets/claude_outlook_web_in_toolbar.png#only-light){: style="width:100%; height:auto;"}

## 3. Connect to AI Assistant

The first time you open the Claude sidebar, it prompts you to sign in.

![Claude sidebar first-run screen with Log in, Sign up, and Cloud provider or gateway options](../assets/claude_outlook_web_sidebar_login_dark.png#only-dark){: style="width:100%; height:auto;"}
![Claude sidebar first-run screen with Log in, Sign up, and Cloud provider or gateway options](../assets/claude_outlook_web_sidebar_login.png#only-light){: style="width:100%; height:auto;"}

1. Click **Cloud provider or gateway** instead of **Log in** or **Sign up**.
2. On the **Connect another way** screen, keep the **Gateway** tab selected.
3. Set **Gateway URL** to `https://ai-assistant.responsibleai.arizona.edu`.
4. Set **Token** to your AI Assistant API key.
5. Click **Continue**.

    ![Connect another way screen with Gateway URL and Token fields](../assets/claude_outlook_web_connect_gateway_dark.png#only-dark){: style="width:100%; height:auto;"}
    ![Connect another way screen with Gateway URL and Token fields](../assets/claude_outlook_web_connect_gateway.png#only-light){: style="width:100%; height:auto;"}


## 4. Start using Claude

Once connected, the sidebar shows a prompt box and a set of starter skills, such as `/triage`, `/meeting-prep`, `/summarize-thread`. Type a single "/" to show all available skills and their descriptions.

![Claude sidebar showing starter skills and a prompt box](../assets/claude_outlook_web_skills_dark.png#only-dark){: style="width:100%; height:auto;"}
![Claude sidebar showing starter skills and a prompt box](../assets/claude_outlook_web_skills.png#only-light){: style="width:100%; height:auto;"}

Type a prompt, or click one of the starter skills, then press **Enter** or click the send button.

## Update your API key

In the Claude sidebar, click the **...** (more options) button near the top-right corner and select **Logout**.

![Claude sidebar more options menu with Settings, Download Transcript, and Logout](../assets/claude_outlook_web_logout_dark.png#only-dark){: style="width:100%; height:auto;"}
![Claude sidebar more options menu with Settings, Download Transcript, and Logout](../assets/claude_outlook_web_logout.png#only-light){: style="width:100%; height:auto;"}

Then repeat [Connect to AI Assistant](#3-connect-to-ai-assistant) with your new AI Assistant API key.
