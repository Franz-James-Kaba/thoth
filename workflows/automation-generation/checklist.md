# Automation Generation Workflow - Validation Checklist

## Structure

- [ ] Document contains all required sections (Context, Stack, Specification, Selectors, Code, Instructions)
- [ ] No placeholder variables remain (all {{variables}} replaced)
- [ ] Code block uses correct file extension syntax highlighting
- [ ] Proper markdown formatting throughout

## Testing Context Quality

- [ ] Clear description of what is being tested (feature/flow/component)
- [ ] Application type identified (web/mobile/API/desktop)
- [ ] Testing scope defined (e2e/integration/unit)
- [ ] Any existing test patterns or structure noted

## Technology Stack Selection

- [ ] Automation framework selected and matches application type
- [ ] Programming language is compatible with chosen framework
- [ ] Test framework is compatible with programming language
- [ ] All selections are technically valid together

## Test Specification Completeness

- [ ] Test name is descriptive and follows naming conventions
- [ ] Test description clearly states what is being verified
- [ ] Required test data is identified
- [ ] Expected outcomes and assertions are specified
- [ ] Preconditions and setup requirements are documented

## Element Selectors Quality

- [ ] Selector strategy is documented (screenshots/HTML/context/existing/general)
- [ ] Selectors follow priority hierarchy (data-testid > id > name > CSS > XPath)
- [ ] Selectors are specific and unlikely to break with UI changes
- [ ] If placeholders used, clear guidance provided for finding real selectors
- [ ] Best practices for selector robustness are documented

## Generated Code Quality

### Code Structure
- [ ] Follows Page Object Model pattern (or appropriate pattern for framework)
- [ ] Proper package/import statements included
- [ ] Class and method names are descriptive and follow language conventions
- [ ] Code is properly organized (Page classes separate from Test classes for Selenium/Selenide)

### Framework-Specific Requirements

**For Selenium/Selenide:**
- [ ] WebDriver setup and teardown properly configured
- [ ] Proper use of waits (explicit waits, not Thread.sleep)
- [ ] Element locators defined in Page Object
- [ ] Test methods use Page Object methods

**For Cypress:**
- [ ] Proper describe/it structure
- [ ] Hooks (before/beforeEach/after) used appropriately
- [ ] Cypress commands used correctly (cy.get, cy.visit, etc.)
- [ ] Assertions use Cypress/Chai syntax

**For Appium:**
- [ ] Mobile capabilities configured correctly
- [ ] Platform-specific considerations addressed (iOS/Android)
- [ ] Touch actions and mobile gestures implemented properly
- [ ] Screen/Page Objects follow mobile patterns

**For RestAssured:**
- [ ] Request specification properly configured
- [ ] HTTP methods used correctly (GET/POST/PUT/DELETE)
- [ ] Response validation includes status code, body, headers
- [ ] JSON/XML path assertions are accurate

### Code Quality Standards
- [ ] Comprehensive comments explain logic and purpose
- [ ] Exception handling included where appropriate
- [ ] Configurable timeouts and waits (not hardcoded)
- [ ] Reusable methods for common actions
- [ ] Proper use of test framework annotations (@Test, @BeforeMethod, etc.)
- [ ] Assertions are clear and specific
- [ ] Logging statements at key points (if logging was requested)

### Enhancements (if requested)
- [ ] Additional assertions added for intermediate verification
- [ ] Edge case handling implemented
- [ ] Data-driven approach with proper parameterization
- [ ] Screenshot capture on failure configured
- [ ] Performance measurements included
- [ ] Retry logic implemented if requested

## Execution Instructions Completeness

- [ ] Clear command-line execution instructions provided
- [ ] IDE execution steps included
- [ ] Framework-specific run commands are accurate
- [ ] Required dependencies listed (WebDriver, npm packages, Maven dependencies)
- [ ] Configuration requirements documented
- [ ] Environment setup steps provided
- [ ] Test data file requirements specified (if applicable)

## Selector Implementation

- [ ] All selectors used in code match the selector strategy documented
- [ ] Placeholder selectors (if any) have clear TODO comments
- [ ] Selector best practices guide included for placeholder scenarios
- [ ] DevTools inspection instructions provided (if needed)

## Technical Accuracy

- [ ] Syntax is correct for the chosen language
- [ ] Framework APIs used correctly
- [ ] Test framework annotations and structure follow conventions
- [ ] No deprecated methods or anti-patterns used
- [ ] Code would compile/run without syntax errors

## Completeness

- [ ] Test covers the specified user flow completely
- [ ] All assertions from specification are implemented
- [ ] Setup and teardown are properly handled
- [ ] Test is ready to run (or clear next steps provided if placeholders exist)
- [ ] Dependencies and setup requirements fully documented

## Final Validation

### Critical Issues (must be empty)
List any issues that prevent the test from being usable:
-

### Minor Issues (should address before using)
List any improvements that would enhance test quality:
-

### Recommendations (optional enhancements)
List any suggestions for future improvements:
-

---

**Validation completed by:** _____________
**Date:** _____________
**Status:** ☐ Pass ☐ Pass with minor issues ☐ Fail - needs revision
