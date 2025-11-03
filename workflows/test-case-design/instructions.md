# Test Case Design Workflow Instructions

<critical>The workflow execution engine is governed by: {project-root}/bmad/core/tasks/workflow.xml</critical>
<critical>You MUST have already loaded and processed: {project-root}/bmad/qa/workflows/test-case-design/workflow.yaml</critical>
<critical>Communicate in {communication_language} throughout the workflow</critical>

<workflow>

<step n="1" goal="Understand the feature or functionality to test">
<action>Engage with the user to understand what needs testing:

Explore:
- What feature or functionality are we designing test cases for?
- What is the business purpose and user value?
- Are there existing requirements or user stories?
- What is the scope (specific feature vs entire module)?
- Are there any known edge cases or problem areas?

Guide them to articulate:
- The main user flows and scenarios
- Expected inputs and outputs
- Success criteria and failure conditions
- Dependencies and integrations

Adapt depth based on their familiarity with the feature.
</action>

<template-output>feature_overview</template-output>
</step>

<step n="2" goal="Identify test scenario categories">
<action>Guide user to identify different types of test scenarios needed:

Work through these categories systematically:

**Functional Testing:**
- Happy path scenarios (expected user flow)
- Alternative paths (different valid routes)
- Negative scenarios (invalid inputs, errors)

**Boundary Testing:**
- Minimum valid values
- Maximum valid values
- Just below/above boundaries

**Integration Points:**
- API integrations
- Database interactions
- Third-party services
- Cross-module dependencies

**User Experience:**
- Usability scenarios
- Accessibility considerations
- Performance-sensitive operations

**Data Scenarios:**
- Different data types
- Data validation rules
- Special characters and edge cases

Help them prioritize which categories are most relevant for this feature.
</action>

<template-output>test_categories</template-output>
</step>

<step n="3" goal="Design positive test cases (happy path)">
<action>Create detailed test cases for successful scenarios:

For each positive scenario, design test cases with:
- **Test Case ID**: Unique identifier (TC-001, TC-002, etc.)
- **Title**: Clear, descriptive name
- **Description**: What this test verifies
- **Preconditions**: Setup required before test
- **Test Steps**: Numbered, specific actions
- **Test Data**: Specific inputs to use
- **Expected Results**: What should happen at each step
- **Postconditions**: System state after test
- **Priority**: Critical/High/Medium/Low

Use clear, unambiguous language.
Each step should be actionable and verifiable.
</action>

<template-output>positive_test_cases</template-output>
</step>

<step n="4" goal="Design negative test cases">
<action>Create test cases for error conditions and invalid inputs:

For each negative scenario:
- Invalid inputs (wrong format, type, range)
- Missing required data
- Unauthorized access attempts
- System errors and exceptions
- Network failures or timeouts

For each negative test case, specify:
- What invalid action or input is tested
- Expected error message or behavior
- How system should gracefully handle the error
- Recovery steps if applicable

Ensure error messages are user-friendly and actionable.
</action>

<template-output>negative_test_cases</template-output>
</step>

<step n="5" goal="Design boundary and edge case tests">
<action>Identify and document boundary value tests and edge cases:

**Boundary Values:**
- Test at exact boundaries (min, max values)
- Test just below and above boundaries
- Empty/null values
- Maximum length strings
- Special characters

**Edge Cases:**
- Concurrent operations
- Race conditions
- Large data volumes
- System under load
- Unusual but valid inputs

For each boundary/edge case:
- Specify the boundary or edge condition
- Expected behavior
- Why this case matters (risk it mitigates)
</action>

<template-output>boundary_edge_cases</template-output>
</step>

<step n="6" goal="Design integration and dependency tests" optional="true">
<action>If the feature has integrations, design test cases for:

**API Integration Tests:**
- Request/response validation
- Error handling from external services
- Timeout scenarios
- Authentication/authorization

**Database Tests:**
- Data persistence
- Transaction handling
- Rollback scenarios
- Data integrity

**Third-party Services:**
- Service availability
- Fallback behavior
- Data synchronization

Document the integration points and test coverage for each.
</action>

<template-output>integration_tests</template-output>
</step>

<step n="7" goal="Add test case metadata and traceability">
<action>Enhance test cases with additional information:

For the complete test suite, add:
- **Traceability**: Link to requirements or user stories
- **Test Environment**: Where tests should run
- **Test Data Requirements**: Data setup needed
- **Execution Order**: Dependencies between test cases
- **Automation Potential**: Which tests are candidates for automation
- **Test Execution Time**: Estimated duration
- **Risk Level**: Impact if this fails in production

Organize test cases logically by priority and dependency.
</action>

<template-output>test_metadata</template-output>
</step>

<step n="8" goal="Review and refine test coverage">
<action>Review the complete test case suite with user:

Present summary:
- Total test cases designed
- Coverage by category (functional, boundary, integration)
- Priority distribution (critical vs. low)
- Automation candidates

Ask user:
- Are there any scenarios we missed?
- Do any test cases need more detail?
- Should we add specific edge cases?
- Is the priority distribution appropriate?

Refine based on feedback.
</action>

<ask>Would you like to add more test cases or refine existing ones? [yes/no]</ask>

<check if="user wants refinement">
  <action>Iterate on specific test cases based on feedback</action>
  <action>Update test cases with additional details or scenarios</action>
</check>

<template-output>refined_test_cases</template-output>
</step>

<step n="9" goal="Save test case document">
<action>Generate the complete test case document with all sections:
- Feature overview
- Test categories and coverage
- Positive test cases
- Negative test cases
- Boundary and edge cases
- Integration tests
- Metadata and traceability
- Summary and execution guidance
</action>

<action>Save to: {test_cases_folder}/{feature_name}-test-cases.md</action>

<action>Address {user_name} in {communication_language}:

"✅ Test case design complete!

**Test Suite Summary:**
- Total Test Cases: {{total_test_cases}}
- Critical/High Priority: {{high_priority_count}}
- Automation Candidates: {{automation_count}}

**File saved:** {test_cases_folder}/{feature_name}-test-cases.md

**Next steps:**
1. Review test cases with team
2. Identify automation candidates
3. Execute manual tests
4. Use *generate-automation for automated tests

The test cases are comprehensive, traceable, and ready for execution."
</action>

<template-output>completion_summary</template-output>
</step>

</workflow>
