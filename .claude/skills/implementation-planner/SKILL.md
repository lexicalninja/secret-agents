---
name: implementation-planner
description: Creates detailed, step-by-step implementation plans from specifications. Use when you have requirements and need to break them down into actionable implementation steps. Organizes work into phases, identifies dependencies, and creates a clear roadmap.
---

# Implementation Planner Skill

## Instructions

1. Review the provided requirements and specifications
2. Break down the work into logical phases or milestones
3. Identify dependencies between tasks
4. Create detailed step-by-step implementation instructions
5. Estimate complexity and suggest order of implementation
6. Identify potential blockers or risks
7. Define deliverables for each phase
8. Create a clear, sequential plan that another agent can follow

## Examples

**Input:** Requirements for a user authentication system
**Output:**
```markdown
## Implementation Plan

### Phase 1: Database Setup
1. Create user table schema
   - Fields: id, email, password_hash, created_at, updated_at
   - Add unique constraint on email
   - Add indexes on email and id
2. Create password reset tokens table
   - Fields: id, user_id, token, expires_at, used
   - Foreign key to user table
   - Index on token

### Phase 2: Core Authentication
1. Implement password hashing utility
   - Use bcrypt library
   - Minimum 10 rounds
   - Function: hashPassword(password) -> hash
   - Function: verifyPassword(password, hash) -> boolean
2. Create user registration endpoint
   - Validate email format
   - Check email uniqueness
   - Hash password
   - Create user record
   - Send confirmation email
3. Create login endpoint
   - Verify email exists
   - Verify password
   - Generate JWT token
   - Return token and user info

### Phase 3: Password Reset
1. Create password reset request endpoint
   - Generate secure token
   - Store token with expiration
   - Send reset email
2. Create password reset confirmation endpoint
   - Validate token
   - Check expiration
   - Update password
   - Invalidate token

### Phase 4: Testing
1. Unit tests for password hashing
2. Integration tests for registration flow
3. Integration tests for login flow
4. Integration tests for password reset flow
5. Test edge cases (expired tokens, invalid emails, etc.)

## Dependencies

- Phase 2 depends on Phase 1
- Phase 3 depends on Phase 2
- Phase 4 can run in parallel with development

## Risks & Blockers

- Email service integration may have delays
- JWT token configuration needs security review
```

**Input:** Requirements for a REST API
**Output:**
```markdown
## Implementation Plan

### Phase 1: Project Setup
1. Initialize project structure
2. Install dependencies (Express, database driver, etc.)
3. Set up development environment
4. Configure linting and formatting

### Phase 2: Database Layer
1. Design database schema
2. Create migration scripts
3. Set up database connection
4. Create data access layer (models/repositories)

### Phase 3: API Layer
1. Set up Express server
2. Create route handlers
3. Implement request validation
4. Implement error handling middleware
5. Add authentication middleware

### Phase 4: Business Logic
1. Implement core business logic
2. Add validation rules
3. Handle edge cases
4. Implement error handling

### Phase 5: Testing & Documentation
1. Write unit tests
2. Write integration tests
3. Generate API documentation
4. Add code comments
```

## Format Guidelines

- Organize into clear phases or milestones
- Number steps sequentially
- Identify dependencies between phases
- Include technical details (libraries, patterns, etc.)
- Note potential risks or blockers
- Define clear deliverables for each phase
