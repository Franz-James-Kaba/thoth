# Automation Generation Workflow Instructions

<critical>The workflow execution engine is governed by: {project-root}/bmad/core/tasks/workflow.xml</critical>
<critical>You MUST have already loaded and processed: {project-root}/bmad/qa/workflows/automation-generation/workflow.yaml</critical>
<critical>Communicate in {communication_language} throughout the workflow</critical>

<workflow>

<step n="1" goal="Understand testing context and requirements">
<action>Engage in discovery to understand what the user wants to test:

Ask open-ended questions to explore:
- What are they testing? (web application, mobile app, API endpoint, desktop application)
- What specific feature or user flow needs automation?
- Is this a new test suite or addition to existing tests?
- What is the critical path or happy path scenario?
- Are there any existing tests or patterns they're following?

Listen for clues about:
- Application type and technology stack
- Testing scope (end-to-end, integration, unit)
- Complexity of the user flow
- Any specific testing challenges or concerns

Adapt your depth based on their responses:
- If experienced QA: Focus on technical specifics
- If new to automation: Guide them through what's needed
- If they have existing tests: Understand their current patterns

The goal is to build a clear picture of what needs to be automated.
</action>

<template-output>testing_context</template-output>
</step>

<step n="2" goal="Select automation framework and technology stack">
<critical>This step uses prescriptive choices for technical decisions</critical>

<ask>Based on what you're testing, which automation framework would you like to use?

**For Web Testing:**
1. Selenium - Industry standard, cross-browser support, Java/Python
2. Selenide - Concise Selenium wrapper, built-in waits, Java
3. Cypress - Modern JavaScript framework, fast, developer-friendly

**For Mobile Testing:**
4. Appium - Cross-platform mobile automation, iOS/Android

**For API Testing:**
5. RestAssured - Java-based REST API testing, fluent syntax

Enter the number (1-5) or framework name:
</ask>

<action>Store the framework selection as {{automation_framework}}</action>

<ask>Which programming language?

**For Selenium/Selenide/RestAssured:**
1. Java

**For Cypress:**
2. JavaScript
3. TypeScript

**For Appium:**
4. Java
5. JavaScript

Select based on your framework choice:
</ask>

<action>Store language as {{test_language}}</action>
<action>Determine file extension: Java → .java, JavaScript → .js, TypeScript → .ts</action>
<action>Store as {{file_extension}}</action>

<ask>Which test framework?

**For Java:**
1. TestNG (recommended for complex test suites)
2. JUnit 5 (modern, flexible)

**For JavaScript/TypeScript:**
3. Mocha
4. Jest

Select based on your language:
</ask>

<action>Store test framework as {{test_framework}}</action>

<template-output>tech_stack</template-output>
</step>

<step n="3" goal="Gather test details and specifications">
<action>Collect specific test information:

Guide the user to provide:
- Test name (will be used for class/file name)
- Test description (what does this test verify?)
- Test data requirements (login credentials, test inputs, etc.)
- Expected outcomes and assertions
- Any preconditions or setup needed

Help them think through:
- What is the starting state?
- What actions need to be performed?
- What should be verified at each step?
- What is the expected end state?

Be specific about:
- Input values needed
- Expected output or behavior
- Success criteria

Format this as a clear test specification.
</action>

<template-output>test_specification</template-output>
</step>

<step n="4" goal="Collect selector information using hybrid approach">
<critical>This is the hybrid selector approach - adapt based on what user can provide</critical>

<action>Explain the selector gathering process:

"To generate accurate test automation, I need to identify the UI elements (buttons, fields, etc.).
You can provide information in several ways, and I'll adapt my approach accordingly."
</action>

<ask>What information can you provide about the UI elements?

1. **Screenshots** - I'll analyze and suggest selectors
2. **HTML snippets** - Copy/paste from browser DevTools
3. **Page URL + context** - I'll generate framework with best practices
4. **Existing selectors** - You already have the locators
5. **General page structure** - I'll create framework with placeholder selectors

What works best for you? (1-5)
</ask>

<action>Based on their choice, adapt the selector generation approach:</action>

<check if="option 1 - Screenshots">
  <action>Request screenshots of the page or feature being tested</action>
  <action>Analyze visible elements (buttons, inputs, links, etc.)</action>
  <action>Suggest robust selectors using this priority:
    1. data-testid or data-test-id attributes (most reliable)
    2. id attributes (if unique and stable)
    3. name attributes (for form fields)
    4. CSS selectors (class-based, specific)
    5. XPath (as last resort, with explanation of brittleness)
  </action>
  <action>Provide selector recommendations with confidence levels</action>
</check>

<check if="option 2 - HTML snippets">
  <action>Request HTML for key elements from browser DevTools</action>
  <action>Parse HTML and extract element attributes</action>
  <action>Generate optimal selectors using priority hierarchy:
    - data-* attributes first
    - id if present and meaningful
    - combination of tag + attributes for stability
  </action>
  <action>Create complete, ready-to-use selectors</action>
</check>

<check if="option 3 - URL + context">
  <action>Note that without specific selectors, you'll generate a framework with best practices</action>
  <action>Create Page Object Model with placeholder selectors</action>
  <action>Add detailed comments explaining where to find selectors using DevTools</action>
  <action>Include selector strategy guide in comments</action>
  <action>Provide TODO markers for elements that need selectors</action>
</check>

<check if="option 4 - Existing selectors">
  <action>Request the element locators they already have</action>
  <action>Use them directly in the generated code</action>
  <action>Validate selector syntax for chosen framework</action>
</check>

