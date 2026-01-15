---
name: accessibility-checker
description: Checks code for accessibility issues including missing alt text, poor color contrast, missing ARIA labels, keyboard navigation issues, screen reader compatibility, and focus management. Returns structured accessibility issue reports with WCAG compliance information.
---

# Accessibility Checker Skill

## Instructions

1. Analyze code for accessibility issues
2. Check for missing or poor alt text on images
3. Verify color contrast meets WCAG standards
4. Check for missing ARIA labels and roles
5. Verify keyboard navigation works
6. Check screen reader compatibility
7. Review focus management
8. Return structured accessibility reports with:
   - File path and line numbers
   - Accessibility issue type
   - WCAG guideline reference
   - Current code
   - Suggested fix
   - Reason and impact
   - Priority (Must-Fix for critical, Should-Fix for important)

## Examples

**Input:** Image without alt text
**Output:**
```markdown
### A11Y-001
- **File**: `index.html`
- **Lines**: 25
- **Priority**: Must-Fix
- **Issue**: Image missing descriptive alt text
- **WCAG Reference**: WCAG 2.1 Level A - 1.1.1 Non-text Content
- **Current Code**:
  ```html
  <img src="dog.jpg" alt="">
  ```
- **Suggested Fix**:
  ```html
  <img src="dog.jpg" alt="Golden retriever puppy playing in a sunny park">
  ```
- **Reason**: Screen readers need descriptive alt text to convey image content to users
- **Impact**: Users with visual impairments cannot understand the image content
```

## Accessibility Issues to Detect

- **Missing Alt Text**: Images without descriptive alt attributes
- **Poor Color Contrast**: Text/background contrast below WCAG standards
- **Missing ARIA Labels**: Interactive elements without proper ARIA labels
- **Keyboard Navigation**: Elements not keyboard accessible
- **Focus Management**: Missing or invisible focus indicators
- **Screen Reader Issues**: Semantic HTML not used, missing landmarks
- **Form Labels**: Missing or improperly associated form labels
- **Heading Hierarchy**: Incorrect or missing heading structure
- **Language Declaration**: Missing lang attribute on html element
- **Text Resizing**: Content that breaks when text is resized
- **Flashing Content**: Content that flashes more than 3 times per second

## Priority Guidelines

- **Must-Fix**: Critical accessibility issues (missing alt text, keyboard navigation, WCAG A violations)
- **Should-Fix**: Important accessibility improvements (contrast, ARIA labels, WCAG AA)
- **Nice-to-Have**: Enhancement accessibility features (WCAG AAA, advanced ARIA)
