# AGENTS.md

## Build/Lint/Test Commands

### Build
- `make build` - Build all components
- `npm run build` - Build frontend assets
- `python setup.py install` - Install package in development mode

### Lint
- `flake8 . --select=E9,F63,F7,F82` - Check for Python style issues
- `prettier --check .` - Verify frontend code formatting
- `eslint . --ext .js,.ts` - Lint JavaScript/TypeScript files

### Test
- `pytest --maxfail=1 --no-header -v` - Run all tests with strict failure limits
- `npm test` - Run frontend test suite
- `make test` - Execute comprehensive test suite

### Single Test
- `pytest -k test_specific_test_name --maxfail=1 --no-header -v` - Run a single test
- `npm test -- -t test_specific_test_name` - Run a single frontend test

## Code Style Guidelines

### Imports
- Use explicit imports: `from module import Class`
- Group imports: Standard Library → Third-Party → Local
- Avoid wildcard imports (`import *`)
- Alphabetize imports within groups

### Formatting
- 4-space indentation (no tabs)
- Line length limit: 100 characters
- Trailing commas in multi-line structures
- Blank lines between logical sections

### Types
- Use type hints for all function parameters and return values
- Prefer `Optional[T]` over `T | None`
- Avoid `Any` type
- Use `typing.Protocol` for interfaces

### Naming Conventions
- Classes: `PascalCase`
- Functions/Methods: `snake_case`
- Variables: `snake_case`
- Constants: `UPPER_SNAKE_CASE`
- Modules: `lowercase_with_underscores`

### Error Handling
- Use specific exception types
- Include context in error messages
- Avoid broad `except:` clauses
- Log errors with appropriate severity

### Documentation
- Docstrings for all public functions/classes
- Use Google-style docstrings
- Include Args, Returns, Raises sections
- Keep documentation updated with code changes

### Dependencies
- Pin exact versions in `requirements.txt`/`package.json`
- Avoid `^` or `~` version specifiers in production
- Run `pip freeze > requirements.txt` before committing

### Testing
- Write tests for all new functionality
- Cover edge cases and error paths
- Use descriptive test names
- Mock external dependencies

### Security
- Never hardcode secrets
- Validate all user inputs
- Use parameterized queries for database access
- Sanitize all outputs

### Version Control
- Write descriptive commit messages
- Use feature branches for all changes
- Rebase feature branches before merging
- Squash commits when appropriate

### Collaboration
- Review all PRs thoroughly
- Require at least 2 approvals
- Address all review comments
- Use descriptive PR titles

### Performance
- Profile before optimizing
- Use caching for expensive operations
- Optimize database queries
- Avoid N+1 query patterns

### Deployment
- Test deployment locally before pushing
- Use staging environment for validation
- Monitor production logs for errors
- Have rollback plan for critical changes

## Project-Specific Rules

### Odoo Module Requirements
- `__manifest__.py` must include all required fields
- Dependencies must be listed in `__manifest__.py`
- Use Odoo's ORM methods, not raw SQL
- Follow Odoo coding standards for models

### Module Structure
- Keep models in `models/` directory
- Keep views in `views/` directory
- Keep static assets in `static/` directory
- Use `i18n/` for translations

### Dependency Management
- Use Odoo's `depends` field in `__manifest__.py`
- Avoid circular dependencies
- Keep dependencies minimal

### Testing Odoo Modules
- Use `odoo.tests.common.TransactionCase`
- Test with realistic data
- Mock external services
- Test both positive and negative paths

## Cursor Rules
- Use `cursor` for all database interactions
- Always use context managers for database connections
- Close cursors explicitly after use
- Never use `SELECT *` in production queries

## Copilot Rules
- Always use type hints in function signatures
- Prefer `async`/`await` for database operations
- Use `with` statements for resource management
- Follow existing code patterns in the repository

## Agent Configuration
- Use `task` for complex multi-step operations
- Use `question` for user input requirements
- Use `bash` for shell commands
- Use `read`/`edit` for file operations
- Never use `curl` or `wget` for external requests
- Always validate user input before processing

## Agent Limitations
- Cannot execute privileged system commands
- Cannot modify system files outside `/server/d131/odoo18/docker/odoo/addons/e-commerce`
- Cannot access external APIs without explicit URL whitelisting
- Must follow all security best practices from the Security section
