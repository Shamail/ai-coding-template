---
trigger: always_on
description: Defines security guidelines and best practices for the application
---

# Security Guidelines

This document outlines security best practices.

## Authentication & Authorization
1.  **Auth Implementation:** Use standards (JWT, OAuth). Hash passwords (bcrypt/Argon2). Secure tokens, refresh, set expirations. MFA if applicable.
2.  **Auth Controls:** RBAC. Validate auth per request. Least privilege. Resource-based auth. No client-side auth checks.
3.  **Session Mgmt:** Secure handling. Timeout. Regenerate IDs post-auth. Validate session data. Proper logout.

## Input Validation & Output Encoding
1.  **Input Validation:** Validate all inputs (params, body, headers). Schema validation (Zod, Joi). Type checks. Validate type, format, range, size. Reject invalid input.
2.  **Output Encoding:** Encode dynamic output (prevent XSS). Context-aware encoding (HTML, URL, JS). CSP. Sanitize HTML. Safe templating.

## Data Protection
1.  **Sensitive Data:** No client-side storage. Encrypt at rest. HTTPS. Mask data in logs/UI. Data retention policies.
2.  **DB Security:** Parameterized queries (no SQLi). DB user access controls. Encrypt sensitive DB data. Secure connection strings. DB auditing if needed.

## API Security
1.  **API Protection:** Rate limiting. HTTPS. Validate content types. CORS. Appropriate HTTP methods/status codes.
2.  **API Keys & Secrets:** No client-side keys. Rotate keys/secrets. Env vars for secrets. Key access controls. Secret management services.

## Frontend Security
1.  **Client-Side Security:** CSP. Subresource Integrity (SRI). CORS. No sensitive client-side storage. Sanitize user content.
2.  **Form Security:** CSRF protection. Validate inputs. Error handling. Secure submission (HTTPS). Rate limit submissions.

## File Upload Security
1.  **File Validation:** Validate type, size, content. Malware scan. Store outside web root. Random filenames. Access controls.

## Error Handling & Logging
1.  **Secure Errors:** No sensitive info in errors. Custom error pages. Log errors with context. Diff messages for users/logs. Handle exceptions.
2.  **Security Logging:** Log security events. Log rotation/retention. Protect logs. Context in logs. No sensitive data in logs.

## Dependency Management
1.  **Dependency Security:** Regular updates. Scanning tools. Pin versions. Audit for vulnerabilities. Minimize usage.

## Security Headers
1.  **HTTP Headers:** Content-Security-Policy. X-Content-Type-Options: nosniff. X-Frame-Options. Strict-Transport-Security (HSTS). Referrer-Policy.

## Security Testing
1.  **Testing Practices:** Security unit tests. Code reviews. SAST. DAST. Test OWASP Top 10.

## Deployment Security
1.  **Secure Deployment:** Secure pipelines. Access controls. Scan containers/dependencies. Immutable infra. Secrets management.

## Incident Response
1.  **Incident Handling:** Logging for investigation. Clear procedures. Detection mechanisms. Vulnerability disclosure plan. Document decisions.

## 14. AI-Assisted Security Enhancement
AI augments, not replaces, security expertise. Use for issue ID, boilerplate, understanding. Review AI advice/code. See `prompt_engineering_guidelines.md`.

### 14.1. Vulnerability ID Aid
*   **AI Action:** Give code/configs to AI for common vulnerability checks (OWASP Top 10).
*   **AI Prompt:** Ask AI to review code for XSS, suggest mitigations.
*   **Benefit:** Supplements SAST/reviews by spotting anti-patterns.

### 14.2. Secure Code Gen (Boilerplate)
*   **AI Action:** Ask AI for security feature boilerplate (best practices).
*   **AI Prompt:** Ask for password hashing code (bcrypt) or basic CSP.
*   **Benefit:** Quick start for security. *Always verify/test AI-gen security code.*

### 14.3. Security Policy & Compliance Aid
*   **AI Action:** Use AI to draft/review policies or understand compliance.
*   **AI Prompt:** Ask for help drafting data retention policy (GDPR) or explaining PCI DSS.
*   **Benefit:** Summarizes complex standards, helps structure policies.

### 14.4. Security Config Review
*   **AI Action:** Give security configs (firewall, IAM) to AI for review.
*   **AI Prompt:** Ask AI to review S3 bucket policy for misconfigs.
*   **Benefit:** Helps ID common misconfigs.

### 14.5. Threat Modeling Ideas
*   **AI Action:** Describe system/feature to AI for threat brainstorming.
*   **AI Prompt:** Ask for threats for a password reset via email feature.
*   **Benefit:** Aids initial threat modeling.