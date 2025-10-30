# Prompt: Extract Function Refactoring

**Purpose**: Identify code blocks that should be extracted into separate functions and suggest the refactoring.

**Model**: GPT-4 or Claude Sonnet  
**Settings**: temperature 0.2, max_tokens 1000

## Prompt

```
You are a refactoring expert. Analyze the following code and identify opportunities to extract functions.

For each suggestion:
1. Identify the code block to extract
2. Propose a descriptive function name
3. Show the refactored code
4. Explain the benefit

Code:
{{CODE}}
```

## Example

**Input**:
```javascript
function processOrder(order) {
  // Validate order
  if (!order.items || order.items.length === 0) {
    throw new Error('Order must have items');
  }
  if (!order.customerId) {
    throw new Error('Order must have customer');
  }
  
  // Calculate total
  let total = 0;
  for (const item of order.items) {
    total += item.price * item.quantity;
  }
  
  // Apply discount
  if (order.coupon) {
    total = total * (1 - order.coupon.discount);
  }
  
  return { ...order, total };
}
```

**Output**:
```
Suggestions:

1. Extract validation logic → `validateOrder(order)`
2. Extract calculation logic → `calculateTotal(items, coupon)`

Refactored:
```javascript
function validateOrder(order) {
  if (!order.items || order.items.length === 0) {
    throw new Error('Order must have items');
  }
  if (!order.customerId) {
    throw new Error('Order must have customer');
  }
}

function calculateTotal(items, coupon = null) {
  let total = items.reduce((sum, item) => 
    sum + (item.price * item.quantity), 0);
  
  if (coupon) {
    total *= (1 - coupon.discount);
  }
  
  return total;
}

function processOrder(order) {
  validateOrder(order);
  const total = calculateTotal(order.items, order.coupon);
  return { ...order, total };
}
```

Benefits:
- Each function has single responsibility
- Validation and calculation logic reusable
- Main function easier to test and understand
```
