---
name: architecture-reviewer
description: Reviews code architecture for design issues including poor separation of concerns, tight coupling, missing abstractions, design pattern violations, scalability concerns, and maintainability issues. Returns structured architecture review reports with improvement suggestions.
---

# Architecture Reviewer Skill

## Instructions

1. Review code architecture and design
2. Check separation of concerns
3. Identify tight coupling between components
4. Look for missing abstractions
5. Check for design pattern violations
6. Assess scalability concerns
7. Review maintainability
8. Return structured architecture reports with:
   - File path and line numbers (if applicable)
   - Architecture issue type
   - Current design
   - Suggested improvement
   - Reason and impact
   - Priority (usually Should-Fix or Nice-to-Have)

## Examples

**Input:** Business logic mixed with presentation
**Output:**
```markdown
### ARCH-001
- **File**: `components/TaskList.jsx`
- **Lines**: 45-60
- **Priority**: Should-Fix
- **Issue**: Business logic mixed with presentation layer
- **Current Code**:
  ```javascript
  function TaskList({ tasks }) {
      const filteredTasks = tasks.filter(task => {
          // Complex business logic here
          return task.status === 'active' && 
                 task.priority > 5 && 
                 new Date(task.dueDate) > new Date();
      });
      return <div>{/* render */}</div>;
  }
  ```
- **Suggested Fix**:
  ```javascript
  // Move to utils/taskFilters.js
  function filterActiveHighPriorityTasks(tasks) {
      return tasks.filter(task => 
          task.status === 'active' && 
          task.priority > 5 && 
          new Date(task.dueDate) > new Date()
      );
  }
  
  // In component
  function TaskList({ tasks }) {
      const filteredTasks = filterActiveHighPriorityTasks(tasks);
      return <div>{/* render */}</div>;
  }
  ```
- **Reason**: Separating business logic from presentation improves testability and maintainability
- **Impact**: Makes code easier to test, reuse, and modify
```

## Architecture Issues to Detect

- **Separation of Concerns**: Business logic mixed with presentation/data layers
- **Tight Coupling**: Components/modules too dependent on each other
- **Missing Abstractions**: Code duplication, missing interfaces/abstract classes
- **Design Pattern Violations**: Not following appropriate design patterns
- **Scalability Concerns**: Architecture that won't scale
- **Maintainability Issues**: Code that's hard to understand or modify
- **Single Responsibility**: Classes/functions doing too much
- **Dependency Management**: Circular dependencies, too many dependencies
- **Code Organization**: Poor file/folder structure
- **Interface Design**: Poor API/interface design

## Priority Guidelines

- **Must-Fix**: Architecture issues that cause bugs or block scalability
- **Should-Fix**: Architecture improvements that enhance maintainability
- **Nice-to-Have**: Refactoring opportunities and design improvements
