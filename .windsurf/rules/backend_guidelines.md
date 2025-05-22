---
trigger: glob
description: Defines backend development guidelines for Hono API applications
globs: packages/api/**/*.{ts,js}
---

# Backend Development Guidelines

These guidelines build upon the core coding conventions and are specific to backend development with Hono.

## API Structure

1. **Route Organization**
   - Organize routes by domain/resource
   - Use kebab-case for route file names (e.g., `user-routes.ts`)
   - Group related endpoints in the same file
   - Follow RESTful principles for API design

2. **Endpoint Design**
   - Use appropriate HTTP methods (GET, POST, PUT, DELETE, PATCH)
   - Return consistent response formats
   - Use meaningful status codes
   - Implement proper error handling
   - Version APIs when necessary

3. **Controller Pattern**
   - Separate route definitions from business logic
   - Keep route handlers thin, delegating to service functions
   - Use middleware for cross-cutting concerns

## Middleware

1. **Middleware Usage**
   - Use middleware for cross-cutting concerns like authentication, logging, etc.
   - Chain middleware in a logical order
   - Keep middleware focused on a single responsibility
   - Use middleware for input validation

2. **Common Middleware**
   - Authentication middleware
   - Request validation middleware
   - Error handling middleware
   - Logging middleware
   - CORS middleware

## Service Layer

1. **Service Organization**
   - Implement business logic in service classes/functions
   - Keep services focused on a single domain
   - Use dependency injection for external dependencies
   - Make services testable by avoiding direct dependencies

2. **Service Patterns**
   - Use factory functions or classes for services
   - Implement proper error handling
   - Return domain objects rather than database entities

## Database Access

1. **Drizzle ORM Usage**
   - Define schemas in dedicated files
   - Use migrations for schema changes
   - Implement repository pattern for database access
   - Keep database queries optimized
   - Use transactions when necessary

2. **Query Patterns**
   - Use parameterized queries to prevent SQL injection
   - Implement pagination for large result sets
   - Use appropriate indexes for frequent queries
   - Handle database errors gracefully

## Authentication & Authorization

1. **Auth Implementation**
   - Use JWT for stateless authentication
   - Implement proper token validation
   - Use secure cookie settings
   - Implement role-based access control
   - Never store sensitive information in tokens

2. **Security Patterns**
   - Implement rate limiting
   - Use HTTPS for all endpoints
   - Validate and sanitize all inputs
   - Implement proper CORS settings

## Error Handling

1. **Error Patterns**
   - Create custom error classes
   - Return consistent error responses
   - Log errors with appropriate severity
   - Include enough information for debugging without exposing sensitive details

2. **Error Response Format**
   ```typescript
   {
     error: {
       code: string;       // Error code
       message: string;    // User-friendly message
       details?: any;      // Optional additional details
     }
   }
   ```

## Logging

1. **Logging Practices**
   - Use appropriate log levels (debug, info, warn, error)
   - Include request IDs in logs for traceability
   - Log request/response details for debugging
   - Avoid logging sensitive information

## Testing

1. **API Testing**
   - Test each endpoint for success and failure cases
   - Mock external dependencies
   - Test middleware in isolation
   - Implement integration tests for critical flows

## Performance

1. **Optimization Techniques**
   - Use caching for frequently accessed data
   - Optimize database queries
   - Implement connection pooling
   - Use appropriate indexes

## Documentation

1. **API Documentation**
   - Document all endpoints
   - Include request/response examples
   - Document error responses
   - Keep documentation up to date

## Environment Configuration

1. **Configuration Management**
   - Use environment variables for configuration
   - Provide sensible defaults
   - Validate configuration at startup
   - Document required environment variables