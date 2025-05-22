---
trigger: always_on
description: Defines logging standards and best practices for the application
---

# Logging Requirements

This document outlines logging practices for consistency, utility, and security. Effective logging is crucial for debugging, monitoring, and understanding application behavior.

## 1. Logger Implementation

*   **1.1. Standardized Loggers**:
    *   Node.js (API) applications **MUST** use `pino`.
    *   React (Web) applications **MUST** use a consistent logging solution (e.g., a custom `Logger` class or a lightweight library like `loglevel`).
*   **1.2. Log Levels**:
    *   Loggers **MUST** support standard levels: `ERROR`, `WARN`, `INFO`, `DEBUG`.
    *   Log levels **MUST** be configurable (default: `INFO` for production, `DEBUG` for development).
*   **1.3. Correlation IDs (API Services)**:
    *   API services **MUST** generate or propagate a correlation ID (e.g., from `x-correlation-id` header) for each request.
    *   This ID **MUST** be included in all log entries related to that request and ideally in API responses for traceability.

## 2. Log Content

*   **2.1. Structured Logging**:
    *   All logs **MUST** be structured (e.g., JSON format) for easier parsing and analysis.
    *   Each log entry **MUST** include: timestamp, log level, service identifier (e.g., 'api-service', 'web-app'), correlation ID (if applicable), and a clear message.
    *   **SHOULD** include additional key-value pairs for contextual data (e.g., `userId`, `orderId`). Avoid embedding structured data within the main message string; use separate fields.
*   **2.2. Sensitive Data Handling**:
    *   Sensitive data (passwords, API keys, full PII, financial details) **MUST NEVER** be logged in clear text.
    *   Implement or use utilities for sanitization/redaction (e.g., masking email addresses, redacting credit card numbers).
    *   Protect sensitive data in all parts of logs, including headers, query parameters, and request/response bodies.
*   **2.3. API Request Logging (API Services)**:
    *   API services **MUST** log incoming requests and outgoing responses at an appropriate level (e.g., `INFO` or `DEBUG`).
    *   Request logs: method, URL, correlation ID, IP address (if permissible), redacted headers/query parameters.
    *   Response logs: method, URL, correlation ID, status code, duration of request processing.

## 3. Error Logging

*   **3.1. Exception Logging**:
    *   All unhandled exceptions and significant operational errors **MUST** be logged at `ERROR` level.
    *   Error logs **MUST** include: error message, error code (if applicable), relevant business identifiers (e.g., `orderId`, `customerId`), and stack trace (especially in non-production environments).
*   **3.2. Validation Error Logging**:
    *   Data validation failures (e.g., invalid API request body) **SHOULD** be logged, typically at `WARN` level.
    *   Include details about which validation failed and (redacted) parts of the input that caused the failure.

## 4. Logging Best Practices

*   **4.1. Performance**:
    *   Logging **MUST** be implemented efficiently to minimize performance impact on the application.
    *   Expensive log generation (e.g., serializing large objects) **SHOULD** be conditional, often limited to `DEBUG` level.
    *   Avoid excessive logging in performance-critical paths or tight loops. High-volume diagnostic logs **MAY** employ sampling.
*   **4.2. Contextual Information**:
    *   Logs **SHOULD** be enriched with relevant application context where possible (e.g., `userId`, `tenantId`, active feature flags).
*   **4.3. Log Management**:
    *   In production, logs **MUST** be sent to a centralized log management system (e.g., ELK stack, Datadog, Splunk).
    *   Configure log rotation (by size or time) and retention policies according to operational and compliance needs.
    *   Configure log rotation (by size or time) and retention policies according to operational and compliance needs.
    *   **SHOULD** configure alerts in the log management system for critical errors, security-related events, or unusual log patterns.
*   **4.5. Compliance and Security**:
    *   Logging practices **MUST** comply with relevant legal and regulatory requirements (e.g., GDPR, HIPAA if applicable).
    *   PII **MUST NOT** be logged unless explicitly required by law or for a legitimate business purpose, and only if appropriately secured and access-controlled. Always review logging of user-specific data for PII.

## 5. AI-Assisted Logging Enhancement

AI tools can help refine logging practices. Refer to `prompt_engineering_guidelines.md`.
