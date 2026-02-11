**EXAM KEY POINTS: Installing and Authenticating Claude Code**

---

**TWO PROFESSIONAL PATHS**
- **Official:** $20/mo (Pro) or $200/mo (Max) - Anthropic models, direct integration
- **Free/Minimal:** $0 or pay-as-you-go - Any LLM backend (Gemini, GPT, local)
- Both teach identical skills (subagents, skills, MCP, hooks)

---

**PREREQUISITES (MUST KNOW)**
1. **Terminal Access Required**
2. **Claude Account:** Subscription OR Console API OR Enterprise
3. **System Requirements:**
   - macOS 13+
   - Windows 10+
   - Linux: Ubuntu 20.04+/Debian 10+
   - 8GB RAM minimum
4. **Optional:** Node.js 18+ (for npm install - deprecated)

---

**INSTALLATION COMMANDS BY PLATFORM**

**Windows (MUST know bash requirement):**
- Requires WSL OR Git for Windows (bash-compatible shell)
- **Method 1 (RECOMMENDED):** WSL
  - Install WSL: `wsl --install` (PowerShell as Admin)
  - Then: `curl -fsSL https://claude.ai/install.sh | bash`
- **Method 2:** PowerShell: `irm https://claude.ai/install.ps1 | iex`
- **Method 2:** CMD: `curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd`

**macOS:**
- **Homebrew:** `brew install --cask claude-code`
- **Shell:** `curl -fsSL https://claude.ai/install.sh | bash`

**Linux:**
- `curl -fsSL https://claude.ai/install.sh | bash`

**npm (Deprecated but testable):**
- `npm install -g @anthropic-ai/claude-code`
- Requires Node.js 18+

---

**VERIFICATION COMMAND (CRITICAL)**
```bash
claude --version
```
Expected: `X.X.XX (Claude Code)`

---

**THREE AUTHENTICATION METHODS (DECISION TREE)**

**Method 1: Claude App (MOST COMMON)**
- For: Pro/Max/Team subscription users
- Run: `claude` → Select Option 1 → Browser auth
- Benefits: Unified access, simpler flow

**Method 2: Console API**
- For: API credits, pay-per-use
- Run: `claude` → Select Option 2 → Paste API key
- Get key from: console.anthropic.com/settings/keys
- ⚠️ Uses API billing, NOT subscription credits

**Method 3: Enterprise**
- For: Bedrock/Vertex AI/Foundry
- Contact enterprise admin for config

---

**IMPORTANT COMMANDS (TESTABLE)**
- **Check version:** `claude --version`
- **System diagnostics:** `claude doctor`
- **Manual update:** `claude update`
- **Disable auto-update:** 
  - macOS/Linux: `export DISABLE_AUTOUPDATER=1`
  - Windows: `$env:DISABLE_AUTOUPDATER=1`
- **Test setup:** `claude "Hello! Can you confirm Claude Code is working?"`

---

**UNINSTALLATION COMMANDS**

**macOS/Linux/WSL:**
```bash
rm -f ~/.local/bin/claude
rm -rf ~/.claude-code
rm ~/.claude.json
```

**Windows PowerShell:**
```powershell
Remove-Item -Path "$env:LOCALAPPDATA\Programs\claude-code" -Recurse -Force
Remove-Item -Path "$env:LOCALAPPDATA\Microsoft\WindowsApps\claude.exe" -Force
```

**Homebrew:** `brew uninstall --cask claude-code`

**npm:** `npm uninstall -g @anthropic-ai/claude-code`

---

**SECURITY BEST PRACTICES (CRITICAL FOR EXAM)**

1. **File System Access:**
   - Start sessions in PROJECT directories, NOT system directories
   - Review ALL file changes before approving

2. **Command Execution:**
   - Review ALL commands, especially `sudo`
   - Claude asks approval for destructive actions

3. **Cost Management (Console API):**
   - Set usage limits: console.anthropic.com/settings/limits
   - Monitor token usage (shown after each interaction)

---

**KEY DIFFERENCES TO MEMORIZE**

| Feature | WSL | Git Bash |
|---------|-----|----------|
| Environment | Full Linux | Minimal bash |
| Best for | Full compatibility | Quick setup |
| Recommended by | Anthropic | Alternative |

| Auth Type | Cost Model | Best For |
|-----------|------------|----------|
| Subscription | Fixed monthly | Regular users |
| Console API | Pay-per-use | Developers, variable usage |
| Enterprise | Dedicated capacity | Large orgs, compliance |

---

**EXAM GOTCHAS**
- ⚠️ Windows requires bash shell (WSL or Git for Windows)
- ⚠️ npm installation is DEPRECATED
- ⚠️ Console API ≠ Subscription (different billing)
- ⚠️ Always verify with `claude doctor` after install
- ⚠️ Terminal comfort = skill multiplier
- ⚠️ Location restrictions apply (check during signup)

---

**WORKFLOW TO REMEMBER**
1. Install Claude Code
2. Run `claude --version` (verify)
3. Run `claude` (authenticate)
4. Run `claude doctor` (diagnostics)
5. Test with safe command
6. Start in project directories only