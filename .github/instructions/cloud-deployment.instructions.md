---
applyTo: "**/{infra,deploy,terraform,bicep,cdk,cloudformation,docker,k8s,kubernetes,helm,vercel,.vercel,netlify}/**/*.{tf,bicep,json,yaml,yml,toml,hcl,Dockerfile}"
---

# Cloud Deployment Security Rules (CSA §2.7)

Apply these rules when generating or modifying infrastructure/deployment code.

## Transport & Encryption
- Enforce HTTPS on all public-facing endpoints. Redirect HTTP to HTTPS.
- Use managed TLS certificates (Let's Encrypt, cloud provider auto-certs).
- Encrypt storage volumes, databases, and object stores at rest using provider-managed keys.

## Firewall & DDoS
- Enable cloud provider firewall and WAF (Web Application Firewall) features.
- Use DDoS mitigation services (Azure DDoS Protection, AWS Shield, Cloudflare).
- Restrict ingress to required ports only; deny all by default.

## Access Control
- Use IAM roles with least privilege. Avoid wildcard (`*`) permissions.
- Enable MFA for all admin and deployment accounts.
- Use SSO/OIDC for team access to cloud consoles and CI/CD.
- Rotate access keys and service credentials regularly.

## Secrets in Deployment
- NEVER hardcode secrets in Dockerfiles, Terraform files, Bicep templates, or YAML manifests.
- Use cloud-native secret stores (Azure Key Vault, AWS Secrets Manager, GCP Secret Manager).
- Reference secrets via environment variables or mounted secret volumes — not build args.

## Environment Variables
- Separate environment variables per environment (dev, staging, production).
- Mark sensitive variables as secret/masked in CI/CD pipelines.
- NEVER expose server-side env vars to client-side bundles.

## Container Security
- Use minimal base images (Alpine, distroless). Avoid running as root.
- Pin image versions by immutable digest (SHA256), not just mutable tags like `latest`. Scan images for CVEs.
- Do not install unnecessary packages or tools in production images.
- Use official images from trusted sources only.
- Verify both integrity and authenticity of images using container signing tools (cosign, notation).
- In Kubernetes, implement admission controllers to enforce signature verification policies.

## Logging & Monitoring
- Enable access logs, audit logs, and application logs.
- Do not log secrets, tokens, or PII in plain text.
- Set up alerts for deployment failures, unusual traffic, and unauthorized access.

## CI/CD Pipeline Security
- Integrate SAST, DAST, and dependency scanning (CodeQL, Semgrep, OWASP Dependency-Check) into CI/CD pipelines.
- Sign commits and artifacts. Verify signatures before deployment.
- Use branch protection rules; require reviews before merging to main.
- Pin GitHub Actions and CI/CD dependencies to specific SHA hashes, not mutable tags. Include version comments alongside SHAs for maintainability.
- Generate Software Bill of Materials (SBOM) using SPDX or CycloneDX tools.
- Use in-toto attestations or similar frameworks for verifiable build provenance.

## Infrastructure-as-Code (IaC) Security
- Restrict access to resources; use secure storage for secrets; validate all inputs in IaC scripts.
- Use the latest versions of IaC dependencies and lock to specific versions.
- When adding external resources (scripts, containers, modules), verify integrity via checksum or signature validation.

## Integrity Verification
- When adding important external resources, include steps to verify integrity (checksum verification or signature validation).
- Use Subresource Integrity (SRI) hashes for CDN-loaded scripts.
- Verify container image signatures from trusted publishers before deployment.
