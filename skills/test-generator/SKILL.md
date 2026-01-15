---
name: test-generator
description: Generate comprehensive test cases for code. Use when writing unit tests, integration tests, or test suites. Creates tests that cover happy paths, edge cases, error conditions, and follow testing best practices for the project's testing framework.
---

# Test Generator Skill

## Instructions

1. Analyze the code to understand what needs testing
2. Identify test cases:
   - Happy path scenarios
   - Edge cases (empty inputs, null values, boundary conditions)
   - Error conditions and exception handling
   - Integration points and dependencies
3. Generate tests following project conventions:
   - Use appropriate testing framework (Jest, pytest, Mocha, etc.)
   - Follow naming conventions (describe/it, test_*, etc.)
   - Use clear, descriptive test names
   - Include setup/teardown when needed
   - Mock external dependencies appropriately
4. Ensure tests are:
   - Independent and isolated
   - Fast and deterministic
   - Well-organized with good structure
   - Include assertions that verify expected behavior
5. Add comments explaining complex test scenarios

## Examples

**Input (Python function):**
```python
def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b
```

**Output:**
```python
import pytest
from calculator import divide

class TestDivide:
    """Test suite for divide function."""
    
    def test_divide_positive_numbers(self):
        """Test dividing two positive numbers."""
        assert divide(10, 2) == 5.0
        assert divide(9, 3) == 3.0
    
    def test_divide_negative_numbers(self):
        """Test dividing negative numbers."""
        assert divide(-10, 2) == -5.0
        assert divide(10, -2) == -5.0
    
    def test_divide_by_zero_raises_error(self):
        """Test that dividing by zero raises ValueError."""
        with pytest.raises(ValueError, match="Cannot divide by zero"):
            divide(10, 0)
    
    def test_divide_float_result(self):
        """Test that division returns float when result is decimal."""
        assert divide(7, 2) == 3.5
    
    def test_divide_zero_numerator(self):
        """Test dividing zero by non-zero number."""
        assert divide(0, 5) == 0.0
```

**Input (JavaScript function):**
```javascript
function validateEmail(email) {
    if (!email) return false;
    return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
}
```

**Output:**
```javascript
describe('validateEmail', () => {
    test('returns true for valid email addresses', () => {
        expect(validateEmail('user@example.com')).toBe(true);
        expect(validateEmail('test.email+tag@domain.co.uk')).toBe(true);
    });
    
    test('returns false for invalid email addresses', () => {
        expect(validateEmail('invalid')).toBe(false);
        expect(validateEmail('@example.com')).toBe(false);
        expect(validateEmail('user@')).toBe(false);
        expect(validateEmail('user@example')).toBe(false);
    });
    
    test('returns false for empty or null input', () => {
        expect(validateEmail('')).toBe(false);
        expect(validateEmail(null)).toBe(false);
        expect(validateEmail(undefined)).toBe(false);
    });
    
    test('handles edge cases', () => {
        expect(validateEmail('user.name@sub.domain.com')).toBe(true);
        expect(validateEmail('user+tag@example.com')).toBe(true);
    });
});
```

## Testing Best Practices

**Structure:**
- Group related tests in describe/test classes
- Use descriptive test names that explain what is being tested
- Follow AAA pattern: Arrange, Act, Assert

**Coverage:**
- Test happy paths
- Test edge cases and boundary conditions
- Test error conditions
- Test with different input types
- Test with null/undefined/empty values

**Framework-Specific:**
- **Jest/Mocha**: Use `describe`/`it` or `test`
- **pytest**: Use `test_` prefix, `pytest.fixture` for setup
- **JUnit**: Use `@Test` annotation, `@BeforeEach` for setup
