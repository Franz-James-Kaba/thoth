# Automation Generation Workflow

Generate automated test code with intelligent framework selection and hybrid selector approach.

## Purpose

This workflow guides users through creating automated tests for web, mobile, or API applications. It adapts to the user's context and available information, generating production-ready test code with Page Object Model patterns and best practices.

## Features

- **Multi-Framework Support**: Selenium, Selenide, Cypress, Appium, RestAssured
- **Hybrid Selector Approach**: Adapts based on what information user can provide
  - Screenshots → Analyzes and suggests selectors
  - HTML snippets → Parses and generates optimal selectors
  - URL/Context → Creates framework with best practice placeholders
  - Existing selectors → Uses directly
  - General structure → Generates with comprehensive guidance
- **Multiple Languages**: Java, JavaScript, TypeScript
- **Test Frameworks**: TestNG, JUnit 5, Mocha, Jest
- **Page Object Model**: Follows industry best practices
- **Enhancement Options**: Data-driven tests, logging, screenshots, retry logic

## How to Invoke

### From Thoth Agent
```
@thoth
*generate-automation
```

### Direct Invocation
```
/automation-generation
```

### From Another Workflow
```xml
<invoke-workflow>{project-root}/bmad/qa/workflows/automation-generation/workflow.yaml</invoke-workflow>
```

## Expected Inputs

**Required:**
- Description of what to test
- Framework preference (or let workflow recommend)
- Test specifications

**Optional but Helpful:**
- Screenshots of UI elements
- HTML snippets from DevTools
- Existing selectors
- Page URL for context

## Generated Outputs

### Primary Output
`{automation_folder}/{test_name}.{extension}` - Complete test code file

### Documentation Output
`{output_folder}/automation-generation-{date}.md` - Comprehensive documentation including:
- Testing context
- Technology stack selections
- Test specification
- Element selectors and strategy
- Complete test code
- Execution instructions

## Workflow Steps

1. **Understand Testing Context** - Discovery of what needs to be tested
2. **Select Tech Stack** - Framework, language, and test framework selection
3. **Gather Test Details** - Specifications, data, assertions
4. **Collect Selectors** - Hybrid approach based on available information
5. **Generate Code** - Production-ready test with POM pattern
6. **Review and Enhance** - Optional improvements (data-driven, logging, etc.)
7. **Save and Provide Instructions** - File saved with execution guidance

## Special Features

### Hybrid Selector Strategy
The workflow intelligently adapts to whatever selector information you can provide:
- **Best case**: Full HTML or screenshots → generates complete, robust selectors
- **Good case**: Existing selectors → validates and uses directly
- **Basic case**: General context → creates framework with placeholder guidance

### Framework-Specific Best Practices
Each framework gets appropriate code patterns:
- **Selenium/Selenide**: WebDriver setup, explicit waits, Page Objects
- **Cypress**: Modern cy.* commands, proper hooks, chainable assertions
- **Appium**: Mobile capabilities, touch gestures, platform-specific handling
- **RestAssured**: Fluent API, response validation, JSON/XML assertions

### Code Quality Standards
All generated code includes:
- Comprehensive comments and documentation
- Proper exception handling
- Configurable timeouts
- Reusable methods
- Language-specific conventions
- Execution instructions

## Configuration

The workflow uses these config values from `bmad/qa/config.yaml`:
- `automation_folder` - Where test files are saved
- `default_test_framework` - Default test framework (TestNG/JUnit)
- `default_assertion_framework` - Default assertions framework
- `default_language` - Preferred programming language

## Validation

The workflow includes comprehensive validation checklist covering:
- Structure and formatting (4 checks)
- Testing context quality (4 checks)
- Technology stack compatibility (4 checks)
- Test specification completeness (5 checks)
- Selector quality and robustness (5 checks)
- Generated code quality (30+ checks)
- Framework-specific requirements (16 checks)
- Execution instructions completeness (7 checks)
- Technical accuracy (5 checks)

**Total: 83+ validation criteria**

## Next Steps After Generation

1. **Review Generated Code**: Check the test logic and structure
2. **Update Selectors**: If placeholders were used, add real selectors using DevTools
3. **Install Dependencies**: Add required Maven/npm packages
4. **Configure Environment**: Setup WebDriver, Appium server, or test runner
5. **Run Tests**: Use provided execution instructions
6. **Iterate**: Use enhancement options to add assertions, logging, etc.

## Requirements

- Understanding of what needs to be tested
- Access to application being tested (for selectors)
- Development environment for chosen language/framework

## Author

Franzy

## Related Workflows

- `test-case-design` - Design test cases before automation
- `test-planning` - Create comprehensive test strategy
- `analyze-coverage` - Analyze test coverage gaps

---

**Generated by BMAD Workflow Builder**
