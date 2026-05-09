# 📡 EasyNetway — Network Control Panel

A mobile-first network device management panel for monitoring OLT stations, MikroTik routers, and managed switches across Ozar, Jaulke, Dindori, and PB areas.

---

## 🚀 Features

- **26 Devices** — MikroTik routers, OLT stations, managed switches
- **Live Status** — Triple-probe detection (fetch + img + WebSocket)
- **Auto-refresh** — Status check every 45 seconds
- **Backup IP** — Auto-switch to backup IP if main is offline
- **Search & Filter** — Search by device name, IP, or tag
- **Bilingual** — English + Marathi (मराठी) labels
- **Mobile-first** — PWA-ready, works on iOS & Android

---

## 📂 Project Structure

```
easynetway/
├── index.html              # Main app (single-file PWA)
├── .mcp.json               # MCP config for Claude Code (project-level)
├── claude_desktop_config.json  # MCP config for Claude Desktop app
├── README.md
└── .github/
    └── workflows/
        └── deploy.yml      # Optional: GitHub Pages deploy
```

---

## 🤖 GitHub MCP Setup (Connect Claude to this Repo)

This lets Claude read/write files, manage issues, create PRs, and more — directly from chat.

### Step 1 — Generate a GitHub Token

1. Go to → https://github.com/settings/tokens/new
2. Select scopes: `repo`, `read:org`, `read:user`
3. Click **Generate token** and copy it

### Step 2 — For Claude Desktop App

Copy `claude_desktop_config.json` content into your Claude Desktop config file:

| OS      | Config File Path |
|---------|-----------------|
| Windows | `%APPDATA%\Claude\claude_desktop_config.json` |
| macOS   | `~/Library/Application Support/Claude/claude_desktop_config.json` |
| Linux   | `~/.config/Claude/claude_desktop_config.json` |

Replace `YOUR_GITHUB_TOKEN_HERE` with your actual token.

### Step 3 — For Claude Code (CLI)

The `.mcp.json` file in this repo root is auto-detected by Claude Code.

```bash
# Install Claude Code if not already installed
npm install -g @anthropic-ai/claude-code

# In the project folder, Claude Code will auto-load .mcp.json
cd easynetway
claude
```

Replace `YOUR_GITHUB_TOKEN_HERE` in `.mcp.json` with your actual token.

### Step 4 — Verify Connection

In Claude, ask:
> "List the files in my easynetway GitHub repository"

Claude will use the GitHub MCP to browse your repo live.

---

## 🌐 Deploy to GitHub Pages

```bash
# 1. Create a new GitHub repository
git init
git remote add origin https://github.com/YOUR_USERNAME/easynetway.git

# 2. Push the code
git add .
git commit -m "Initial commit — EasyNetway Network Panel"
git push -u origin main

# 3. Enable GitHub Pages
# Go to repo → Settings → Pages → Source: main branch / root
# Your app will be live at: https://YOUR_USERNAME.github.io/easynetway/
```

---

## 📱 Install as PWA (Mobile)

On your phone browser:
- **Android (Chrome):** Menu → "Add to Home Screen"
- **iOS (Safari):** Share → "Add to Home Screen"

---

## 🛠️ Customization

To add a new device, add a card inside the relevant section in `index.html`:

```html
<a class="card c-teal" href="https://IP:PORT" target="_blank"
   data-url="https://IP:PORT" data-tags="your tags here">
  <div class="card-icon i-teal">📡</div>
  <div class="card-info">
    <h3>Device Name / डिव्हाइसचे नाव</h3>
    <div class="status-row">
      <span class="status-dot checking"></span>
      <span class="status-lbl">...</span>
    </div>
    <p>IP:PORT</p>
  </div>
  <span class="card-arrow">➜</span>
</a>
```

Also update the total device count in the topbar (`26` → new count).

---

## 📄 License

MIT — Free to use and modify.
