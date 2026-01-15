# My Little Scrum Team

A Claude Code plugin providing a collection of AI agents and skills that work together as a coordinated scrum team.

## Installation

### From Plugin Marketplace

```
/plugin install my-little-scrum-team
```

### From GitHub

```
/plugin install https://github.com/lexicalninja/secret-agents
```

### Local Development

```bash
claude --plugin-dir ./path-to-this-repo
```

## Overview

This plugin provides a complete development team of AI agents to help build things together.

## Agent Workflows

Agents work together in a coordinated workflow:
- **Manager** → Makes strategic decisions, hires agents, manages resources, and ensures projects have the right agents before work begins
- **Orchestrator** → Orchestrates the full development workflow from idea to implementation
- **Specification Writer** → Creates detailed specifications
- **Scrum Master** → Breaks specifications into atomic tasks (including Design, Implementation, Infrastructure, Deployment)
- **UI/UX Designer** → Picks up Design tasks and adds design specifications
- **Implementation Engineer** → Implements tasks, submits for review, iterates until approved, then commits
- **Infrastructure Engineer** → Handles Infrastructure and Deployment tasks
- **Code Reviewer Feedback** → Reviews code and provides structured feedback

Each agent's documentation explains how it discovers and processes tasks.
- Task discovery and processing
- Design task integration

## What are Claude Code Agents?

Claude Code agents are specialized AI assistants that Claude can delegate tasks to. Each agent operates in its own context window, handles specific types of work, and returns its result to the parent agent. Use agents to break down complex tasks, do work in parallel, and preserve context in the main conversation.

