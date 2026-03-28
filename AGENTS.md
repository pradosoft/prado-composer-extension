# PRADO Composer Extension Agent Guidelines

## Build, Lint, and Test Commands

### Running Tests
- **Unit Tests**: `composer unittest` - runs all unit tests
- **Functional Tests**: `composer functionaltest` - runs all functional tests  
- **Single Test File**: `vendor/bin/phpunit tests/unit/Path/To/TestFile.php`
- **Single Test Method**: `vendor/bin/phpunit tests/unit/Path/To/TestFile.php::testMethodName`

### Linting and Code Analysis
- **PHPStan Analysis**: `vendor/bin/phpstan analyse src/ --memory-limit=512M`
- **PHP CS Fixer**: `vendor/bin/php-cs-fixer fix --dry-run` (check)
- **PHP CS Fixer (Fix)**: `vendor/bin/php-cs-fixer fix` (apply fixes)

### Build Commands
- **Generate Documentation**: `composer gendoc` - generates API documentation
- **Install Dependencies**: `composer install` - installs all dependencies

## Code Style Guidelines
- "if" has a statement block after.
- Use php-cs-fixer to correct code styles.

### PHP Coding Standards
- Follow PSR-4 autoloading standard
- All PHP files must begin with `<?php` tag (short open tags not allowed)
- Use 1 tab for indentations (no spaces)
- All class names must be in PascalCase
- All method names must be in camelCase
- All variable names must be in camelCase
- Constants must be in UPPER_CASE
- Use explicit return types for methods when possible
- All class properties must be declared with visibility modifiers (public, protected, private)

### Naming Conventions
- Class names: `PascalCase` (e.g., `MyExampleClass`)
- Method names: `camelCase` (e.g., `getComponent`)
- Variables: `camelCase` (e.g., `$componentName`)
- Constants: `UPPER_CASE` (e.g., `MAX_RETRY_COUNT`)
- Namespace: `PradoComposerExtension\{Module}` (e.g., `PradoComposerExtension\Pages`)

### Documentation Standards
- All public methods must have PHPDoc comments with:
  - `@param` for parameters
  - `@return` for return values  
  - `@throws` for exceptions
  - `@since` to indicate version
- Files must have a docblock at the top with class description
- Inline comments should be in English and start with `//`

### Error Handling
- Use try/catch blocks for operations that can fail
- Throw appropriate exceptions (`Exception`, `InvalidArgumentException`, etc.)
- Return false or null for methods that are designed to fail gracefully
- All methods should handle edge cases and validate input parameters
- PRADO Exceptions use errorCodes specified in framework/Exceptions/messages/messages.txt; the master error Code file in English. messages.txt is purely for user information display only.

### Imports and Includes
- Use PSR-4 autoloading - no manual includes required
- All framework classes are accessed via namespace prefixes
- Third-party libraries are loaded via Composer
- Use proper `use` statements for namespaces at the top of PHP files

### Framework Specific Guidelines
- You are a professional Software Engineer working on a PRADO 4 Plugin Module.
- All components inherit from `TComponent` base class
- `TComponent` has features for dynamic methods (__call, __callStatic), dynamic properties (__get, __set, __isset, __unset), __clone, __sleep, __wakeup, and _getZappableSleepProps
- Behaviors can be attached to any `TComponent` to alter its behavior and functionality.
- Use the event-driven programming model with events; like `onLoad`, `onInit`, `onPreRender`
- Use dynamic methods ('dy-' events) to call attached and active `TBehavior` classes; like 'dyAlterCodePath', 'dyClone', and 'dyValidate'
- Methods with prefix 'fx' are global events that may or may not be automatically registered depending on getAutoGlobalListen(); like 'fxAttachClassBehavior'
- Follow the component lifecycle: init → load → preRender → render → unload
- Data components should support `TActiveRecord` pattern
- All UI controls should have proper template support and state management
- A full check consists of the 4 checks (in order): php compile, php-cs-fixer, phpstan, composer unittest (must all pass successfully)
- A full check must be done for code to be ready to commit.
- All changes must be backward compatible.
- The current version is 1.0.1. git HEAD is working on version 1.0.2.
- Use the next release version when adding new files, methods, or classes comments "@since"

## Testing Guidelines
- The testing platform is "phpunit"
- All new code must include unit tests
- Test both typical and edge cases
- Test error conditions and exception handling
- Use mock objects where appropriate
- Functional tests should verify complete user workflows
- Tests should be isolated from each other (no shared state)

## Development Environment
- PHP 8.1 or higher required
- PHP extensions: ctype, dom, json, pcre, spl (required)
- Optional extensions for additional features: apcu, mbstring, openssl, pdo, soap, xsl, zlib
- Composer for dependency management
- Required developer dependencies for code checking: phpunit/phpunit, phpstan/phpstan, friendsofphp/php-cs-fixer
- Presume that the dependencies are installed, unless running them fails

## Cursor/Copilot Instructions
No specific Cursor or Copilot rules currently defined for this project.

# PRADO Framework Agent Safeguards --  
Between the next brackets, it is required without exception:
{
- NEVER execute the following "git" commands without asking the developer for approval first: clone, checkout, mv, restore, rm, branch, add, commit, merge, rebase, reset, pull, push, fetch
- NEVER execute "rm" commands on any paths without asking the developer for approval first
}

# File References
- The working/planning directory for Coding Agents is "agents/working/"; temporary files go in this directory
- To Search the PHP language and libraries, use url: "https://www.php.net/search.php#gsc.tab=0&gsc.sort=&gsc.q=<replace with query string>"
- To look up inherent PHP functions, use url: "https://www.php.net/manual/en/function.<replace with PHP function>.php"