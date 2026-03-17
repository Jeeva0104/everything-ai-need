# Claude Code Common Rules

## Development Workflow

### Research & Reuse (Mandatory)
- Run `gh search repos` and `gh search code` before writing new code
- Use Context7 or primary vendor docs to confirm API behavior
- Use Exa only when GitHub search and docs are insufficient
- Search npm, PyPI, crates.io, and other registries before writing utility code
- **Prefer battle-tested libraries over hand-rolled solutions**
- **Look for open-source projects that solve 80%+ of the problem**
- **Prefer adopting or porting a proven approach over writing net-new code**

### Planning
- Use **planner** agent to create implementation plan
- Generate planning docs before coding: PRD, architecture, system_design, tech_doc, task_list
- Identify dependencies and risks
- Break down work into phases

### TDD Approach
- Use **tdd-guide** agent
- Write tests first (RED phase)
- Implement to pass tests (GREEN phase)
- Refactor (IMPROVE phase)
- **Verify 80%+ coverage**

### Code Review
- Use **code-reviewer** agent immediately after writing code
- Address CRITICAL and HIGH issues first
- Fix MEDIUM issues when possible

## Testing Rules

### Coverage Requirement
- **Minimum 80% test coverage** is mandatory

### Required Test Types (ALL Required)
- **Unit Tests** - For individual functions, utilities, components
- **Integration Tests** - For API endpoints, database operations
- **E2E Tests** - For critical user flows (framework chosen per language)

### TDD Workflow (MANDATORY)
1. Write test first (RED)
2. Run test - it should FAIL
3. Write minimal implementation (GREEN)
4. Run test - it should PASS
5. Refactor (IMPROVE)
6. Verify coverage (80%+)

### Troubleshooting Guidelines
- Use **tdd-guide** agent
- Check test isolation
- Verify mocks are correct
- **Fix implementation, not tests (unless tests are wrong)**

## Security Rules

### Mandatory Security Checks (Pre-Commit)
- No hardcoded secrets (API keys, passwords, tokens)
- Validate all user inputs
- Use parameterized queries for SQL injection prevention
- Sanitize HTML to prevent XSS attacks
- Enable CSRF protection
- Verify authentication and authorization
- Implement rate limiting on all endpoints
- Ensure error messages don't leak sensitive data

### Secret Management Guidelines
- **NEVER hardcode secrets in source code**
- **ALWAYS use environment variables or a secret manager**
- Validate required secrets are present at startup
- Rotate any secrets that may have been exposed

### Security Response Protocol (When Issues Found)
1. **STOP immediately**
2. Use security-reviewer agent
3. Fix CRITICAL issues before continuing
4. Rotate any exposed secrets
5. Review entire codebase for similar issues

## Performance Optimization

### Model Selection
- Use Haiku for lightweight agents with frequent invocation, pair programming, code generation, and worker agents
- Use Sonnet for main development work, orchestrating multi-agent workflows, and complex coding tasks
- Use Opus for complex architectural decisions, maximum reasoning requirements, and research tasks

### Context Window Management
- Avoid using the last 20% of the context window for large-scale refactoring, multi-file feature implementation, and debugging complex interactions
- Reserve lower context sensitivity tasks for single-file edits, utility creation, documentation updates, and simple bug fixes

### Extended Thinking
- Extended thinking reserves up to 31,999 tokens for internal reasoning by default
- Control it via the toggle Option+T (macOS) or Alt+T (Windows/Linux)
- Set `alwaysThinkingEnabled` in settings.json or use the budget cap `MAX_THINKING_TOKENS`
- For complex reasoning tasks: enable extended thinking, use Plan Mode, apply multiple critique rounds, and leverage split role sub-agents

### Build Troubleshooting
- Use the **build-error-resolver** agent, analyze error messages, fix incrementally, and verify after each fix

## Design Patterns

### Skeleton Projects
- **Search first**: "Search for battle-tested skeleton projects"
- **Use parallel evaluation**: Conduct security assessment, extensibility analysis, relevance scoring, and implementation planning using parallel agents
- **Clone and iterate**: Clone the best match as a foundation and iterate within the proven structure

### Repository Pattern
- **Define standard operations**: Implement findAll, findById, create, update, and delete methods
- **Encapsulate storage details**: Let concrete implementations handle database, API, file, or other storage mechanisms
- **Depend on abstractions**: Business logic should rely on the abstract interface rather than specific storage mechanisms
- **Enable flexibility**: This approach allows easy swapping of data sources and simplifies testing through mocks

### API Response Format
- **Include status indicator**: Always provide a success or status field
- **Include data payload**: The data field should be nullable when errors occur
- **Provide error messaging**: Error message field should be nullable on successful responses
- **Add pagination metadata**: Include total count, page number, and limit for paginated responses

## Coding Style

- Follow the existing code style in the project
- Match naming conventions used in the codebase
- Keep functions small and focused
- Write self-documenting code with clear variable names
- Add comments only when necessary to explain "why", not "what"

## Commit & Push
- Write detailed commit messages
- Follow conventional commits format
- Reference related issues in commit messages