Learn more: [Claude Code Plugins Documentation](https://code.claude.com/docs/en/plugins)

## Available Agents

All agents are located in `agents/` and can be invoked explicitly or used automatically by Claude.

### 👔 Manager
**File:** `agents/manager.md`

Makes strategic decisions on work, hires agents (creates new or selects existing), and ensures projects have the right agents before work begins. Works alongside orchestrator to manage resources, prioritize tasks, handle escalations, resolve conflicts, and manage quality gates.

**Usage:**
```
/my-little-scrum-team:manager review tasks and hire necessary agents
/my-little-scrum-team:manager prioritize these tasks
/my-little-scrum-team:manager resolve this conflict between agents
```

### 🎯 Orchestrator
**File:** `agents/orchestrator.md`

Orchestrates the full development workflow from idea to implementation. Automatically coordinates all agents in the correct sequence: specification → tasks → design → implementation → review → commit.

**Usage:**
```
/my-little-scrum-team:orchestrator build a user login page with email and password
/my-little-scrum-team:orchestrator implement the features in specification-user-dashboard.md
```

This is the recommended way to build features end-to-end automatically.

### 📋 Specification Writer
**File:** `agents/specification-writer.md`

Transforms ideas into detailed specifications and implementation directions. Takes high-level concepts and breaks them down into actionable specifications for another agent to implement.

**Usage:**
```
/my-little-scrum-team:specification-writer turn this idea into a detailed spec: "build a user dashboard"
```

### 📊 Scrum Master
**File:** `agents/scrum-master.md`

Reviews specification documents and breaks them down into atomic, modular tasks. Creates task lists with dependencies, parallel execution opportunities, and build-safe implementation strategies.

**Usage:**
```
/my-little-scrum-team:scrum-master break down this specification into tasks: [specification document]
```

### 🎨 UI/UX Designer
**File:** `agents/ui-ux-designer.md`

Accepts design-focused tasks and adds comprehensive design specifications. Creates markdown design specs, considers accessibility and responsive design, and updates task documents using a hybrid approach (sections for simple tasks, separate tasks for complex).

**Usage:**
```
/my-little-scrum-team:ui-ux-designer add design specs to this task: [task document]
```

### 👷 Implementation Engineer
**File:** `agents/implementation-engineer.md`

Implements tasks from scrum-master, submits to code-reviewer-feedback, responds to feedback iteratively until approved, then commits changes. Handles both frontend and backend implementation work.

**Usage:**
```
/my-little-scrum-team:implementation-engineer implement TASK-010 from tasks-dog-webpage.md
```

### 🏗️ Infrastructure Engineer
**File:** `agents/infrastructure-engineer.md`

Sets up infrastructure, CI/CD pipelines, deployment configurations, and development environments. Handles infrastructure-as-code, automation, and deployment readiness.

**Usage:**
```
/my-little-scrum-team:infrastructure-engineer set up CI/CD pipeline for this project
```

### 🔍 Code Reviewer Feedback
**File:** `agents/code-reviewer-feedback.md`

Reviews code and provides structured feedback documents for coding agents. Creates actionable feedback with file paths, line numbers, code examples, and prioritization. Automatically triggers on commits to main, branch merges, or pull requests.

**Usage:**
```
/my-little-scrum-team:code-reviewer-feedback review the latest changes
```


## How to Use

### Automatic Orchestration (Recommended)

Use the orchestrator to automatically run the full workflow from idea to implementation:

```
/my-little-scrum-team:orchestrator build a user login page with email and password
```

The orchestrator will automatically:
1. Create specification (specification-writer)
2. Break into tasks (scrum-master)
3. Manager reviews and hires necessary agents (manager)
4. Add design specs (ui-ux-designer)
5. Implement code (implementation-engineer)
6. Review and iterate (code-reviewer-feedback)
7. Commit changes

**Note:** The manager works alongside the orchestrator to make strategic decisions, hire agents when needed, and manage resources throughout the workflow.

### Explicit Invocation

Use the `/my-little-scrum-team:agent-name` syntax to invoke a specific agent:

```
/my-little-scrum-team:implementation-engineer implement the login form
/my-little-scrum-team:code-reviewer-feedback review the authentication code
/my-little-scrum-team:infrastructure-engineer set up the deployment pipeline
```

### Natural Language

You can also invoke agents naturally:

```
Use the orchestrator agent to build a user dashboard
Have the code reviewer agent review the latest changes
Run the infrastructure engineer agent on the deployment setup
```

### Automatic Delegation

Claude Code will automatically use these agents when appropriate based on their descriptions. The agent reads the `description` field in each agent's YAML frontmatter to decide when to delegate.

## Creating Custom Agents

To create a new agent, add a markdown file to `agents/` with YAML frontmatter:

```markdown
---
name: my-agent
description: When to use this agent. Be specific!
model: inherit
---

Your agent instructions here...
```

### Configuration Fields

- `name`: Unique identifier (lowercase with hyphens)
- `description`: When to use this agent (Claude reads this for delegation)
- `model`: `fast`, `inherit`, or specific model ID (defaults to `inherit`)
- `readonly`: If `true`, restricts write permissions
- `is_background`: If `true`, runs in background without waiting

## Best Practices

- **Write focused agents** — Each agent should have a single, clear responsibility
- **Invest in descriptions** — The `description` field determines when Claude delegates
- **Keep prompts concise** — Be specific and direct
- **Add to version control** — Check `agents/` into your repository

## Available Skills (Claude-Style)

Skills are reusable, single-purpose capabilities that follow Claude's Skills format. Each skill is a folder with a `SKILL.md` file containing structured instructions and examples.

All skills are located in `skills/` and follow the Claude Skills standard format.

### 📝 Changelog Generator
**Path:** `skills/changelog-generator/SKILL.md`

Generates changelog entries from git commits, pull requests, or code changes. Follows Keep a Changelog format.

**Usage:** "Generate a changelog for the last 10 commits"

### 📦 Import Formatter
**Path:** `skills/import-formatter/SKILL.md`

Formats and organizes import statements in code files. Groups imports by type (standard library, third-party, local) and sorts them alphabetically.

**Usage:** "Format the imports in this file"

### 📚 Code Documentation
**Path:** `skills/code-documentation/SKILL.md`

Generates comprehensive code documentation including docstrings, comments, and API documentation. Follows language-specific conventions (Google style, JSDoc, etc.).

**Usage:** "Add documentation to this function"

### 🔧 Git Commit Helper
**Path:** `skills/git-commit-helper/SKILL.md`

Generates well-structured git commit messages following conventional commits format. Ensures commits are clear, descriptive, and follow project conventions.

**Usage:** "Create a commit message for these changes"

### 🧪 Test Generator
**Path:** `skills/test-generator/SKILL.md`

Generates comprehensive test cases for code. Creates tests covering happy paths, edge cases, error conditions, following testing best practices.

**Usage:** "Generate tests for this function"

### 📊 Requirement Analyzer
**Path:** `skills/requirement-analyzer/SKILL.md`

Analyzes ideas and extracts functional and non-functional requirements. Identifies what needs to be built, constraints, and success criteria.

**Usage:** "Analyze requirements for this feature idea"

### 🗺️ Implementation Planner
**Path:** `skills/implementation-planner/SKILL.md`

Creates detailed, step-by-step implementation plans from specifications. Organizes work into phases, identifies dependencies, and creates a clear roadmap.

**Usage:** "Create an implementation plan for these requirements"

### 🔧 Technical Spec Writer
**Path:** `skills/technical-spec-writer/SKILL.md`

Creates detailed technical specifications including architecture, data models, APIs, and technology choices. Provides concrete technical guidance for implementation.

**Usage:** "Write technical specs for this system"

### 🐛 Bug Detector
**Path:** `skills/bug-detector/SKILL.md`

Detects bugs, logic errors, and edge case handling issues in code. Returns structured bug reports with file paths, line numbers, and suggested fixes.

**Usage:** "Detect bugs in this code"

### 🔒 Security Scanner
**Path:** `skills/security-scanner/SKILL.md`

Scans code for security vulnerabilities including SQL injection, XSS, hardcoded secrets, and missing input validation. Returns structured security issue reports.

**Usage:** "Scan this code for security vulnerabilities"

### 📋 Specification Checker
**Path:** `skills/specification-checker/SKILL.md`

Compares code implementation against specifications and requirements. Verifies functional requirements, acceptance criteria, and technical specifications are met.

**Usage:** "Check if this code meets the specification requirements"

### 🎨 Code Style Analyzer
**Path:** `skills/code-style-analyzer/SKILL.md`

Analyzes code for style and formatting issues including inconsistent formatting, naming conventions, code organization, and unused code.

**Usage:** "Analyze code style in these files"

### ⚡ Performance Analyzer
**Path:** `skills/performance-analyzer/SKILL.md`

Analyzes code for performance issues including inefficient algorithms, unnecessary computations, memory leaks, and missing caching. Returns optimization suggestions.

**Usage:** "Analyze performance issues in this code"

### ♿ Accessibility Checker
**Path:** `skills/accessibility-checker/SKILL.md`

Checks code for accessibility issues including missing alt text, poor color contrast, missing ARIA labels, and keyboard navigation issues. Returns WCAG compliance information.

**Usage:** "Check accessibility compliance for this code"

### 🏗️ Architecture Reviewer
**Path:** `skills/architecture-reviewer/SKILL.md`

Reviews code architecture for design issues including poor separation of concerns, tight coupling, missing abstractions, and scalability concerns.

**Usage:** "Review the architecture of this code"

### ✅ Best Practices Checker
**Path:** `skills/best-practices-checker/SKILL.md`

Checks code for best practice violations including DRY violations, SOLID principles, error handling patterns, and testing practices.

**Usage:** "Check best practices in this code"

### 📐 Layout Designer
**Path:** `skills/layout-designer/SKILL.md`

Designs page layouts, grid systems, and structural arrangements. Considers responsive design, visual hierarchy, and accessibility.

**Usage:** "Design layout for this page"

### 🧩 Component Designer
**Path:** `skills/component-designer/SKILL.md`

Designs reusable UI components including buttons, inputs, cards, modals. Specifies states, variations, and usage guidelines.

**Usage:** "Design a button component"

### 🎨 Color System Designer
**Path:** `skills/color-system-designer/SKILL.md`

Creates color palettes and color systems. Defines primary, secondary, neutral, and semantic colors with accessibility compliance.

**Usage:** "Create color system for this application"

### ✍️ Typography Designer
**Path:** `skills/typography-designer/SKILL.md`

Designs typography systems including font choices, sizes, weights, line heights. Creates type scale and usage guidelines.

**Usage:** "Design typography system"

### 📏 Spacing System Designer
**Path:** `skills/spacing-system-designer/SKILL.md`

Creates spacing and sizing systems including margins, padding, gaps. Defines spacing tokens and usage guidelines.

**Usage:** "Create spacing system"

### 🎭 Interaction Designer
**Path:** `skills/interaction-designer/SKILL.md`

Designs interactions, animations, transitions, and micro-interactions. Specifies hover states, click feedback, and loading states.

**Usage:** "Design interactions for this component"

### 📱 Responsive Design Planner
**Path:** `skills/responsive-design-planner/SKILL.md`

Plans responsive design breakpoints, mobile-first approaches, and adaptive layouts. Defines how designs adapt across screen sizes.

**Usage:** "Plan responsive design for this layout"

### ♿ Accessibility Design Checker
**Path:** `skills/accessibility-design-checker/SKILL.md`

Ensures designs meet accessibility requirements including WCAG compliance, color contrast, keyboard navigation, and screen reader support.

**Usage:** "Check accessibility compliance for this design"

### 🔌 API Implementer
**Path:** `skills/api-implementer/SKILL.md`

Implements API endpoints, routes, controllers, and request/response handling. Handles routing, validation, error handling, and response formatting.

**Usage:** "Implement POST /api/tasks endpoint"

### 💾 Database Implementer
**Path:** `skills/database-implementer/SKILL.md`

Creates database schemas, migrations, queries, and data access layers. Handles schema design, migrations, CRUD operations, and optimization.

**Usage:** "Create User and Task database tables"

### 🧩 Component Implementer
**Path:** `skills/component-implementer/SKILL.md`

Implements UI components from design specifications. Follows design specs, implements responsive design, and ensures accessibility.

**Usage:** "Implement submit button component with design specs"

### 🧪 Test Writer
**Path:** `skills/test-writer/SKILL.md`

Writes comprehensive test cases including unit tests, integration tests, and E2E tests. Covers happy paths, edge cases, and error conditions.

**Usage:** "Write tests for calculateTotal function"

### 🛠️ Utility Implementer
**Path:** `skills/utility-implementer/SKILL.md`

Implements utility functions, helpers, and shared code. Creates reusable functions, validation utilities, and helper modules.

**Usage:** "Implement password hashing utility"

### ⚙️ Config Setup
**Path:** `skills/config-setup/SKILL.md`

Sets up configuration files, environment variables, and project configuration. Creates config files, .env examples, and documentation.

**Usage:** "Set up environment configuration"

### 👔 Manager Skills

The following skills are used by the Manager agent for strategic project management:

#### 🔍 Agent Capability Assessor
**Path:** `skills/agent-capability-assessor/SKILL.md`

Assesses agent capabilities by analyzing agent files and determining what tasks they can handle. Evaluates if an existing agent can handle a task or if a new agent is needed.

**Usage:** "Assess if implementation-engineer can handle this task"

#### 🎯 Task-to-Agent Matcher
**Path:** `skills/task-to-agent-matcher/SKILL.md`

Matches tasks to appropriate agents by analyzing task requirements and finding agents with matching capabilities. Considers task type, requirements, and agent capabilities.

**Usage:** "Match this task to the best agent"

#### 🏭 Agent Creator
**Path:** `skills/agent-creator/SKILL.md`

Creates new agent files with complete specifications, following the same format as existing agents. Generates agent markdown files with name, description, core principles, workflow, and integration details.

**Usage:** "Create a new ML engineer agent for machine learning tasks"

#### 📊 Resource Planner
**Path:** `skills/resource-planner/SKILL.md`

Plans resource allocation and agent assignments to tasks. Considers task dependencies, agent capabilities, and workload distribution.

**Usage:** "Plan resource allocation for these tasks"

#### 📈 Task Prioritizer
**Path:** `skills/task-prioritizer/SKILL.md`

Prioritizes tasks based on dependencies, business value, resource availability, and project goals. Determines task execution order.

**Usage:** "Prioritize these tasks"

#### 🚨 Escalation Handler
**Path:** `skills/escalation-handler/SKILL.md`

Handles escalations and determines appropriate escalation paths. Analyzes issues, determines severity, and routes to appropriate resolution path.

**Usage:** "Handle this escalation"

#### ⚖️ Conflict Resolver
**Path:** `skills/conflict-resolver/SKILL.md`

Resolves conflicts between agents or approaches when disagreements arise. Analyzes conflicts, evaluates options, and makes decisions to resolve conflicts.

**Usage:** "Resolve this conflict between agents"

#### ✅ Quality Gate Manager
**Path:** `skills/quality-gate-manager/SKILL.md`

Manages quality gates and checkpoints to ensure work meets standards before proceeding to next phases. Defines quality criteria, checks work against criteria, and makes go/no-go decisions.

**Usage:** "Check if this work meets quality gates"

#### 🔧 Resource Optimizer
**Path:** `skills/resource-optimizer/SKILL.md`

Optimizes resource usage and makes decisions about when to optimize existing resources vs. add new resources. Analyzes current resource usage and recommends optimization strategies.

**Usage:** "Optimize resource allocation for this project"

## Skills vs Agents

| Feature | Skills | Agents |
|---------|--------|--------|
| **Purpose** | Single-purpose, quick actions | Complex, multi-step tasks |
| **Context** | No separate context window needed | Own context window |
| **Structure** | Folder with `SKILL.md` | Markdown file with YAML frontmatter |
| **Best For** | Formatting, generating docs, simple tasks | Debugging, reviewing, complex workflows |
| **Invocation** | Model-invoked automatically | Explicit or automatic delegation |

## Creating Custom Skills (Claude-Style)

To create a new skill, create a folder in `skills/` with a `SKILL.md` file:

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

- Claude Code version 1.0.33 or later

To check your version:
```bash
claude --version
```

To install or update Claude Code, visit the [Claude Code documentation](https://code.claude.com/docs/en/).
