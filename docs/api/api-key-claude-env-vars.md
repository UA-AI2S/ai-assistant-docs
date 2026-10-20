# Saving Claude Code environment variables

The setup guides ask you to run lines like this in a terminal:

=== "macOS and Linux"

    ```bash
    export ANTHROPIC_AUTH_TOKEN="<your-ai-assistant-api-key>"
    ```

=== "Windows"

    ```powershell
    $env:ANTHROPIC_AUTH_TOKEN = "<your-ai-assistant-api-key>"
    ```

Each line sets one environment variable, a named value that Claude Code reads when it starts. The value lasts only as long as that terminal window, so the next window you open knows nothing about it.

To keep the settings, add them to a startup file that your terminal runs automatically every time it opens.

Use the block from the guide you followed: [Bedrock](api-key-claude.md#1-configure-bedrock) for Claude models, or the [Anthropic-compatible endpoint](api-key-claude-non-anthropic.md#1-configure-the-anthropic-compatible-endpoint) for non-Anthropic models. Save only one of them, and replace any older Claude Code configuration already in the file. The examples below use the Bedrock configuration.

## Save the configuration

=== "macOS and Linux"

    Open `~/.zshrc` for Zsh, the default shell on macOS, or `~/.bashrc` for Bash:

    ```bash
    nano ~/.zshrc
    ```

    Add the configuration to the end of the file and save it:

    ```bash
    unset ANTHROPIC_BASE_URL ANTHROPIC_API_KEY AWS_BEARER_TOKEN_BEDROCK

    export ANTHROPIC_AUTH_TOKEN="<your-ai-assistant-api-key>"
    export ANTHROPIC_BEDROCK_BASE_URL="https://ai-assistant.responsibleai.arizona.edu/bedrock"
    export CLAUDE_CODE_SKIP_BEDROCK_AUTH=1
    export CLAUDE_CODE_USE_BEDROCK=1

    export ANTHROPIC_DEFAULT_OPUS_MODEL="<opus-model-id>"
    export ANTHROPIC_DEFAULT_SONNET_MODEL="<sonnet-model-id>"
    export ANTHROPIC_DEFAULT_HAIKU_MODEL="<haiku-model-id>"
    export ANTHROPIC_MODEL="$ANTHROPIC_DEFAULT_SONNET_MODEL"
    ```

    Keep the `unset` line. It clears settings from other setups whenever a terminal starts.

    Apply the file to your current terminal, then check the values:

    ```bash
    source ~/.zshrc
    env | grep -E '^(ANTHROPIC|CLAUDE_CODE|AWS_BEARER)'
    ```

    On macOS, Bash reads `~/.bash_profile` rather than `~/.bashrc`. Either save the block there, or add `[ -f ~/.bashrc ] && source ~/.bashrc` to `~/.bash_profile`.

    If you run Claude Code under WSL on Windows, follow these steps inside the Linux distribution. Windows variables do not carry into it.

=== "Windows"

    PowerShell's startup file is called a profile. Create it if it does not exist, then open it:

    ```powershell
    if (-not (Test-Path $PROFILE)) { New-Item -ItemType File -Path $PROFILE -Force }
    notepad $PROFILE
    ```

    Add the configuration to the file and save it:

    ```powershell
    Remove-Item Env:ANTHROPIC_BASE_URL, Env:ANTHROPIC_API_KEY, Env:AWS_BEARER_TOKEN_BEDROCK -ErrorAction SilentlyContinue

    $env:ANTHROPIC_AUTH_TOKEN = "<your-ai-assistant-api-key>"
    $env:ANTHROPIC_BEDROCK_BASE_URL = "https://ai-assistant.responsibleai.arizona.edu/bedrock"
    $env:CLAUDE_CODE_SKIP_BEDROCK_AUTH = "1"
    $env:CLAUDE_CODE_USE_BEDROCK = "1"

    $env:ANTHROPIC_DEFAULT_OPUS_MODEL = "<opus-model-id>"
    $env:ANTHROPIC_DEFAULT_SONNET_MODEL = "<sonnet-model-id>"
    $env:ANTHROPIC_DEFAULT_HAIKU_MODEL = "<haiku-model-id>"
    $env:ANTHROPIC_MODEL = $env:ANTHROPIC_DEFAULT_SONNET_MODEL
    ```

    Keep the `Remove-Item` line. It clears settings from other setups whenever PowerShell starts.

    Apply the profile to your current session, then check the values:

    ```powershell
    . $PROFILE
    Get-ChildItem Env: | Where-Object Name -match '^(ANTHROPIC|CLAUDE_CODE|AWS_BEARER)'
    ```

    If PowerShell reports that running scripts is disabled, run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` and open the profile again.

    The profile applies to PowerShell only. To cover programs you start elsewhere, including VS Code, see [Programs started outside PowerShell](#programs-started-outside-powershell).

Start Claude Code from a new terminal and run `/status` to confirm it still connects to the AI Assistant.

## Programs started outside PowerShell

On Windows, a program started from the Start menu does not read your PowerShell profile. To set the variables for every program you start, add them to your Windows account: open **Settings**, search for **Edit environment variables for your account**, and add each name and value under **User variables**. Or run:

```powershell
setx ANTHROPIC_AUTH_TOKEN "<your-ai-assistant-api-key>"
setx ANTHROPIC_BEDROCK_BASE_URL "https://ai-assistant.responsibleai.arizona.edu/bedrock"
setx CLAUDE_CODE_SKIP_BEDROCK_AUTH "1"
setx CLAUDE_CODE_USE_BEDROCK "1"
setx ANTHROPIC_DEFAULT_OPUS_MODEL "<opus-model-id>"
setx ANTHROPIC_DEFAULT_SONNET_MODEL "<sonnet-model-id>"
setx ANTHROPIC_DEFAULT_HAIKU_MODEL "<haiku-model-id>"
setx ANTHROPIC_MODEL "<sonnet-model-id>"
```

Write the Sonnet model ID in full for `ANTHROPIC_MODEL`. `setx` stores values literally and cannot copy another variable's value.

These variables reach new programs only, so close and reopen your terminal, or restart VS Code, before starting Claude Code.

Delete leftover variables from other setups in the same **User variables** window, especially `ANTHROPIC_BASE_URL`, `ANTHROPIC_API_KEY`, and `AWS_BEARER_TOKEN_BEDROCK`, which can override your AI Assistant credential. Setting a variable to an empty string with `setx` does not remove it. To remove one from PowerShell, run `Remove-ItemProperty -Path HKCU:\Environment -Name ANTHROPIC_API_KEY`.

For the VS Code extension, configuring it directly is usually simpler. See [Using Claude Code in VS Code with AI Assistant](api-key-claude-vscode.md).

## Protect your API key

These files and variables store your key as readable text. The following steps are optional but recommended:

- On macOS and Linux, limit the startup file to your own account: `chmod 600 ~/.zshrc`.
- Keep startup files containing your key out of repositories and shared dotfiles.
- On Windows, remember that any program running as you can read your account variables.
