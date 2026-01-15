# Secret Agents

A collection of Cursor subagents to help build things together.

## What are Cursor Subagents?

Cursor subagents are specialized AI assistants that Cursor's agent can delegate tasks to. Each subagent operates in its own context window, handles specific types of work, and returns its result to the parent agent. Use subagents to break down complex tasks, do work in parallel, and preserve context in the main conversation.

Learn more: [Cursor Subagents Documentation](https://cursor.com/docs/context/subagents)

## Available Subagents

All subagents are located in `.cursor/agents/` and can be invoked explicitly or used automatically by Cursor's agent.

### 🔍 Verifier
**File:** `.cursor/agents/verifier.md`

Validates completed work. Use after tasks are marked done to confirm implementations are functional.

**Usage:**
```
/verifier confirm the auth flow is complete
```

### 🐛 Debugger
**File:** `.cursor/agents/debugger.md`

Debugging specialist for errors and test failures. Use when encountering issues.

**Usage:**
```
/debugger investigate this error
```

### 🧪 Test Runner
**File:** `.cursor/agents/test-runner.md`

Test automation expert. Runs proactively to test code changes and fix failures.

**Usage:**
```
/test-runner run tests for the new feature
```

### 🔒 Security Auditor
**File:** `.cursor/agents/security-auditor.md`

Security specialist. Use when implementing auth, payments, or handling sensitive data.

**Usage:**
```
/security-auditor review the payment module
```

### 📝 Code Reviewer
**File:** `.cursor/agents/code-reviewer.md`

Code quality specialist. Reviews code for best practices, maintainability, and team standards.

**Usage:**
```
/code-reviewer review this pull request
```

### 📚 Documentation
**File:** `.cursor/agents/documentation.md`

Documentation specialist. Creates and updates docs, README files, API documentation, and code comments.

**Usage:**
```
/documentation update the README with the new API
```

## How to Use

### Explicit Invocation

Use the `/name` syntax to invoke a specific subagent:

```
/verifier confirm the implementation works
/debugger fix this test failure
/security-auditor audit the authentication code
```

### Natural Language

You can also invoke subagents naturally:

```
Use the verifier subagent to confirm the auth flow is complete
Have the debugger subagent investigate this error
Run the security-auditor subagent on the payment module
```

### Automatic Delegation

Cursor's agent will automatically use these subagents when appropriate based on their descriptions. The agent reads the `description` field in each subagent's YAML frontmatter to decide when to delegate.

## Creating Custom Subagents

To create a new subagent, add a markdown file to `.cursor/agents/` with YAML frontmatter:

```markdown
---
name: my-subagent
description: When to use this subagent. Be specific!
model: inherit
---

Your subagent instructions here...
```

### Configuration Fields

- `name`: Unique identifier (lowercase with hyphens)
- `description`: When to use this subagent (Agent reads this for delegation)
- `model`: `fast`, `inherit`, or specific model ID (defaults to `inherit`)
- `readonly`: If `true`, restricts write permissions
- `is_background`: If `true`, runs in background without waiting

## Best Practices

- **Write focused subagents** — Each subagent should have a single, clear responsibility
- **Invest in descriptions** — The `description` field determines when Agent delegates
- **Keep prompts concise** — Be specific and direct
- **Add to version control** — Check `.cursor/agents/` into your repository

## Available Skills (Claude-Style)

Skills are reusable, single-purpose capabilities that follow Claude's Skills format. Each skill is a folder with a `SKILL.md` file containing structured instructions and examples.

All skills are located in `.cursor/skills/` and follow the Claude Skills standard format.

### 📝 Changelog Generator
**Path:** `.cursor/skills/changelog-generator/SKILL.md`

Generates changelog entries from git commits, pull requests, or code changes. Follows Keep a Changelog format.

**Usage:** "Generate a changelog for the last 10 commits"

### 📦 Import Formatter
**Path:** `.cursor/skills/import-formatter/SKILL.md`

Formats and organizes import statements in code files. Groups imports by type (standard library, third-party, local) and sorts them alphabetically.

**Usage:** "Format the imports in this file"

### 📚 Code Documentation
**Path:** `.cursor/skills/code-documentation/SKILL.md`

Generates comprehensive code documentation including docstrings, comments, and API documentation. Follows language-specific conventions (Google style, JSDoc, etc.).

**Usage:** "Add documentation to this function"

### 🔧 Git Commit Helper
**Path:** `.cursor/skills/git-commit-helper/SKILL.md`

Generates well-structured git commit messages following conventional commits format. Ensures commits are clear, descriptive, and follow project conventions.

**Usage:** "Create a commit message for these changes"

### 🧪 Test Generator
**Path:** `.cursor/skills/test-generator/SKILL.md`

Generates comprehensive test cases for code. Creates tests covering happy paths, edge cases, error conditions, following testing best practices.

**Usage:** "Generate tests for this function"

## Skills vs Subagents

| Feature | Skills | Subagents |
|---------|--------|-----------|
| **Purpose** | Single-purpose, quick actions | Complex, multi-step tasks |
| **Context** | No separate context window needed | Own context window |
| **Structure** | Folder with `SKILL.md` | Markdown file with YAML frontmatter |
| **Best For** | Formatting, generating docs, simple tasks | Debugging, reviewing, complex workflows |
| **Format** | Claude Skills standard | Cursor subagents format |

## Creating Custom Skills (Claude-Style)

To create a new skill, create a folder in `.cursor/skills/` with a `SKILL.md` file:

```markdown
---
name: my-skill
description: What this skill does and when to use it. Be specific!
---

# My Skill

## Instructions

1. Step-by-step instructions
2. What the skill should do
3. How to handle edge cases

## Examples

**Input:** "Example request"
**Output:** "Example result"
```

### Skill Structure

- **YAML frontmatter**: `name` and `description` (required)
- **Instructions section**: Step-by-step guidance
- **Examples section**: Concrete input/output examples
- **Optional files**: Templates, scripts, reference files in the same folder

## Requirements

- Cursor with Nightly release channel enabled
- Subagents feature must be enabled in Cursor Settings

To enable subagents:
1. Open Cursor Settings (`Cmd+Shift+J`)
2. Select **Beta**
3. Set update channel to **Nightly**
4. Restart Cursor

**Note:** Skills follow Claude's Skills format and may work when Cursor fully supports skills. They're structured to be compatible with both Cursor and Claude systems.
