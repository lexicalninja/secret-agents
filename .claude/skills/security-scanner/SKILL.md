---
name: security-scanner
description: Scans code for security vulnerabilities including SQL injection, XSS, hardcoded secrets, insecure authentication, and missing input validation. Returns structured security issue reports with file paths, line numbers, and remediation steps.
---

# Security Scanner Skill

## Instructions

1. Scan code for security vulnerabilities
2. Check for SQL injection risks
3. Check for XSS vulnerabilities
4. Look for hardcoded secrets/credentials
5. Verify authentication/authorization security
6. Check input validation and sanitization
7. Review dependency security
8. Return structured security reports with:
   - File path and line numbers
   - Vulnerability type and severity
   - Current vulnerable code
   - Suggested secure fix
   - Reason and impact
   - Priority (Must-Fix for critical, Should-Fix for high)

## Examples

**Input:** Hardcoded API key in source code
**Output:**
```markdown
### SEC-001
- **File**: `config.js`
- **Lines**: 12
- **Priority**: Must-Fix
- **Issue**: Hardcoded API key exposed in source code
- **Current Code**:
  ```javascript
  const API_KEY = "sk_live_1234567890abcdef";
  ```
- **Suggested Fix**:
  ```javascript
  const API_KEY = process.env.API_KEY;
  if (!API_KEY) {
      throw new Error("API_KEY environment variable not set");
  }
  ```
- **Reason**: Hardcoded secrets can be exposed in version control and compromise security
```

## Security Issues to Detect

- **SQL Injection**: Unparameterized database queries
- **XSS Vulnerabilities**: Unsanitized user input in HTML
- **Hardcoded Secrets**: API keys, passwords, tokens in code
- **Insecure Authentication**: Weak password requirements, missing 2FA
- **Missing Input Validation**: Unvalidated user input
- **Insecure Dependencies**: Outdated packages with known vulnerabilities
- **CSRF Vulnerabilities**: Missing CSRF tokens
- **Insecure File Uploads**: Unvalidated file types/sizes
- **Path Traversal**: Unvalidated file paths
- **Insecure Random**: Weak random number generation
- **Information Disclosure**: Error messages exposing sensitive data
- **Missing HTTPS**: Insecure communication protocols

## Priority Guidelines

- **Must-Fix**: Critical vulnerabilities (SQL injection, XSS, exposed secrets)
- **Should-Fix**: High-risk vulnerabilities (missing validation, insecure auth)
- **Nice-to-Have**: Medium-risk issues (dependency updates, minor improvements)
