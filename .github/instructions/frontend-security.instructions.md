---
applyTo: "**/*.{html,htm,jsx,tsx,vue,svelte,astro,ejs,hbs,pug}"
---

# Frontend Security Rules (CSA §2.1, §2.2, §2.7)

Apply these rules when generating or modifying frontend/UI code.

## Cross-Site Scripting (XSS) Prevention
- Use framework auto-escaping (React JSX, Vue templates, Angular DomSanitizer).
- NEVER use `dangerouslySetInnerHTML`, `v-html`, or `innerHTML` with user-supplied data without sanitization.
- When raw HTML rendering is required, sanitize with DOMPurify or equivalent before insertion.
- Encode all dynamic content rendered in HTML attributes, JavaScript, CSS, and URLs.

## Content Security Policy (CSP)
- Set a strict Content-Security-Policy header; avoid `unsafe-inline` and `unsafe-eval`.
- Use nonces or hashes for inline scripts when unavoidable.

## Sensitive Data in the Browser
- NEVER store secrets, API keys, or tokens in client-side JavaScript, localStorage, or sessionStorage.
- Use `httpOnly`, `secure`, and `sameSite` flags on cookies carrying session tokens.
- Do not embed backend credentials or connection strings in frontend bundles.

## CORS & Fetch Security
- Set `credentials: 'include'` or `'same-origin'` only when needed.
- Avoid fetch requests to untrusted or user-controlled URLs (SSRF risk).
- Validate redirect URLs to prevent open redirect vulnerabilities.

## Form Security
- Include CSRF tokens on all state-changing forms.
- Validate form inputs client-side AND server-side (client-side alone is insufficient).
- Use `autocomplete="off"` on sensitive fields (credit card, password) when appropriate.

## Dependency Security
- Do not load scripts from untrusted third-party CDNs without Subresource Integrity (SRI) hashes.
- Audit frontend dependencies for known vulnerabilities (`npm audit`, `yarn audit`).

## Debug Artifacts
- Remove all `console.log()`, `console.debug()`, `alert()`, and debugging UI before production.
- Ensure source maps are not deployed to production environments.

## Mobile & Desktop App Security
- Do not store sensitive data in plaintext on the device.
- Use the platform's secure storage APIs (Android EncryptedSharedPreferences, iOS Keychain, Windows DPAPI).
- Prefer high-level libraries for cryptography rather than custom implementations.
