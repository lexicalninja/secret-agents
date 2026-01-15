# Agent Workflow: Scrum Master → UI/UX Designer

This document explains how the scrum-master and ui-ux-designer agents work together.

## Overview

The workflow enables design tasks to flow from scrum-master task creation to ui-ux-designer, which adds design specifications that implementation agents can use.

## Workflow Steps

### 1. Scrum Master Creates Tasks

When the scrum-master breaks down a specification, it identifies tasks that need UI/UX design work.

**Task Marking Options:**

**Option A: Mark with "Needs Design" flag**
```markdown
### TASK-010: Style the submit button
- **Type**: Implementation
- **Needs Design**: Yes
- **Description**: Style the submit button with proper colors, spacing, and states
```

**Option B: Create separate Design task type**
```markdown
### TASK-010-DESIGN: Design submit button
- **Type**: Design
- **Dependencies**: None
- **Description**: Create design specifications for submit button

### TASK-010: Implement submit button styling
- **Type**: Implementation
- **Dependencies**: TASK-010-DESIGN
- **Description**: Implement button styling according to TASK-010-DESIGN
```

**Option C: Use design keywords in task**
Tasks with keywords like "style", "design", "UI", "layout", "component", "button", "form" are automatically detected as needing design.

### 2. UI/UX Designer Discovers Tasks

The UI/UX designer can pick up design tasks in three ways:

**A. Explicit Invocation**
```
/ui-ux-designer add design specs to TASK-010
```
or
```
Add design specifications to all tasks that need design in tasks-dog-webpage.md
```

**B. Automatic Detection**
The agent scans task documents for:
- Tasks marked `Type: Design`
- Tasks with `Needs Design: Yes`
- Tasks with design-related keywords in title/description

**C. Task List Review**
When given a task list, the agent identifies which tasks need design work and processes them.

### 3. UI/UX Designer Processes Tasks

For each design task, the designer:

1. **Analyzes the task** to understand design requirements
2. **Checks for design system** (asks if none exists)
3. **Creates design specifications** using appropriate design skills
4. **Updates task document** using hybrid approach:
   - **Simple tasks**: Adds "Design Specifications" section directly to task
   - **Complex tasks**: Creates separate design task (TASK-010-DESIGN) and links to original

### 4. Implementation Agent Uses Design

When an implementation agent picks up a task:
- If task has design section: Uses those specs
- If task depends on design task: Reads the design task first
- Implements according to design specifications

## Example Workflow

### Step 1: Specification Created
```
specification-writer creates: "Build a login page"
```

### Step 2: Scrum Master Breaks Down
```markdown
### TASK-005: Create login form component
- **Type**: Implementation
- **Needs Design**: Yes
- **Description**: Create login form with email and password fields

### TASK-006: Style login page layout
- **Type**: Implementation
- **Needs Design**: Yes
- **Description**: Style the overall login page layout
```

### Step 3: UI/UX Designer Processes
```markdown
### TASK-005: Create login form component
- **Type**: Implementation
- **Needs Design**: Yes
[... existing task content ...]

## Design Specifications

### Component: Login Form
- Layout: Centered, max-width 400px
- Spacing: 24px padding
- Fields: Email and password inputs
- Button: Primary submit button
[... detailed design specs ...]
```

### Step 4: Implementation Agent Implements
- Reads TASK-005 with design specs
- Implements login form according to design specifications
- Creates accessible, responsive login form

## Task Dependencies

**Design Before Implementation:**
- Design tasks should be completed before implementation tasks
- Scrum master should set dependencies: `Implementation depends on Design`

**Example:**
```markdown
### TASK-010-DESIGN: Design user dashboard
- **Type**: Design
- **Dependencies**: None

### TASK-010: Implement user dashboard
- **Type**: Implementation
- **Dependencies**: TASK-010-DESIGN
```

## Best Practices

1. **Scrum Master**: Always identify and mark design tasks when breaking down specifications
2. **UI/UX Designer**: Process design tasks before implementation begins
3. **Dependencies**: Set clear dependencies so design happens before implementation
4. **Task Linking**: Link design tasks to implementation tasks for traceability
5. **Design System**: Create design system early if multiple design tasks exist

## Integration Points

- **Scrum Master → UI/UX Designer**: Task documents with marked design tasks
- **UI/UX Designer → Task Document**: Updated tasks with design specifications
- **Task Document → Implementation Agent**: Tasks with design specs ready for implementation
