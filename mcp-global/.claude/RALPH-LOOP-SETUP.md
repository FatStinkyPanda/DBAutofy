# Ralph Loop Simplified Command Setup

## Goal
Execute Ralph Loop with predefined configuration from `.claude\ralph-loop.local.md` using a simple command like `/ralph` or `ralph`.

---

## Current Configuration
Your `.claude\ralph-loop.local.md` contains:
- **Max Iterations**: 20
- **Completion Promise**: "ROADMAP COMPLETE"
- **Prompt**: AI AUTONOMOUS DEVELOPMENT SCRIPT for Project-Firefly

---

## Solution Options

### Option 1: Create a Shell Script/Batch File (Recommended)

#### For Windows (PowerShell):
1. Create `start-ralph.ps1` in your project root:
```powershell
# start-ralph.ps1
$prompt = Get-Content ".claude\ralph-loop.local.md" -Raw
$prompt = $prompt -replace '---[\s\S]*?---\n', ''  # Remove frontmatter

# Execute Ralph Loop with the prompt
claude "/ralph-loop --max-iterations 20 --completion-promise 'ROADMAP COMPLETE' $prompt"
```

2. Make it executable and create an alias:
```powershell
# Add to your PowerShell profile
Set-Alias ralph "C:\Users\dbiss\Desktop\Projects\Personal\Cerebrum-3\start-ralph.ps1"
```

3. Usage:
```bash
ralph
```

#### For Windows (Batch File):
1. Create `start-ralph.bat` in your project root:
```batch
@echo off
type .claude\ralph-loop.local.md | claude /ralph-loop --max-iterations 20 --completion-promise "ROADMAP COMPLETE"
```

2. Usage:
```bash
start-ralph.bat
```

---

### Option 2: Create a Claude Skill (Advanced)

1. Create a new skill file: `.claude\skills\ralph-start.md`
```markdown
---
name: ralph-start
description: Start Ralph Loop with predefined configuration
---

# Ralph Loop Starter

This skill automatically loads the configuration from `.claude\ralph-loop.local.md` and starts the Ralph Loop.

**When invoked:**
1. Read `.claude\ralph-loop.local.md`
2. Extract the prompt (everything after frontmatter)
3. Execute `/ralph-loop` with max-iterations=20 and completion-promise="ROADMAP COMPLETE"
```

2. Usage:
```bash
/ralph-start
```

---

### Option 3: Use Hookify to Intercept Commands (Most Elegant)

1. Create a hookify rule: `.claude\hooks\ralph-shortcut.md`
```markdown
---
name: ralph-shortcut
trigger: on_user_message
pattern: ^(ralph|/ralph)$
active: true
---

# Ralph Loop Shortcut Hook

When user types "ralph" or "/ralph":
1. Read the file `.claude\ralph-loop.local.md`
2. Extract configuration (max_iterations, completion_promise)
3. Extract prompt content (everything after the frontmatter)
4. Execute the Ralph Loop skill with these parameters
```

2. Configure the hook:
```bash
/hookify:configure
```

3. Usage - simply type:
```bash
ralph
```

---

### Option 4: Direct Command with File Input (Simplest)

Since Ralph Loop can accept file input, you can create a simple wrapper:

1. Create `RALPH-PROMPT.md` with just the prompt content (no frontmatter):
```markdown
# AI AUTONOMOUS DEVELOPMENT SCRIPT (STRICT ENFORCEMENT)

**TO ANY AI AGENT READING THIS:**
You are now the Lead Developer/Orchestrator for **Project-Firefly**...
[rest of your prompt]
```

2. Create a simple alias or batch file:
```bash
# Windows Batch
@echo off
claude /ralph-loop --max-iterations 20 --completion-promise "ROADMAP COMPLETE" @RALPH-PROMPT.md
```

```powershell
# PowerShell Alias
function Start-Ralph {
    claude "/ralph-loop --max-iterations 20 --completion-promise 'ROADMAP COMPLETE' $(Get-Content RALPH-PROMPT.md -Raw)"
}
Set-Alias ralph Start-Ralph
```

---

## Recommended Setup (Step-by-Step)

### Quick Start (5 minutes):

1. **Create the prompt file** (without frontmatter):
   - Copy content from `.claude\ralph-loop.local.md`
   - Remove the `---` frontmatter section
   - Save as `RALPH-PROMPT.md` in project root

2. **Create batch file** `ralph.bat`:
```batch
@echo off
setlocal enabledelayedexpansion

REM Read the prompt file
set "prompt_file=RALPH-PROMPT.md"
set "prompt="

for /f "usebackq delims=" %%a in ("%prompt_file%") do (
    set "line=%%a"
    set "prompt=!prompt! !line!"
)

REM Execute Ralph Loop
claude /ralph-loop --max-iterations 20 --completion-promise "ROADMAP COMPLETE" %prompt%
```

3. **Add to PATH** or use directly:
```bash
.\ralph.bat
```

---

## Testing Your Setup

After implementing any option above, test it:

1. Navigate to your project directory
2. Run your command: `ralph` or `.\ralph.bat` or `/ralph-start`
3. Verify that Ralph Loop starts with:
   - Max iterations: 20
   - Completion promise: "ROADMAP COMPLETE"
   - Your full AI AUTONOMOUS DEVELOPMENT SCRIPT prompt

---

## Troubleshooting

### Issue: "No prompt provided"
- **Cause**: Prompt not being passed correctly
- **Fix**: Ensure your script properly reads and passes the file content

### Issue: Prompt truncated
- **Cause**: Special characters or newlines breaking the command
- **Fix**: Escape special characters or use file input method (`@RALPH-PROMPT.md`)

### Issue: Configuration not applied
- **Cause**: Flags not being passed to Ralph Loop command
- **Fix**: Verify `--max-iterations` and `--completion-promise` flags are included

---

## Best Practice Recommendation

**Use Option 4 (Direct Command with File Input)** because:
- ✅ Simplest to implement
- ✅ Easy to modify prompt (just edit one file)
- ✅ No complex scripting required
- ✅ Works on any platform
- ✅ Transparent and debuggable

Create these two files:
1. `RALPH-PROMPT.md` - Your prompt content
2. `ralph.bat` - Simple launcher

Done!
