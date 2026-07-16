# Engineering Standards

| Document Information | |
|----------------------|--------------------------------|
| Document Name | Engineering Standards |
| Version | 1.0 |
| Status | Draft |
| Author | Alfa |
| Created | July 2026 |
| Last Updated | July 2026 |

---

# Purpose

This document defines the engineering standards and development practices for the JobAgent AI project.

The goal is to ensure consistency across documentation, source code, architecture, APIs, database design, testing, and deployment.

These standards apply to all development activities and should be followed throughout the lifecycle of the project.

---

# 1. General Principles

The following principles guide all development decisions for the JobAgent AI project.

## 1. Documentation First

Documentation should be created or updated before implementation begins. Clear documentation improves communication, planning, and maintainability.

---

## 2. Simplicity

Prefer simple, readable, and maintainable solutions over complex implementations. Complexity should only be introduced when it provides clear value.

---

## 3. Incremental Development

Develop the project in small, manageable iterations. Complete one feature or task before moving on to the next.

---

## 4. Reusability

Design components, services, APIs, and modules to be reusable whenever practical.

---

## 5. Consistency

Maintain consistent naming conventions, folder structures, coding styles, and documentation throughout the project.

---

## 6. Security by Design

Security should be considered from the beginning rather than added later. Sensitive data must never be hardcoded or exposed.

---

## 7. User-Centered Design

Every feature should provide clear value to the end user. Avoid adding functionality that does not solve a real problem.

---

## 8. Continuous Improvement

Engineering standards should evolve as the project grows. Improvements should be documented through the Decision Log.

---

# 2. Git Workflow

## Workflow

The project follows a feature-based Git workflow.

Every task begins with a GitHub Issue and follows this lifecycle:

```text
Todo
    ↓
In Progress
    ↓
Review (Optional)
    ↓
Done
```

Development workflow:

1. Select a GitHub Issue.
2. Move the issue to **In Progress**.
3. Create or update documentation if required.
4. Implement the feature.
5. Test the implementation.
6. Commit changes using the project's commit message convention.
7. Push changes to GitHub.
8. Close the GitHub Issue.
9. Move the issue to **Done**.

Only one issue should be in **In Progress** at any time (Work In Progress Limit = 1).

---

# 3. Branch Naming Convention

Every Git branch must follow a consistent naming convention.

Format:

```text
<type>/<issue-id>-<short-description>
```

Examples:

```text
feature/JAI-010-dashboard
feature/JAI-025-job-search

bugfix/JAI-042-login-error

hotfix/JAI-051-production-fix

docs/JAI-003-product-vision

refactor/JAI-060-job-service
```

## Branch Types

| Type | Purpose |
|------|---------|
| feature | New functionality |
| bugfix | Bug fixes |
| hotfix | Critical production fixes |
| docs | Documentation updates |
| refactor | Code improvements without changing functionality |
| chore | Maintenance tasks such as dependency updates or configuration changes |

## Rules

- Use lowercase branch names.
- Separate words using hyphens (`-`).
- Always include the GitHub Issue ID.
- Keep names short but descriptive.

---

# 4. Commit Message Convention

All commits must follow the Conventional Commits format with the associated GitHub Issue ID.

## Format

```text
<type>(<issue-id>): <short description>
```

Example:

```text
docs(JAI-001): complete Project Charter

feat(JAI-010): create dashboard

fix(JAI-025): correct application status update
```

## Commit Types

| Type | Purpose |
|------|---------|
| feat | New feature |
| fix | Bug fix |
| docs | Documentation changes |
| refactor | Code restructuring without changing behavior |
| test | Adding or updating tests |
| chore | Maintenance tasks |
| style | Formatting changes (no logic changes) |
| perf | Performance improvements |

## Rules

- Use lowercase commit types.
- Write descriptions in the imperative mood (e.g., "add", "create", "fix").
- Keep the summary concise (preferably under 72 characters).
- Include the GitHub Issue ID whenever applicable.

---

# 5. Folder Structure

## Standard

The repository should maintain a clear and consistent directory structure.

```text
JobAgentAI/
│
├── assets/          # Images, icons, and static resources
├── automation/      # Browser automation services
├── backend/         # Spring Boot application
├── database/        # Database scripts and migrations
├── docs/            # Project documentation
├── frontend/        # Angular application
├── scripts/         # Utility and setup scripts
├── .gitignore
├── README.md
└── LICENSE
```

## Rules

