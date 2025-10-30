# Prompt: Task Breakdown and Planning

**Purpose**: Break down a large task or feature into smaller, actionable subtasks with clear dependencies.

**Model**: GPT-4 or Claude Sonnet  
**Settings**: temperature 0.4, max_tokens 1200

## Prompt

```
You are a technical project planner. Break down the following task into concrete, implementable subtasks.

For each subtask provide:
1. Clear title
2. Description of what needs to be done
3. Estimated complexity (Small/Medium/Large)
4. Dependencies (which tasks must be done first)

Present as a numbered list, ordered by logical implementation sequence.

Task:
{{TASK_DESCRIPTION}}
```

## Example

**Input**:
```
Add user authentication to the application with email/password login and session management.
```

**Output**:
```
1. Database schema for users [Medium]
   - Create users table (id, email, password_hash, created_at)
   - Add indexes on email
   Dependencies: None

2. Password hashing utility [Small]
   - Implement bcrypt wrapper functions
   - Add salt rounds configuration
   Dependencies: None

3. User registration endpoint [Medium]
   - POST /api/auth/register
   - Validate email format and password strength
   - Hash password and store user
   Dependencies: #1, #2

4. Login endpoint [Medium]
   - POST /api/auth/login
   - Verify credentials
   - Generate session token
   Dependencies: #1, #2

5. Session management [Large]
   - Create sessions table
   - Implement session creation/validation middleware
   - Add token refresh logic
   Dependencies: #1, #4

6. Protected route middleware [Small]
   - Check for valid session
   - Attach user to request object
   Dependencies: #5

7. Logout endpoint [Small]
   - POST /api/auth/logout
   - Invalidate session
   Dependencies: #5

8. Integration tests [Medium]
   - Test registration flow
   - Test login/logout
   - Test protected routes
   Dependencies: All above
```
