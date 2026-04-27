# 📂 Concato v3.0
Concato is a high-performance, local-first utility designed to bridge the gap between complex local codebases and LLM context windows. It intelligently fragments your source code into AI-ready parts while ensuring your data never leaves your browser.

---

# 🚀 Quick Start
Select Directory: Grant permission to your project folder using the "Select Directory" button.

Choose Orchestration: Select a preset (Security, Refactor, etc.) or write a custom Master Prompt.

Filter: Use the sidebar to include or exclude specific files.

Copy/Download: Grab the generated Part and paste it into your AI of choice.

---

# 🛠 Key Technical Features
1. Web File System Access API
Unlike traditional tools that use file inputs, Concato uses window.showDirectoryPicker().

Why it matters: This allows the tool to maintain a handle on your local directory, enabling real-time updates without re-uploading files when you change your code.

2. Smart Fragment Slicing
The code uses a newline-aware slicing logic to prevent breaking functions or logic blocks mid-sentence:

```JavaScript
// Smart slicing logic
let end = i + MAX_CHARS;
if (end < combined.length) {
    const lastNewline = combined.lastIndexOf('\n', end);
    if (lastNewline > i) end = lastNewline; // Ensure we don't cut a line in half
}
```

3. Dynamic "Stress Line" Indicator
The UI features a visual capacity bar (#stressLine) that changes color based on the fragment size relative to the MAX_CHARS limit (80,000 characters).

Green/Yellow: Safe context window.

Red + Pulse Animation: Warning that the fragment is nearing the limit, which might cause the LLM to "forget" earlier context or lag.

---


# 📋 Usage Example
Scenario: Performing a Security Audit
If you want to check your Laravel or Express.js backend for vulnerabilities:

- Open Concato.

- Click Select Directory and choose your src or app folder.

- Select 🛡️ Security Audit from the Orchestration dropdown.

- Concato will automatically prepend your fragment with:

- SYSTEM INSTRUCTION: Analyze this code for security vulnerabilities, SQL injections, or leaked API keys. Suggest immediate fixes.

- Check the Stress Line. If it's red, switch to PART 2 to send the remaining logic.

---

# ⚙️ Configuration & Security
- Zero-Server Footprint: All processing occurs in the browser's RAM.

- Default Exclusions: Automatically ignores "noise" directories to save context: node_modules, vendor, .git, storage, dist, etc.

- Token Estimation: Uses a 1:4 ratio (Characters to Tokens) to provide a safe estimate for models like GPT-4 or Claude 3.

---

# 💻 Local Development
To run this locally, simply clone the repo and open index.html in a modern browser (Chrome/Edge recommended for File System API support).

```Bash
git clone https://github.com/Farrelius/concato.git
cd concato
```
# No installation required - Pure HTML/JS/Tailwind

---
