---
name: ralph-shortcut
enabled: true
event: prompt
conditions:
  - field: user_prompt
    operator: regex_match
    pattern: ^(ralph|/ralph)$
---

# 🚀 Ralph Loop Auto-Start Triggered

The user typed "ralph" or "/ralph" - this is a shortcut to start Ralph Loop with predefined configuration.

**Your instructions (TWO-STAGE PROCESS):**

## STAGE 1: Auto-Commit & Push (Conditional)

1. **Read the configuration file**: `.claude\ralph-loop.local.md`
   - Parse the YAML frontmatter to extract configuration values
   - Key fields: `auto_commit`, `auto_push`, `max_iterations`, `completion_promise`

2. **Check auto_commit flag**:
   - If `auto_commit: true`, proceed with commit process
   - If `auto_commit: false`, skip to Stage 2

3. **Execute commit sequence** (only if auto_commit is true):
   ```bash
   git add .
   git commit -m "AUTO-COMMIT: Ralph Loop iteration checkpoint - $(date +%Y-%m-%d_%H:%M:%S)"
   ```

4. **Check auto_push flag** (only if auto_commit is true):
   - If `auto_push: true`, execute:
     ```bash
     git push
     ```
   - If `auto_push: false`, skip push

5. **Handle commit/push failures**:
   - If commit fails (nothing to commit), that's OK - proceed to Stage 2
   - If push fails, STOP and inform the user of the error
   - Only proceed to Stage 2 if commit/push succeeded OR nothing to commit

## STAGE 2: Trigger Ralph Loop (Always Executed)

6. **Extract prompt content**:
   - Read `.claude\ralph-loop.local.md` again
   - Extract the full content AFTER the frontmatter (after the second `---`)
   - This is the AI autonomous development script

7. **Start Ralph Loop** by invoking the skill:
   ```
   /ralph-loop --max-iterations {max_iterations} --completion-promise "{completion_promise}" {prompt_content}
   ```

8. **Important notes**:
   - Strip the YAML frontmatter completely (everything between the first `---` and second `---`)
   - Pass only the markdown content as the prompt
   - Use the exact values from the configuration file
   - Do not ask for confirmation - execute immediately

## Example Execution Flow

**With auto_commit enabled:**
```
1. git add .
2. git commit -m "AUTO-COMMIT: Ralph Loop iteration checkpoint - 2026-01-12_19:30:45"
3. git push (if auto_push: true)
4. /ralph-loop --max-iterations 20 --completion-promise "ROADMAP COMPLETE" [full prompt]
```

**With auto_commit disabled:**
```
1. Skip commit/push
2. /ralph-loop --max-iterations 20 --completion-promise "ROADMAP COMPLETE" [full prompt]
```

## Configuration Reference

Enable/disable auto-commit by editing `.claude\ralph-loop.local.md` frontmatter:

```yaml
---
auto_commit: true   # Set to false to disable auto-commit
auto_push: true     # Set to false to commit but not push
max_iterations: 20
completion_promise: "ROADMAP COMPLETE"
---
```

This shortcut saves the user from typing the full command every time and ensures work is committed before each Ralph Loop iteration.
