---
name: code-documentation
description: Generate comprehensive code documentation including docstrings, comments, and API documentation. Use when code lacks documentation, needs better explanations, or requires API docs. Focuses on clarity, completeness, and following language-specific documentation standards.
---

# Code Documentation Skill

## Instructions

1. Analyze the code structure to understand what needs documentation
2. Generate docstrings/comments following language conventions:
   - Python: Google, NumPy, or Sphinx style
   - JavaScript/TypeScript: JSDoc format
   - Go: Standard Go doc comments
   - Java: JavaDoc format
3. Document:
   - Function/method purpose and behavior
   - Parameters with types and descriptions
   - Return values with types and descriptions
   - Exceptions/errors that may be raised
   - Usage examples when helpful
   - Edge cases and important notes
4. Add inline comments for complex logic or non-obvious code
5. Generate API documentation when requested
6. Keep documentation concise but complete
7. Use clear, professional language

## Examples

**Input (Python function without docs):**
```python
def calculate_total(items, tax_rate=0.1):
    subtotal = sum(item.price for item in items)
    return subtotal * (1 + tax_rate)
```

**Output:**
```python
def calculate_total(items: List[Item], tax_rate: float = 0.1) -> float:
    """
    Calculate the total price including tax for a list of items.
    
    Args:
        items: List of Item objects with a price attribute
        tax_rate: Tax rate as a decimal (default: 0.1 for 10%)
    
    Returns:
        Total price including tax as a float
    
    Example:
        >>> items = [Item(price=10.0), Item(price=20.0)]
        >>> calculate_total(items, tax_rate=0.08)
        32.4
    """
    subtotal = sum(item.price for item in items)
    return subtotal * (1 + tax_rate)
```

**Input (JavaScript function):**
```javascript
function processUserData(data) {
    const filtered = data.filter(u => u.active);
    return filtered.map(u => ({ id: u.id, name: u.name }));
}
```

**Output:**
```javascript
/**
 * Process user data by filtering active users and extracting key fields.
 * 
 * @param {Array<Object>} data - Array of user objects
 * @param {boolean} data[].active - Whether the user is active
 * @param {string} data[].id - User identifier
 * @param {string} data[].name - User display name
 * @returns {Array<Object>} Array of processed user objects with id and name
 * 
 * @example
 * const users = [
 *   { id: '1', name: 'Alice', active: true },
 *   { id: '2', name: 'Bob', active: false }
 * ];
 * processUserData(users); // [{ id: '1', name: 'Alice' }]
 */
function processUserData(data) {
    const filtered = data.filter(u => u.active);
    return filtered.map(u => ({ id: u.id, name: u.name }));
}
```

## Documentation Standards

**Python:**
- Use Google or NumPy style docstrings
- Include type hints when possible
- Document exceptions with `Raises:`
- Add `Example:` section for complex functions

**JavaScript/TypeScript:**
- Use JSDoc format with `@param`, `@returns`, `@throws`
- Include type information in JSDoc comments
- Add `@example` for usage demonstrations
