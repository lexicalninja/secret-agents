---
name: test-writer
description: Writes comprehensive test cases including unit tests, integration tests, and E2E tests. Use when implementing test requirements from tasks. Creates tests that cover happy paths, edge cases, error conditions, and follow testing best practices.
---

# Test Writer Skill

## Instructions

1. Analyze test requirements from task
2. Identify what needs to be tested (functions, components, endpoints)
3. Write unit tests for individual functions/components
4. Write integration tests for component interactions
5. Write E2E tests for user flows (if applicable)
6. Cover happy paths, edge cases, and error conditions
7. Ensure tests are independent and isolated
8. Return test implementation with:
   - Test files
   - Test cases covering all scenarios
   - Setup and teardown
   - Mocking where needed
   - Assertions and expectations

## Examples

**Input:** "Write tests for calculateTotal function"
**Output:**
```javascript
// tests/utils.test.js
describe('calculateTotal', () => {
    test('calculates total for valid items array', () => {
        const items = [
            { price: 10.00 },
            { price: 20.00 },
            { price: 5.00 }
        ];
        expect(calculateTotal(items)).toBe(35.00);
    });

    test('returns 0 for empty array', () => {
        expect(calculateTotal([])).toBe(0);
    });

    test('returns 0 for null input', () => {
        expect(calculateTotal(null)).toBe(0);
    });

    test('returns 0 for undefined input', () => {
        expect(calculateTotal(undefined)).toBe(0);
    });

    test('handles items with zero price', () => {
        const items = [
            { price: 10.00 },
            { price: 0 },
            { price: 5.00 }
        ];
        expect(calculateTotal(items)).toBe(15.00);
    });
});
```

## Test Types

- **Unit Tests**: Test individual functions/components in isolation
- **Integration Tests**: Test component interactions, API integrations
- **E2E Tests**: Test complete user flows
- **Snapshot Tests**: Test component rendering (if applicable)
- **Performance Tests**: Test performance characteristics (if needed)

## Test Coverage Areas

- **Happy Paths**: Normal, expected behavior
- **Edge Cases**: Boundary conditions, empty inputs, null values
- **Error Conditions**: Invalid inputs, error handling
- **State Changes**: Component state transitions
- **User Interactions**: Click, input, navigation
- **API Responses**: Success and error responses

## Best Practices

- **Independent Tests**: Each test should be independent
- **Clear Names**: Descriptive test names
- **Arrange-Act-Assert**: Follow AAA pattern
- **Mock External Dependencies**: Mock APIs, databases, etc.
- **Test One Thing**: Each test should test one behavior
- **Fast Tests**: Tests should run quickly
- **Maintainable**: Tests should be easy to understand and maintain