- Each top-level folder should have a single responsibility.
- Avoid placing unrelated files in the repository root.
- Documentation belongs in the `docs/` directory.
- Application code should never be mixed with documentation.
- New top-level folders should only be added when clearly justified.

## Why?

A predictable folder structure improves navigation, onboarding, and long-term maintainability.

---

# 6. Documentation Standards

## Standard

Documentation is considered a first-class project artifact and must be maintained alongside the source code.

## Rules

- All project documentation must be stored in the `docs/` directory.
- Documents should follow the project's standard document template.
- Significant technical or architectural decisions must be recorded in the Decision Log.
- Documentation should be updated whenever a feature, process, or architecture changes.
- Avoid duplicate information across documents. Instead, reference the appropriate document when possible.

## Document Naming

Documents should use the following naming convention:

```text
00-Decision-Log.md
01-Project-Charter.md
02-Engineering-Standards.md
03-Product-Roadmap.md
04-Product-Vision.md
05-Software-Requirements-Specification.md
06-User-Stories.md
07-System-Architecture.md
08-API-Specification.md
09-Technology-Stack.md
```

## Why?

Clear and consistent documentation improves communication, preserves project knowledge, and makes future maintenance significantly easier.

---

# 7. Coding Standards

## Standard

All source code should be written to prioritize readability, maintainability, consistency, and simplicity.

## General Rules

- Write code that is easy to read before optimizing for complexity.
- Follow the established style guide of the programming language or framework.
- Keep functions and methods focused on a single responsibility.
- Avoid duplicated code whenever practical.
- Use meaningful and descriptive names for variables, methods, classes, and files.
- Remove unused code instead of commenting it out.
- Keep files organized and easy to navigate.

## Naming Conventions

| Item | Convention | Example |
|------|------------|---------|
| Class | PascalCase | `JobService` |
| Interface | PascalCase | `JobRepository` |
| Method | camelCase | `getApplications()` |
| Variable | camelCase | `applicationCount` |
| Constant | UPPER_SNAKE_CASE | `MAX_RETRY_COUNT` |
| File | kebab-case (where applicable) | `job-list.component.ts` |

## Framework-Specific Standards

### Angular

- Use standalone components where appropriate.
- Organize code by feature rather than by type.
- Keep components focused on presentation.
- Move business logic into services.
- Use Angular signals or state management consistently where appropriate.

### Spring Boot

- Follow a layered architecture (Controller → Service → Repository).
- Keep controllers thin.
- Place business logic in services.
- Validate incoming requests.
- Return consistent API responses.

### Python (Automation)

- Follow PEP 8 style guidelines.
- Write modular automation scripts.
- Separate browser automation from business logic.
- Handle retries and exceptions gracefully.

## Why?

Consistent coding standards reduce technical debt, improve collaboration, and make the codebase easier to understand and maintain.

---

# 8. Definition of Done (DoD)

## Standard

A GitHub Issue is considered **Done** only when all applicable criteria have been completed.

## General Checklist

- [ ] Requirements are fully implemented.
- [ ] Documentation has been updated (if applicable).
- [ ] Code follows the project's coding standards.
- [ ] No known critical bugs remain.
- [ ] Changes have been tested.
- [ ] Git commits follow the commit message convention.
- [ ] Changes have been pushed to GitHub.
- [ ] The GitHub Issue has been updated.
- [ ] The work has been reviewed (self-review for solo development).
- [ ] The issue is moved to **Done** in the GitHub Project.

## Notes

Not every checklist item applies to every issue. For example, a documentation-only task may not require application testing, but it should still be reviewed for completeness and accuracy.

## Why?

A shared Definition of Done ensures consistent quality, prevents incomplete work from being closed, and provides confidence that each completed issue meets the project's engineering standards.

---

# 9. Code Review Checklist

## Standard

Every completed task should undergo a review before being marked as Done. For a solo developer, this review is a structured self-review.

## Review Checklist

### Functionality

- [ ] The implementation satisfies the requirements.
- [ ] Edge cases have been considered.
- [ ] Existing functionality has not been broken.

### Code Quality

- [ ] Code is readable and easy to understand.
- [ ] Functions and classes have a single responsibility.
- [ ] Naming is meaningful and consistent.
- [ ] Duplicate code has been avoided.

### Documentation

- [ ] Documentation has been updated if necessary.
- [ ] Public APIs or architectural changes are documented.
- [ ] Decision Log has been updated for significant decisions.

