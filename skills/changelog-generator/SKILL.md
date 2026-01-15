---
name: changelog-generator
description: Generate changelog entries from git commits, pull requests, or code changes. Use when creating release notes, updating CHANGELOG.md, or documenting what changed in a version.
---

# Changelog Generator Skill

## Instructions

1. Analyze git commits, pull requests, or code changes to identify what was modified
2. Categorize changes into: Added, Changed, Deprecated, Removed, Fixed, Security
3. Format entries following Keep a Changelog format (https://keepachangelog.com/)
4. Group related changes together
5. Use clear, concise language that users can understand
6. Include relevant issue/PR numbers when available
7. Maintain chronological order (newest first)
8. Add appropriate version headers and dates

## Examples

**Input:** "Generate a changelog for the last 10 commits"
**Output:**
```markdown
## [1.2.0] - 2025-01-15

### Added
- New authentication flow with OAuth2 support
- User profile editing capabilities

### Changed
- Updated API rate limiting to be more permissive
- Improved error messages for validation failures

### Fixed
- Resolved memory leak in background job processor
- Fixed issue where deleted users could still receive emails
```

**Input:** "Create changelog entry for the payment module changes"
**Output:**
```markdown
## [Unreleased]

### Added
- Support for Stripe payment processing
- Payment retry logic for failed transactions

### Changed
- Payment webhook handling now uses async processing
```

## Format Guidelines

- Use semantic versioning (MAJOR.MINOR.PATCH)
- Start with [Unreleased] for ongoing changes
- Use present tense: "Add feature" not "Added feature"
- Reference issues/PRs: "Fix login bug (#123)"
- Group breaking changes under "### Changed" with migration notes
