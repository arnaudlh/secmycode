---
description: "Generate secure database queries with parameterized statements, least privilege, and proper error handling"
mode: "edit"
---

# Generate Secure Database Query

Generate secure database access code following **CSA Secure Vibe Coding Guide §2.5** (Database Security) with these mandatory controls:

1. **Parameterized Queries**: Use prepared statements or ORM query builders — NEVER concatenate user input into queries.
2. **Least Privilege**: Use a database connection role with minimum required permissions (read-only where possible).
3. **Input Validation**: Validate and sanitize all inputs BEFORE passing to the query layer.
4. **Error Handling**: Catch database errors. Return generic messages to the caller. Log full errors server-side.
5. **Connection Security**: Use TLS-encrypted connections (`sslmode=require`).
6. **Credential Management**: Load connection strings from environment variables, never hardcode.
7. **Result Filtering**: Select only required columns. Never use `SELECT *` for API-facing queries.
8. **Password Hashing**: If storing passwords, use bcrypt/scrypt/Argon2. Never store plain text or use MD5/SHA-1 alone.
9. **No Frontend Access**: Database logic MUST be in server-side code, never exposed to the client.
10. **Transactions**: Use transactions for multi-step operations to ensure data consistency.

## Query Requirements

#{input:Describe the database operation you need (read/write, table, fields, conditions)}
