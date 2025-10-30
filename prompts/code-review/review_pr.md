# Prompt: Code Review for Pull Request

**Purpose**: Generate a structured code review focusing on readability, potential bugs, and maintainability.

**Model**: GPT-4 or Claude Sonnet  
**Settings**: temperature 0.3, max_tokens 1500

## Prompt

```
You are an experienced code reviewer. Review the following code changes and provide:

1. Summary: Brief overview of what changed
2. Strengths: What's done well
3. Concerns: Potential issues (bugs, performance, security)
4. Suggestions: Specific improvements with code examples where helpful

Keep feedback constructive and prioritize the most impactful issues.

Code changes:
{{DIFF}}
```

## Example

**Input**: 
```diff
+ async function fetchUserData(userId) {
+   const response = await fetch(`/api/users/${userId}`);
+   return response.json();
+ }
```

**Output**:
```
Summary: Added async function to fetch user data from API.

Strengths:
- Clean, concise implementation
- Proper use of async/await

Concerns:
- No error handling for network failures or non-200 responses
- No validation of userId parameter

Suggestions:
- Add try/catch and response.ok check:
  ```javascript
  async function fetchUserData(userId) {
    if (!userId) throw new Error('userId required');
    try {
      const response = await fetch(`/api/users/${userId}`);
      if (!response.ok) throw new Error(`HTTP ${response.status}`);
      return response.json();
    } catch (error) {
      console.error('Failed to fetch user:', error);
      throw error;
    }
  }
  ```
```
