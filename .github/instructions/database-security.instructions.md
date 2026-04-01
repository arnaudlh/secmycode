---
applyTo: "**/{models,db,database,repositories,migrations,queries,prisma,drizzle,sequelize,typeorm,knex,sqlalchemy,entity}/**/*.{ts,js,py,java,cs,go,rb,php,sql}"
---

# Database Security Rules (CSA §2.5 — OWASP Database Security)

Apply these rules when generating or modifying database access code.

## Parameterized Queries
- ALWAYS use parameterized queries or prepared statements. NEVER concatenate user input into SQL strings.
- Use ORM query builders (Prisma, Drizzle, TypeORM, SQLAlchemy, Entity Framework) for safe query construction.
- If raw SQL is necessary, use parameter placeholders (`$1`, `?`, `:param`) — never template literals with user data.

## Data Encryption
- Encrypt sensitive data at rest using AES-256 or equivalent.
- Use cloud provider KMS (Azure Key Vault, AWS KMS, GCP Cloud KMS) for key management.
- Hash passwords with bcrypt, scrypt, or Argon2 — never MD5 or SHA-1 alone.
- Encrypt database connections with TLS; require `sslmode=require` or equivalent.

## Least Privilege Access
- Connect to databases with the minimum permissions required (read-only where possible).
- Use separate database users/roles for different application components.
- Never use root/admin credentials in application connection strings.
- Regularly audit and revoke unused database permissions.

## No Direct Frontend Access
- NEVER expose database connections or credentials to client-side/frontend code.
- Always route data access through server-side API routes or backend services.
- Use API layers to enforce authorization before any database operation.

## Backup & Recovery
- Ensure automated, encrypted backups are configured.
- Test restore procedures regularly.
- Store backups in a separate location from the primary database.

## Monitoring & Auditing
- Enable query logging and monitor for unusual patterns (mass deletes, unexpected schema changes).
- Set alerts for suspicious activity (off-hours access, privilege escalation).
- Log database access without recording sensitive data values or PII in logs.
- Use logging frameworks that can be configured for security; never log query parameters containing user data.