<check if="option 5 - General structure">
  <action>Create high-level test structure without specific selectors</action>
  <action>Use descriptive placeholder names (loginButton, usernameField, etc.)</action>
  <action>Add comprehensive inline guide for adding selectors later</action>
  <action>Include best practices for selector strategy</action>
</check>

<action>For all options, provide guidance on robust selector strategies:
- Avoid fragile selectors (absolute XPath, index-based, brittle CSS)
- Prefer semantic attributes (data-testid, aria-label, role)
- Use relative selectors over absolute
- Recommend adding test IDs to application if possible
</action>

<template-output>element_selectors</template-output>
</step>

<step n="5" goal="Generate test automation code">
<action>Generate complete test code following best practices for the selected framework and language.

**Code Structure (adapt based on framework):**

**For Selenium/Selenide (Java):**
- Page Object Model pattern
- Separate Page class with element locators
- Test class with test methods
- Proper annotations (@Test, @BeforeMethod, @AfterMethod)
- WebDriver setup and teardown
- Explicit waits and robust element interactions
- Assertions using test framework (TestNG/JUnit)

**For Cypress (JavaScript/TypeScript):**
- Page Object or custom commands
- describe/it test structure
- Proper hooks (before, beforeEach, after)
- Cypress commands (cy.get, cy.visit, etc.)
- Assertions using chai/cypress
- Good command chaining practices

**For Appium (Java/JavaScript):**
- Page Object Model for mobile screens
- Mobile-specific capabilities
- Touch actions and gestures
- Platform-specific selectors (iOS/Android)
- Proper driver setup for mobile

**For RestAssured (Java):**
- Request specification
- Response validation
- JSON/XML path assertions
- Status code checks
- Header validations
- Request/response logging

**Code Quality Standards:**
1. Clear, descriptive method and variable names
2. Comprehensive comments explaining logic
3. Proper exception handling
4. Configurable timeouts and waits
5. Reusable methods for common actions
6. Data-driven approach where applicable
7. Logging for debugging
8. Follow language conventions (camelCase for Java, etc.)

**Include in generated code:**
- Package/import statements
- Class-level documentation
- Method-level documentation
- Inline comments for complex logic
- TODO comments if selectors are placeholders
- Example of how to run the test

Adapt code complexity to user's experience level based on earlier conversation.
</action>

<template-output>test_code</template-output>
</step>

<step n="6" goal="Review and enhance the generated test">
<action>Present the generated test code to the user</action>

<ask>Review the generated test code. Would you like to enhance it with any of the following?

1. Add more assertions or verification points
2. Add edge case handling
3. Make it data-driven (parameterized test)
4. Add more detailed logging
5. Add screenshot capture on failure
6. Include performance measurements
7. Add retry logic for flaky tests
8. No changes needed - looks good

Select option(s) (comma-separated for multiple) or 8 to continue:
</ask>

<check if="user wants enhancements">
  <action>Based on selected enhancements, modify the test code:

  - More assertions: Add intermediate verification points throughout the flow
  - Edge cases: Add try-catch blocks, null checks, boundary validations
  - Data-driven: Convert to parameterized test with DataProvider/ParameterizedTest
  - Logging: Add detailed log statements at key steps
  - Screenshots: Add screenshot capture in catch blocks or after assertions
  - Performance: Add timing measurements and performance assertions
  - Retry: Add retry annotations or retry logic
  </action>

  <action>Regenerate the enhanced test code</action>
  <template-output>enhanced_test_code</template-output>
</check>

<check if="no enhancements needed">
  <action>Use the original generated test code as final version</action>
</check>

<template-output>final_test_code</template-output>
</step>

<step n="7" goal="Save test file and provide execution guidance">
<action>Determine the complete file path:
- Base path: {automation_folder}
- File name: {{test_name}}.{{file_extension}}
- Create subdirectories if needed (e.g., pages/, tests/)
</action>

<action>Save the test code to the determined file path</action>

<action>Generate execution instructions based on framework:

**For TestNG:**
```
Run via IDE: Right-click test class → Run
Run via Maven: mvn test -Dtest={{test_name}}
Run via CLI: java -cp ... org.testng.TestNG testng.xml
```

**For JUnit 5:**
```
Run via IDE: Right-click test method → Run
Run via Maven: mvn test -Dtest={{test_name}}
Run via Gradle: gradle test --tests {{test_name}}
```

**For Cypress:**
```
Run specific test: npx cypress run --spec "cypress/e2e/{{test_name}}.{{file_extension}}"
Run in UI mode: npx cypress open
```

**For Appium:**
```
Ensure Appium server is running: appium
Run test: [same as TestNG/JUnit depending on language]
```

**For RestAssured:**
```
Run via Maven: mvn test -Dtest={{test_name}}
Run via IDE: Right-click and run
```
</action>

<action>Provide setup requirements if any:
- WebDriver setup (ChromeDriver, GeckoDriver, etc.)
- Dependencies to add (Maven/npm)
- Configuration files needed
- Environment variables
- Test data files
</action>

<action>Address {user_name} and summarize in {communication_language}:

"✅ Test automation generated successfully!

**File saved:** {automation_folder}/{{test_name}}.{{file_extension}}

**Framework:** {{automation_framework}}
**Language:** {{test_language}}
**Test Framework:** {{test_framework}}

**Next steps:**
1. Review the generated code
2. Update any placeholder selectors (if applicable)
3. Configure your test environment
4. Run the test using the instructions above

The test follows Page Object Model best practices and includes comprehensive comments to guide you."
</action>

<template-output>execution_instructions</template-output>
</step>

</workflow>
