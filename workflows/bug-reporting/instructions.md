# Bug Reporting Workflow Instructions

<critical>The workflow execution engine is governed by: {project-root}/bmad/core/tasks/workflow.xml</critical>
<critical>You MUST have already loaded and processed: {project-root}/bmad/qa/workflows/bug-reporting/workflow.yaml</critical>
<critical>Communicate in {communication_language} throughout the workflow</critical>

<workflow>

<step n="1" goal="Capture bug summary and basic information">
<action>Gather essential bug information:

Guide user to provide:
- **Bug Title**: Clear, concise summary (one sentence)
- **Bug ID**: Tracking number if available, otherwise auto-generate
- **Discovery Date**: When was it found
- **Reporter**: Who found it (default to {user_name})
- **Environment**: Where it occurred (dev/test/staging/production)

Help them craft a title that includes:
- What is broken
- Where it's broken
- Impact on user

Example: "Login button unresponsive on mobile Chrome browser"
</action>

<template-output>bug_summary</template-output>
</step>

<step n="2" goal="Determine severity and priority">
<action>Assess bug impact and urgency:

**Severity** (technical impact):
- **Critical**: System crash, data loss, security breach
- **High**: Major functionality broken, no workaround
- **Medium**: Feature partially broken, workaround exists
- **Low**: Minor issue, cosmetic problem

**Priority** (business urgency):
- **P1/Urgent**: Fix immediately, blocks release
- **P2/High**: Fix in current sprint
- **P3/Medium**: Fix in next release
- **P4/Low**: Fix when time allows

Guide user through decision:
- How many users affected?
- Is there a workaround?
- Does it block testing or release?
- What is the business impact?
</action>

<template-output>severity_priority</template-output>
</step>

<step n="3" goal="Document reproduction steps">
<action>Create detailed, reproducible steps:

Guide user to provide:
- **Preconditions**: What setup is needed before starting
- **Step-by-Step Instructions**: Numbered, specific actions
- **Test Data**: Exact inputs used
- **Expected Result**: What should happen
- **Actual Result**: What actually happened

Ensure steps are:
- Specific and actionable
- In chronological order
- Include exact values/inputs
- Can be followed by someone unfamiliar with the feature

Example format:
1. Navigate to login page (https://example.com/login)
2. Enter username: "testuser@example.com"
3. Enter password: "Test@123"
4. Click "Login" button
5. Expected: Redirect to dashboard
6. Actual: Button becomes unresponsive, no navigation occurs
</action>

<template-output>reproduction_steps</template-output>
</step>

<step n="4" goal="Gather environment and configuration details">
<action>Collect technical context:

**System Information:**
- Operating System (Windows 11, macOS 14, iOS 17, Android 13, etc.)
- Browser/App version
- Screen resolution (if UI-related)
- Device type (desktop, mobile, tablet)

**Application Details:**
- Application version/build number
- Environment (dev/test/staging/production)
- Configuration settings relevant to bug
- User role/permissions

**Network/Infrastructure:**
- Network conditions (if relevant)
- Database version
- API versions
- Third-party service versions

This helps developers reproduce and fix the issue.
</action>

<template-output>environment_details</template-output>
</step>

<step n="5" goal="Add supporting evidence">
<action>Collect screenshots, logs, and attachments:

Ask user if they can provide:
- **Screenshots**: Visual evidence of the issue
- **Screen recordings/videos**: Reproduction walkthrough
- **Console logs**: Browser console errors
- **Network logs**: API failures or timeouts
- **Server logs**: Backend errors
- **Stack traces**: Error details

For each piece of evidence:
- Note what it shows
- When it was captured
- Include file name/path

Guide them on capturing:
- Browser console: F12 → Console tab
- Network logs: F12 → Network tab
- Screenshots: PrintScreen or Snipping Tool
</action>

<template-output>supporting_evidence</template-output>
</step>

<step n="6" goal="Identify affected areas and impact">
<action>Determine scope of the bug:

**Affected Functionality:**
- Which features are impacted
- Which user roles affected
- Which workflows broken

**Impact Assessment:**
- How many users potentially affected
- Business processes impacted
- Revenue/customer satisfaction impact
- Regulatory/compliance concerns

**Regression Status:**
- Is this a new bug or regression?
- When did it start occurring?
- What changed recently (code/config/infrastructure)?

This helps prioritize and allocate resources.
</action>

<template-output>impact_assessment</template-output>
</step>

<step n="7" goal="Document workarounds and temporary solutions" optional="true">
<action>Identify temporary fixes if available:

Ask if there's a workaround:
- Alternative way to complete the task
- Manual process to bypass the bug
- Configuration change that helps
- Rollback option

Document:
- What is the workaround
- Steps to implement it
- Limitations or side effects
- How long it can be used

This helps unblock users while fix is in progress.
</action>

<template-output>workarounds</template-output>
</step>

<step n="8" goal="Add additional context and notes">
<action>Include any other relevant information:

- Related bugs or dependencies
- Previous similar issues
- Attempted fixes that didn't work
- Developer notes or hints
- Customer feedback or complaints
- Links to requirements or user stories

Anything that helps developers understand and fix faster.
</action>

<template-output>additional_context</template-output>
</step>

<step n="9" goal="Review and finalize bug report">
<action>Present complete bug report to user:

Show summary:
- Bug ID and title
- Severity and priority
- Clear reproduction steps
- Environment details
- Supporting evidence
- Impact assessment

Ask for verification:
- Are reproduction steps clear and complete?
- Is severity/priority appropriate?
- Is any information missing?
</action>

<ask>Is the bug report complete and accurate? [yes/no]</ask>

<check if="user wants changes">
  <action>Make requested updates to bug report</action>
</check>

<action>Save to: {bug_reports_folder}/BUG-{bug_id}-{date}.md</action>

<action>Address {user_name} in {communication_language}:

"✅ Bug report created!

**Bug ID:** {{bug_id}}
**Severity:** {{severity}}
**Priority:** {{priority}}

**File saved:** {bug_reports_folder}/BUG-{bug_id}-{date}.md

**Next steps:**
1. Submit to bug tracking system (Jira, GitHub Issues, etc.)
2. Attach screenshots and logs
3. Assign to appropriate developer
4. Track progress until resolved

Your detailed bug report provides all information needed for quick resolution."
</action>

<template-output>completion_summary</template-output>
</step>

</workflow>