### Testing

- [ ] Manual testing has been completed.
- [ ] Automated tests have been added or updated where applicable.

### Git

- [ ] Commit messages follow the project's convention.
- [ ] No unnecessary files are committed.
- [ ] Branch is up to date before merging.

## Why?

A structured review improves software quality, reduces bugs, and encourages continuous improvement. Even in solo projects, reviewing your own work helps identify issues before they become part of the project's history.

---

# 10. API Standards

## Standard

All backend APIs must follow RESTful principles and provide a consistent structure for requests and responses.

## Endpoint Naming

Use plural nouns for resources.

Examples:

```text
GET    /api/v1/jobs
GET    /api/v1/jobs/{id}

POST   /api/v1/applications

PUT    /api/v1/applications/{id}

DELETE /api/v1/applications/{id}
```

## API Versioning

All public APIs must include a version.

Example:

```text
/api/v1/
```

Future versions:

```text
/api/v2/
```

## HTTP Methods

| Method | Purpose |
|---------|----------|
| GET | Retrieve data |
| POST | Create data |
| PUT | Replace existing resource |
| PATCH | Partial update |
| DELETE | Remove resource |

## HTTP Status Codes

| Code | Meaning |
|------|----------|
| 200 | Success |
| 201 | Resource Created |
| 204 | No Content |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict |
| 500 | Internal Server Error |

## Standard Response Format

Successful response:

```json
{
  "success": true,
  "message": "Application retrieved successfully.",
  "data": {}
}
```

Error response:

```json
{
  "success": false,
  "message": "Validation failed.",
  "errors": []
}
```

## Validation

- Validate all incoming requests.
- Never trust client-side validation alone.
- Return meaningful validation messages.

## Why?

Consistent APIs simplify frontend integration, improve maintainability, and provide a predictable developer experience.

---

# 11. Database Standards

## Standard

The database should be designed for clarity, consistency, scalability, and maintainability.

## Naming Conventions

### Tables

- Use lowercase.
- Use plural nouns.
- Separate words using underscores.

Examples:

```text
users
companies
jobs
applications
application_notes
job_skills
```

### Columns

Use lowercase with underscores.

Examples:

```text
first_name
last_name
created_at
updated_at
application_status
```

### Primary Keys

Every table should have a single primary key.

Example:

```text
id
```

### Foreign Keys

Foreign keys should reference the related table name.

Examples:

```text
user_id
company_id
job_id
application_id
```

## Timestamps

Every table should include:

```text
created_at
updated_at
```

Optional:

```text
deleted_at
```

for soft deletes where appropriate.

## Relationships

- Use foreign key constraints.
- Avoid duplicate data whenever practical.
- Normalize data unless denormalization provides a clear performance benefit.

## Migrations

- Database changes must be managed through version-controlled migrations.
- Avoid manual schema changes in production.

## Indexing

Create indexes for:

- Frequently searched columns
- Foreign keys
- Unique fields where appropriate

## Why?

Consistent database standards improve data integrity, simplify maintenance, and make future schema evolution safer and more predictable.

---
# 12. Security Standards

## Standard

Security must be considered throughout the entire software development lifecycle. Every feature should be designed and implemented with security in mind.

## Authentication

- Authentication must be handled using JWT access tokens.
- Passwords must never be stored in plain text.
- Passwords must be hashed using a strong algorithm (e.g., BCrypt).
- Authentication secrets must never be committed to the repository.

## Authorization

- Every protected endpoint must validate the user's permissions.
- Apply the principle of least privilege.
- Users should only access resources they are authorized to use.

## Sensitive Data

- Store secrets and API keys in environment variables.
- Never hardcode credentials or tokens.
- Never expose sensitive information in API responses or logs.

## Input Validation

- Validate all incoming requests on the backend.
- Sanitize user input where appropriate.
- Prevent SQL injection by using parameterized queries or ORM features.
- Validate uploaded files for type and size.

## API Security

- Use HTTPS in production.
- Return generic error messages for unexpected server errors.
- Apply rate limiting where appropriate.
- Log security-related events without exposing sensitive data.

## Dependencies

- Keep project dependencies up to date.
- Remove unused libraries.
- Regularly review dependencies for known vulnerabilities.

## Logging

- Never log passwords, tokens, or sensitive personal information.
- Log sufficient information to support debugging and auditing.

## Why?

Building security into the project from the beginning reduces risk, protects user data, and creates a stronger foundation for future features.