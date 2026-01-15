---
name: performance-analyzer
description: Analyzes code for performance issues including inefficient algorithms, unnecessary computations, memory leaks, large file sizes, slow queries, and missing caching. Returns structured performance issue reports with optimization suggestions.
---

# Performance Analyzer Skill

## Instructions

1. Analyze code for performance issues
2. Check for inefficient algorithms (O(n²) when O(n) possible)
3. Identify unnecessary computations or redundant operations
4. Look for memory leaks or inefficient memory usage
5. Check file sizes and resource usage
6. Review database queries for optimization opportunities
7. Check for missing caching where beneficial
8. Return structured performance reports with:
   - File path and line numbers
   - Performance issue type
   - Current code
   - Suggested optimization
   - Expected performance improvement
   - Priority (Must-Fix for blocking issues, Should-Fix for optimizations)

## Examples

**Input:** Inefficient nested loop
**Output:**
```markdown
### PERF-001
- **File**: `utils.js`
- **Lines**: 30-35
- **Priority**: Should-Fix
- **Issue**: O(n²) nested loop when O(n) solution is possible
- **Current Code**:
  ```javascript
  function findDuplicates(arr1, arr2) {
      const duplicates = [];
      for (let i = 0; i < arr1.length; i++) {
          for (let j = 0; j < arr2.length; j++) {
              if (arr1[i] === arr2[j]) {
                  duplicates.push(arr1[i]);
              }
          }
      }
      return duplicates;
  }
  ```
- **Suggested Fix**:
  ```javascript
  function findDuplicates(arr1, arr2) {
      const set2 = new Set(arr2);
      return arr1.filter(item => set2.has(item));
  }
  ```
- **Reason**: Using Set reduces time complexity from O(n²) to O(n)
- **Expected Improvement**: Significant performance gain for large arrays
```

## Performance Issues to Detect

- **Inefficient Algorithms**: O(n²) or worse when better solutions exist
- **Unnecessary Computations**: Redundant calculations, repeated operations
- **Memory Leaks**: Unclosed resources, circular references, event listeners
- **Large File Sizes**: Unoptimized images, large bundles, unnecessary dependencies
- **Slow Queries**: N+1 queries, missing indexes, inefficient joins
- **Missing Caching**: Repeated expensive operations without caching
- **Blocking Operations**: Synchronous operations that should be async
- **Inefficient Data Structures**: Wrong data structure for use case
- **Unoptimized Loops**: Inefficient loop patterns
- **Resource Loading**: Missing lazy loading, blocking resources

## Priority Guidelines

- **Must-Fix**: Performance issues that block functionality or cause timeouts
- **Should-Fix**: Performance optimizations that improve user experience
- **Nice-to-Have**: Minor optimizations with small impact
