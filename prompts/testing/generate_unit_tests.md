# Prompt: Generate Unit Tests

**Purpose**: Create unit tests for a given function or class, covering edge cases and error conditions.

**Model**: GPT-4 or Claude Sonnet  
**Settings**: temperature 0.2, max_tokens 1200

## Prompt

```
You are a test-driven development expert. Generate comprehensive unit tests for the following code.

Include:
1. Happy path tests
2. Edge cases
3. Error conditions
4. Clear test descriptions

Use the testing framework appropriate for the language, or specify: {{FRAMEWORK}}

Code to test:
{{CODE}}
```

## Example

**Input**:
```javascript
function calculateDiscount(price, discountPercent) {
  if (discountPercent < 0 || discountPercent > 100) {
    throw new Error('Discount must be between 0 and 100');
  }
  return price * (1 - discountPercent / 100);
}
```

**Output** (Jest):
```javascript
describe('calculateDiscount', () => {
  test('applies 10% discount correctly', () => {
    expect(calculateDiscount(100, 10)).toBe(90);
  });

  test('applies 0% discount (no discount)', () => {
    expect(calculateDiscount(100, 0)).toBe(100);
  });

  test('applies 100% discount (free)', () => {
    expect(calculateDiscount(100, 100)).toBe(0);
  });

  test('handles decimal prices', () => {
    expect(calculateDiscount(19.99, 15)).toBeCloseTo(16.99, 2);
  });

  test('throws error for negative discount', () => {
    expect(() => calculateDiscount(100, -5))
      .toThrow('Discount must be between 0 and 100');
  });

  test('throws error for discount over 100', () => {
    expect(() => calculateDiscount(100, 101))
      .toThrow('Discount must be between 0 and 100');
  });

  test('handles zero price', () => {
    expect(calculateDiscount(0, 50)).toBe(0);
  });
});
```
