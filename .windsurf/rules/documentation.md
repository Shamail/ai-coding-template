---
trigger: glob
globs: **/*.{ts,tsx,js,jsx,md}
---

# Documentation Guidelines

This document outlines documentation guidelines and practices to ensure consistent and comprehensive documentation across the application.

## Code Documentation

1. **JSDoc Comments**
   - Use JSDoc comments for all public APIs, functions, and classes
   - Include parameter descriptions, return types, and examples
   - Document thrown exceptions and edge cases
   - Keep comments up to date with code changes
   - Example:
     ```typescript
     /**
      * Retrieves a user by their unique identifier.
      * @param {string} id - The unique identifier of the user.
      * @returns {Promise<User>} The user object if found.
      * @throws {NotFoundError} If the user does not exist.
      * @example
      * const user = await getUserById('123');
      */
     async function getUserById(id: string): Promise<User> {
       // Implementation
     }
     ```

2. **Inline Comments**
   - Use inline comments for complex or non-obvious code
   - Focus on explaining "why" rather than "what"
   - Keep comments concise and relevant
   - Update comments when code changes

3. **Type Definitions**
   - Document complex types and interfaces
   - Explain the purpose and usage of each property
   - Provide examples for complex types
   - Example:
     ```typescript
     /**
      * Represents a user in the system.
      */
     interface User {
       /** Unique identifier for the user */
       id: string;
       /** User's full name */
       name: string;
       /** User's email address */
       email: string;
       /** User's role in the system */
       role: UserRole;
     }
     ```

## README Files

1. **Project README**
   - Include project overview and purpose
   - Document setup and installation instructions
   - List key features and technologies
   - Provide usage examples
   - Include contribution guidelines
   - Add license information

2. **Package READMEs**
   - Create README.md files for each package
   - Document package purpose and responsibilities
   - List key components and services
   - Provide usage examples
   - Document package-specific configuration

## API Documentation

1. **API Endpoints**
   - Document all API endpoints
   - Include HTTP method, path, and description
   - Document request parameters and body schema
   - Document response format and status codes
   - Provide example requests and responses
   - Document error responses and codes

2. **API Documentation Format**
   ```markdown
   # Endpoint Name
   
   **URL:** `/api/resource`
   **Method:** `GET`
   **Auth required:** Yes
   
   ## Description
   Brief description of what this endpoint does.
   
   ## Query Parameters
   | Parameter | Type   | Required | Description           |
   |-----------|--------|----------|-----------------------|
   | param1    | string | Yes      | Description of param1 |
   
   ## Request Body
   ```json
   {
     "property": "value"
   }
   ```
   
   ## Success Response
   **Code:** 200 OK
   ```json
   {
     "data": {}
   }
   ```
   
   ## Error Response
   **Code:** 400 BAD REQUEST
   ```json
   {
     "error": {
       "code": "INVALID_INPUT",
       "message": "Error message"
     }
   }
   ```
   ```

3. **API Documentation Generation**
   - Generate API documentation from code when possible
   - Store API documentation in `docs/api/` directory
   - Update documentation when API changes
   - Include versioning information

## Architecture Documentation

1. **Architecture Overview**
   - Document system architecture
   - Include component diagrams
   - Explain design decisions and trade-offs
   - Document system dependencies and integrations
   - Store in `docs/architecture/` directory

2. **Data Flow Documentation**
   - Document key data flows
   - Include sequence diagrams for complex operations
   - Explain state management
   - Document database schema and relationships

## User Guides

1. **User Guide Structure**
   - Create guides for key features and workflows
   - Include step-by-step instructions
   - Add screenshots and examples
   - Store in `docs/guides/` directory
   - Keep guides up to date with feature changes

## TODO Documentation

1. **TODO Format**
   - Use consistent TODO format in code comments
   - Include issue reference when applicable
   - Categorize TODOs by type (bug, enhancement, refactor)
   - Add priority and assignee when known
   - Example:
     ```typescript
     // TODO(high): Implement proper error handling for API responses
     // TODO(medium): Optimize query performance
     // TODO(low): Add additional unit tests
     ```

2. **TODO Extraction**
   - Automatically extract TODOs from code comments
   - Generate TODO reports in `docs/todos/` directory
   - Update TODO reports regularly
   - Track TODO completion

## Documentation Maintenance

1. **Documentation Review**
   - Review documentation during code reviews
   - Update documentation when code changes
   - Remove outdated documentation
   - Ensure documentation accuracy and completeness

2. **Documentation Standards**
   - Use consistent formatting and style
   - Write in clear, concise language
   - Use examples to illustrate complex concepts
   - Target documentation for the appropriate audience

## Automated Documentation

1. **Documentation Generation**
   - Use automated tools to generate documentation when possible
   - Generate API documentation from code comments
   - Extract TODOs automatically
   - Update generated documentation in CI/CD pipeline

2. **Documentation Verification**
   - Verify documentation links and references
   - Check for outdated information
   - Ensure documentation coverage for all features
   - Validate code examples
