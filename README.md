# Antigravity CLI Statusline with Gemini Jokes

A dynamic, responsive statusline script for the **Google Antigravity CLI** featuring Gemini CLI witty loading phrases and jokes while the agent works.

## Features

- **Gemini CLI Jokes**: Automatically cycles witty loading phrases and programmer jokes when state is `thinking`, `working`, or `tool_use`.
- **Token Usage & Quota**: Displays token counts (`k`/`M`), context window usage bar, and rate limit quotas.
- **Git & Workspace Info**: Shows current workspace folder and active Git branch with dirty state indicator.
- **Responsive Layout**: Adapts gracefully to wide (≥120 cols), medium (80–119 cols), and narrow (<80 cols) terminal sizes.
- **Standard ANSI 16-color**: Works across light and dark terminal palettes without color clashes.

## Prerequisites

- `bash` (v4+)
- `jq`

```bash
# On macOS
brew install jq
```

## Quick Start

1. Clone this repository:
```bash
git clone https://github.com/AndrewMason7/antigravity-statusbar-jokes.git ~/.gemini/antigravity-statusbar-jokes
```

2. Make the script executable:
```bash
chmod +x ~/.gemini/antigravity-statusbar-jokes/statusline.sh
```

3. Enable it in your Antigravity CLI configuration (`~/.gemini/antigravity-cli/settings.json`):
```json
{
  "statusLine": {
    "type": "custom",
    "command": "~/.gemini/antigravity-statusbar-jokes/statusline.sh",
    "enabled": true
  }
}
```

## Preview / Test

Simulate a thinking state:
```bash
printf '{"agent_state":"thinking","context_window":{"used_percentage":25,"total_input_tokens":12000,"total_output_tokens":3000,"limit_tokens":1000000},"workspace_dir":"/Users/andrew/Desktop","vcs":{"branch":"main","dirty":false},"sandbox":{"enabled":true},"artifact_count":2,"subagents":[],"task_count":0,"model":{"display_name":"Gemini 3.8 Flash"},"terminal_width":120}' | ./statusline.sh
```

Output:
```text
◆ THINKING ╱ Gemini 3.8 Flash ╱ 🌱 main ╱ Reticulating splines  │  ctx ██░······· 15.0k/0 (25.0%) · 📦 2 · 👥 0 · ⚙️ 0 · 🛡️ ON
```

## License

Apache-2.0
