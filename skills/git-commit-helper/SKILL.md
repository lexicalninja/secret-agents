---
name: git-commit-helper
description: Generate well-structured git commit messages following conventional commits format. Use when committing changes, creating commit messages, or when commit history needs improvement. Ensures commits are clear, descriptive, and follow project conventions.
---

# Git Commit Helper Skill

## Instructions

1. Analyze the staged changes or diff to understand what was modified
2. Determine the type of change:
   - `feat`: New feature
   - `fix`: Bug fix
   - `docs`: Documentation changes
   - `style`: Code style changes (formatting, no logic change)
   - `refactor`: Code refactoring
   - `perf`: Performance improvements
   - `test`: Adding or updating tests
   - `chore`: Maintenance tasks, build config, etc.
   - `ci`: CI/CD changes
   - `build`: Build system changes
3. Write a clear, concise subject line (50 chars or less)
4. Add a blank line, then detailed body if needed (wrap at 72 chars)
5. Reference issues/PRs when applicable
6. Use imperative mood: "Add feature" not "Added feature" or "Adds feature"
7. Follow conventional commits format: `type(scope): subject`

## Examples

**Input:** "I added a new login button and fixed the validation bug"
**Output:**
```
feat(auth): add login button to header

- Add new login button component to navigation header
- Implement click handler to open login modal
- Add styling to match design system

fix(validation): resolve email validation error

- Fix regex pattern for email validation
- Add test cases for edge cases
- Update error message to be more user-friendly

Closes #123
```

**Input:** "Updated the README and fixed some typos"
**Output:**
```
docs: update README with installation instructions

- Add detailed installation steps for different platforms
- Include troubleshooting section
- Fix typos in existing documentation
```

**Input:** "Refactored the payment processing code"
**Output:**
```
refactor(payments): improve payment processing logic

- Extract payment validation into separate function
- Simplify retry logic for failed transactions
- Improve error handling and logging
- Add unit tests for payment flow

BREAKING CHANGE: PaymentProcessor constructor now requires config object
```

## Format Guidelines

**Conventional Commits Format:**
```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature for users
- `fix`: Bug fix for users
- `docs`: Documentation only
- `style`: Formatting, missing semicolons, etc.
- `refactor`: Code change that neither fixes bug nor adds feature
- `perf`: Performance improvement
- `test`: Adding missing tests
- `chore`: Changes to build process or auxiliary tools

**Best Practices:**
- Subject line: imperative, lowercase, no period
- Body: explain what and why, not how
- Footer: reference issues, breaking changes
- Use present tense: "Fix bug" not "Fixed bug"
