# Opencodian Installation Guide

## Prerequisites

### 1. OpenCode CLI

Opencodian requires OpenCode CLI to be installed and accessible.

**Check if installed:**

```bash
opencode --version
```

If not installed, download from [opencode.ai](https://opencode.ai).

**Windows installation:**

```powershell
# Using PowerShell
irm opencode.ai/install.ps1 | iex

# Or manually download from:
# https://github.com/opencode-ai/opencode/releases
```

**Verify installation:**

```bash
opencode --version
# Should show something like: 1.14.41
```

### 2. OpenCode Configuration

Ensure OpenCode has valid model configuration:

```bash
# Check config file exists
cat ~/.config/opencode/opencode.json
```

The config file should contain valid provider and model settings.

### 3. Node.js

Requires Node.js 18+ or Bun:

```bash
node --version
# or
bun --version
```

---

## Installation

### Option 1: From Source

1. **Clone or download this repository:**

```bash
git clone https://github.com/YOUR_USERNAME/opencodian.git
cd opencodian
```

2. **Install dependencies and build:**

```bash
npm install
npm run build
```

3. **Copy to Obsidian plugins folder:**

```bash
# macOS/Linux
cp main.js manifest.json /path/to/your/vault/.obsidian/plugins/opencodian/

# Windows PowerShell
Copy-Item "main.js" "C:\path\to\your\vault\.obsidian\plugins\opencodian\" -Force
Copy-Item "manifest.json" "C:\path\to\your\vault\.obsidian\plugins\opencodian\" -Force
```

**Typical Obsidian plugin locations:**

| Platform | Path |
|----------|------|
| Windows | `%APPDATA%\obsidian\YourVault\.obsidian\plugins\` |
| macOS | `~/Library/Application Support/obsidian/YourVault/.obsidian/plugins/` |
| Linux | `~/.config/obsidian/YourVault/.obsidian/plugins/` |

### Option 2: Manual Download

1. Download `main.js` and `manifest.json` from [Releases](https://github.com/YOUR_USERNAME/opencodian/releases)
2. Create folder: `<vault>/.obsidian/plugins/opencodian/`
3. Copy both files to that folder

---

## Enable the Plugin

1. Open Obsidian
2. Go to **Settings** → **Community plugins**
3. Click **Reload** button
4. Find **"Opencodian"** and enable it

---

## Verify Installation

### 1. Check plugin files exist

```
<vault>/.obsidian/plugins/opencodian/
├── main.js
└── manifest.json
```

### 2. Test the plugin

1. Click the robot icon in the left ribbon
2. Or use command palette: `Ctrl/Cmd + P` → "Opencodian: Open Chat"
3. A sidebar chat view should appear
4. Status bar should show "● Connected"

---

## Configuration

### Model Selection

Go to **Settings** → **Opencodian** → **Models** to configure visible models.

### Categories

Go to **Settings** → **Opencodian** → **Categories** to set model routing for different task types.

### Skills

Create skills in:
- `<vault>/.opencode/skills/my-skill/SKILL.md`
- `~/.config/opencode/skills/my-skill/SKILL.md`

---

## Development

### Watch mode

```bash
npm run dev
```

### Manual reload after changes

After rebuilding, reload the plugin in Obsidian:
- Press `Ctrl+R` (or `Cmd+R` on macOS)
- Or restart Obsidian

---

## Troubleshooting

### Plugin not showing in Community plugins list

1. Ensure `manifest.json` is copied correctly
2. Click "Reload" button in Settings → Community plugins
3. Check the `.obsidian/plugins/opencodian/` directory exists

### Status shows "○ Disconnected"

1. Check OpenCode CLI is installed: `opencode --version`
2. Check OpenCode is in PATH
3. In Settings → Opencodian, set the correct CLI Path

### Build fails

```bash
# Clean and reinstall
rm -rf node_modules
npm install
npm run build
```

### Windows UNC path issues

If your vault is on a network drive, copy the project to a local directory before building:

```powershell
# Copy to local temp directory
$src = "\\network\path\Opencodian"
$dest = "C:\Temp\opencodian-build"
Copy-Item -Path "$src\*" -Destination $dest -Recurse -Force

# Build locally
cd $dest
npm install
npm run build

# Copy result to vault
Copy-Item "main.js" "\\network\path\.obsidian\plugins\opencodian\" -Force
Copy-Item "manifest.json" "\\network\path\.obsidian\plugins\opencodian\" -Force
```

---

## Uninstall

1. Go to **Settings** → **Community plugins** → Disable "Opencodian"
2. Delete the plugin folder:
   ```bash
   # macOS/Linux
   rm -rf /path/to/your/vault/.obsidian/plugins/opencodian
   
   # Windows
   Remove-Item "C:\path\to\your\vault\.obsidian\plugins\opencodian" -Recurse -Force
   ```

---

## Directory Structure

After installation:

```
your-vault/
├── .obsidian/
│   └── plugins/
│       └── opencodian/
│           ├── main.js
│           └── manifest.json
├── .opencode/
│   └── skills/           # Custom skills (optional)
│       └── my-skill/
│           └── SKILL.md
└── ... (your vault content)
```
