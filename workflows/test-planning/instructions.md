# Test Planning Workflow Instructions

<critical>The workflow execution engine is governed by: {project-root}/bmad/core/tasks/workflow.xml</critical>
<critical>You MUST have already loaded and processed: {project-root}/bmad/qa/workflows/test-planning/workflow.yaml</critical>
<critical>Communicate in {communication_language} throughout the workflow</critical>

<workflow>

<step n="1" goal="Understand project scope and objectives">
<action>Discover the project context and testing needs:

Explore:
- What is the project/product being tested?
- What are the key business objectives?
- What is the scope of testing (new feature, regression, full product)?
- Timeline and release dates?
- Available resources (team size, skills, tools)?

Guide them to articulate:
- Critical business functionality
- Risk areas and concerns
- Success criteria for testing
- Stakeholder expectations
</action>

<template-output>project_scope</template-output>
</step>

<step n="2" goal="Identify test items and features">
<action>Define what will be tested:

Work with user to list:
- Features and functionalities in scope
- Integrations and dependencies
- Platforms and environments (web, mobile, desktop, API)
- User roles and personas

For each test item, identify:
- Complexity level (simple/medium/complex)
- Business criticality (high/medium/low)
- Technical risk (high/medium/low)

Prioritize test items based on risk and criticality.
</action>

<template-output>test_items</template-output>
</step>

<step n="3" goal="Define test strategy and approach">
<action>Design the testing strategy:

**Test Types:**
- Functional testing (unit, integration, system, UAT)
- Non-functional testing (performance, security, usability, accessibility)
- Regression testing
- Smoke/sanity testing

**Test Approach:**
- Manual vs automated testing split
- Exploratory testing needs
- Risk-based testing focus
- Test-driven development integration

**Test Levels:**
- Component/unit level
- Integration level
- System level
- Acceptance level

For each test type, specify:
- Objectives and coverage
- Entry and exit criteria
- Tools and frameworks
- Who performs it
</action>

<template-output>test_strategy</template-output>
</step>

<step n="4" goal="Perform risk assessment">
<action>Identify and assess project risks:

**Technical Risks:**
- Complex integrations
- New technologies
- Performance requirements
- Security vulnerabilities

**Project Risks:**
- Tight timelines
- Resource constraints
- Changing requirements
- Dependencies on external systems

For each risk:
- **Risk Description**: What could go wrong
- **Impact**: High/Medium/Low (effect if it occurs)
- **Probability**: High/Medium/Low (likelihood)
- **Mitigation Strategy**: How to prevent or reduce
- **Contingency Plan**: What to do if it happens

Calculate risk priority (Impact x Probability) and focus testing accordingly.
</action>

<template-output>risk_assessment</template-output>
</step>

<step n="5" goal="Define test environment and data requirements">
<action>Specify testing environments and test data:

**Test Environments:**
- Development environment
- QA/Test environment
- Staging environment
- Production-like environment
- Specific configurations needed

**Test Data:**
- Types of data required
- Data volume requirements
- Data privacy/masking needs
- Test data sources
- Data refresh strategy

**Infrastructure:**
- Hardware requirements
- Network configuration
- Third-party service access
- Database setup
</action>

<template-output>environment_data</template-output>
</step>

<step n="6" goal="Create test schedule and milestones">
<action>Develop testing timeline:

Work with user to define:
- Test preparation phase (environment, data, scripts)
- Test execution phases (by test type or sprint)
- Defect fixing cycles
- Regression testing windows
- Final validation phase

For each phase:
- Start and end dates
- Deliverables
- Dependencies
- Resource allocation
- Review points

Identify critical path and buffer time for risks.
</action>

<template-output>test_schedule</template-output>
</step>

<step n="7" goal="Define test deliverables and reporting">
<action>Specify what will be produced:

**Test Deliverables:**
- Test plan document (this output)
- Test cases and scripts
- Test data sets
- Defect reports
- Test execution reports
- Test summary report
- Lessons learned

**Reporting:**
- Status reporting frequency (daily/weekly)
- Metrics to track (pass/fail rate, coverage, defects, velocity)
- Stakeholders and communication plan
- Escalation procedures
- Sign-off criteria

Define acceptance criteria for testing phase completion.
</action>

<template-output>deliverables_reporting</template-output>
</step>

<step n="8" goal="Identify tools, resources, and responsibilities">
<action>Define team structure and tooling:

**Team and Roles:**
- Test lead/manager
- Test engineers (manual/automation)
- Domain experts
- DevOps support
- Responsibilities for each role

**Tools and Frameworks:**
- Test management tools (Jira, TestRail, etc.)
- Automation tools (Selenium, Cypress, etc.)
- Performance tools (JMeter, K6, etc.)
- Defect tracking
- CI/CD integration

**Training Needs:**
- Tool training required
- Domain knowledge needed
- Skills gaps to address
</action>

<template-output>resources_tools</template-output>
</step>

<step n="9" goal="Review and finalize test plan">
<action>Present complete test plan to user:

Show comprehensive summary:
- Scope and objectives
- Strategy and approach
- Risk assessment
- Schedule and milestones
- Resource allocation
- Success criteria

Ask for feedback and refinements.
</action>

<ask>Would you like to refine any section of the test plan? [yes/no]</ask>

<check if="user wants refinement">
  <action>Iterate on specific sections based on feedback</action>
</check>

<action>Save to: {test_plans_folder}/{project_name}-test-plan.md</action>

<action>Address {user_name} in {communication_language}:

"✅ Test plan complete!

**Plan Summary:**
- Test Scope: {{scope_summary}}
- Timeline: {{timeline_summary}}
- Risk Focus: {{top_risks}}

**File saved:** {test_plans_folder}/{project_name}-test-plan.md

**Next steps:**
1. Review with stakeholders
2. Get approval and sign-off
3. Use *design-cases to create detailed test cases
4. Use *generate-automation for automated tests

Your comprehensive test plan provides strategic direction for successful testing."
</action>

<template-output>completion_summary</template-output>
</step>

</workflow>
