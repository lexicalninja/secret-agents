# Secret Agents

A collection of Cursor subagents to help build things together.

## Agent Workflows

See [WORKFLOW.md](WORKFLOW.md) for detailed explanations of how agents work together, including:
- Scrum Master → UI/UX Designer workflow
- Task discovery and processing
- Design task integration

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

### 🔍 Code Reviewer Feedback
**File:** `.cursor/agents/code-reviewer-feedback.md`

Reviews code and provides structured feedback documents for coding agents. Creates actionable feedback with file paths, line numbers, code examples, and prioritization. Automatically triggers on commits to main, branch merges, or pull requests.

**Usage:**
```
/code-reviewer-feedback review the latest changes
```

### 📚 Documentation
**File:** `.cursor/agents/documentation.md`

Documentation specialist. Creates and updates docs, README files, API documentation, and code comments.

**Usage:**
```
/documentation update the README with the new API
```

### 📋 Specification Writer
**File:** `.cursor/agents/specification-writer.md`

Transforms ideas into detailed specifications and implementation directions. Takes high-level concepts and breaks them down into actionable specifications for another agent to implement.

**Usage:**
```
/specification-writer turn this idea into a detailed spec: "build a user dashboard"
```

### 📊 Scrum Master
**File:** `.cursor/agents/scrum-master.md`

Reviews specification documents and breaks them down into atomic, modular tasks. Creates task lists with dependencies, parallel execution opportunities, and build-safe implementation strategies.

**Usage:**
```
/scrum-master break down this specification into tasks: [specification document]
```

### 🎨 UI/UX Designer
**File:** `.cursor/agents/ui-ux-designer.md`

Accepts design-focused tasks and adds comprehensive design specifications. Creates markdown design specs, considers accessibility and responsive design, and updates task documents using a hybrid approach (sections for simple tasks, separate tasks for complex).

**Usage:**
```
/ui-ux-designer add design specs to this task: [task document]
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

### 📊 Requirement Analyzer
**Path:** `.cursor/skills/requirement-analyzer/SKILL.md`

Analyzes ideas and extracts functional and non-functional requirements. Identifies what needs to be built, constraints, and success criteria.

**Usage:** "Analyze requirements for this feature idea"

### 🗺️ Implementation Planner
**Path:** `.cursor/skills/implementation-planner/SKILL.md`

Creates detailed, step-by-step implementation plans from specifications. Organizes work into phases, identifies dependencies, and creates a clear roadmap.

**Usage:** "Create an implementation plan for these requirements"

### 🔧 Technical Spec Writer
**Path:** `.cursor/skills/technical-spec-writer/SKILL.md`

Creates detailed technical specifications including architecture, data models, APIs, and technology choices. Provides concrete technical guidance for implementation.

**Usage:** "Write technical specs for this system"

### 🐛 Bug Detector
**Path:** `.cursor/skills/bug-detector/SKILL.md`

Detects bugs, logic errors, and edge case handling issues in code. Returns structured bug reports with file paths, line numbers, and suggested fixes.

**Usage:** "Detect bugs in this code"

### 🔒 Security Scanner
**Path:** `.cursor/skills/security-scanner/SKILL.md`

Scans code for security vulnerabilities including SQL injection, XSS, hardcoded secrets, and missing input validation. Returns structured security issue reports.

**Usage:** "Scan this code for security vulnerabilities"

### 📋 Specification Checker
**Path:** `.cursor/skills/specification-checker/SKILL.md`

Compares code implementation against specifications and requirements. Verifies functional requirements, acceptance criteria, and technical specifications are met.

**Usage:** "Check if this code meets the specification requirements"

### 🎨 Code Style Analyzer
**Path:** `.cursor/skills/code-style-analyzer/SKILL.md`

Analyzes code for style and formatting issues including inconsistent formatting, naming conventions, code organization, and unused code.

**Usage:** "Analyze code style in these files"

### ⚡ Performance Analyzer
**Path:** `.cursor/skills/performance-analyzer/SKILL.md`

Analyzes code for performance issues including inefficient algorithms, unnecessary computations, memory leaks, and missing caching. Returns optimization suggestions.

**Usage:** "Analyze performance issues in this code"

### ♿ Accessibility Checker
**Path:** `.cursor/skills/accessibility-checker/SKILL.md`

Checks code for accessibility issues including missing alt text, poor color contrast, missing ARIA labels, and keyboard navigation issues. Returns WCAG compliance information.

**Usage:** "Check accessibility compliance for this code"

### 🏗️ Architecture Reviewer
**Path:** `.cursor/skills/architecture-reviewer/SKILL.md`

Reviews code architecture for design issues including poor separation of concerns, tight coupling, missing abstractions, and scalability concerns.

**Usage:** "Review the architecture of this code"

### ✅ Best Practices Checker
**Path:** `.cursor/skills/best-practices-checker/SKILL.md`

Checks code for best practice violations including DRY violations, SOLID principles, error handling patterns, and testing practices.

**Usage:** "Check best practices in this code"

### 📐 Layout Designer
**Path:** `.cursor/skills/layout-designer/SKILL.md`

Designs page layouts, grid systems, and structural arrangements. Considers responsive design, visual hierarchy, and accessibility.

**Usage:** "Design layout for this page"

### 🧩 Component Designer
**Path:** `.cursor/skills/component-designer/SKILL.md`

Designs reusable UI components including buttons, inputs, cards, modals. Specifies states, variations, and usage guidelines.

**Usage:** "Design a button component"

### 🎨 Color System Designer
**Path:** `.cursor/skills/color-system-designer/SKILL.md`

Creates color palettes and color systems. Defines primary, secondary, neutral, and semantic colors with accessibility compliance.

**Usage:** "Create color system for this application"

### ✍️ Typography Designer
**Path:** `.cursor/skills/typography-designer/SKILL.md`

Designs typography systems including font choices, sizes, weights, line heights. Creates type scale and usage guidelines.

**Usage:** "Design typography system"

### 📏 Spacing System Designer
**Path:** `.cursor/skills/spacing-system-designer/SKILL.md`

Creates spacing and sizing systems including margins, padding, gaps. Defines spacing tokens and usage guidelines.

**Usage:** "Create spacing system"

### 🎭 Interaction Designer
**Path:** `.cursor/skills/interaction-designer/SKILL.md`

Designs interactions, animations, transitions, and micro-interactions. Specifies hover states, click feedback, and loading states.

**Usage:** "Design interactions for this component"

### 📱 Responsive Design Planner
**Path:** `.cursor/skills/responsive-design-planner/SKILL.md`

Plans responsive design breakpoints, mobile-first approaches, and adaptive layouts. Defines how designs adapt across screen sizes.

**Usage:** "Plan responsive design for this layout"

### ♿ Accessibility Design Checker
**Path:** `.cursor/skills/accessibility-design-checker/SKILL.md`

Ensures designs meet accessibility requirements including WCAG compliance, color contrast, keyboard navigation, and screen reader support.

**Usage:** "Check accessibility compliance for this design"

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
