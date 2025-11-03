# Result Analysis Workflow Instructions

<critical>The workflow execution engine is governed by: {project-root}/bmad/core/tasks/workflow.xml</critical>
<critical>You MUST have already loaded and processed: {project-root}/bmad/qa/workflows/result-analysis/workflow.yaml</critical>
<critical>Communicate in {communication_language} throughout the workflow</critical>

<workflow>

<step n="1" goal="Gather test execution data">
<action>Collect test results and execution information:

Ask user to provide:
- Test execution reports (JUnit XML, TestNG results, Cypress reports, etc.)
- Test run summary (total, passed, failed, skipped)
- Execution environment and configuration
- Test execution period (start/end dates)
- Team members involved

If test results files are available, offer to read and parse them.
Otherwise, gather information through conversation.

Guide them to describe:
- Overall test execution status
- Any blockers or issues encountered
- Test coverage achieved
</action>

<template-output>test_execution_data</template-output>
</step>

<step n="2" goal="Calculate key metrics and statistics">
<action>Analyze test results numerically:

Calculate and present:

**Test Execution Metrics:**
- Total test cases executed
- Passed tests (count and percentage)
- Failed tests (count and percentage)
- Skipped/blocked tests (count and percentage)
- Pass rate trend (if historical data available)

**Quality Metrics:**
- Test coverage percentage
- Defects found per test case
- Defect density
- Mean time to detect (MTTD)
- Test effectiveness ratio

**Execution Efficiency:**
- Total execution time
- Average time per test
- Flaky test rate
- Automation rate (automated vs manual)

Present metrics in clear, readable format with context.
</action>

<template-output>metrics_statistics</template-output>
</step>

<step n="3" goal="Identify failure patterns and root causes">
<action>Analyze test failures systematically:

For failed tests, identify:

**Failure Categories:**
- Environment issues (config, infrastructure)
- Data problems (missing, incorrect, corrupted)
- Actual product defects
- Test script issues (flaky tests, timing issues)
- Integration failures (API, database, third-party)

**Patterns:**
- Are failures concentrated in specific areas?
- Do failures occur at specific times or conditions?
- Are there common error messages?
- Which components have highest failure rates?

**Root Cause Analysis:**
For major failures:
- What is the underlying cause?
- When was it introduced?
- Why wasn't it caught earlier?
- What is the impact?

Group failures by category and prioritize investigation.
</action>

<template-output>failure_analysis</template-output>
</step>

<step n="4" goal="Analyze trends and comparisons">
<action>Compare results against benchmarks and history:

**Historical Comparison:**
- How do results compare to previous runs?
- Is quality improving or declining?
- Are new issues appearing?
- Are old issues reappearing (regressions)?

**Sprint/Release Comparison:**
- Quality vs previous sprint
- Defect injection rate
- Fix rate

**Benchmark Comparison:**
- Industry standards for pass rate
- Team goals vs actual
- Expected vs actual coverage

**Trend Analysis:**
- Quality trajectory (improving/stable/declining)
- Defect trends
- Test stability trends

Visualize trends when possible (describe charts/graphs).
</action>

<template-output>trend_analysis</template-output>
</step>

<step n="5" goal="Assess test coverage and gaps">
<action>Evaluate testing comprehensiveness:

**Coverage Assessment:**
- Code coverage (if available)
- Requirements coverage
- Feature coverage
- Risk area coverage
- User scenario coverage

**Gap Analysis:**
- What wasn't tested?
- Why wasn't it tested?
- What risks remain?
- Which areas need more testing?

**Coverage Recommendations:**
- Priority areas for additional testing
- Test cases to add
- Coverage targets for next cycle

Balance thoroughness with pragmatism.
</action>

<template-output>coverage_assessment</template-output>
</step>

<step n="6" goal="Identify quality insights and concerns">
<action>Extract actionable quality insights:

**Positive Findings:**
- Areas of strong quality
- Improvements from previous runs
- Stable features
- Effective tests

**Concerns:**
- High-risk areas with failures
- Unstable features
- Technical debt indicators
- Flaky or unreliable tests

**Red Flags:**
- Critical failures
- Security vulnerabilities
- Performance degradation
- Compliance issues

**Quality Gates:**
- Which quality gates passed/failed?
- Is the build ready for next stage?
- What needs to be fixed before proceeding?

Provide evidence-based assessment.
</action>

<template-output>quality_insights</template-output>
</step>

<step n="7" goal="Generate recommendations and action items">
<action>Create actionable recommendations:

**Immediate Actions:**
- Critical bugs to fix
- Blockers to resolve
- Tests to rerun
- Emergency fixes needed

**Short-term Improvements:**
- Flaky tests to stabilize
- Missing test cases to add
- Technical debt to address
- Process improvements

**Long-term Initiatives:**
- Architecture improvements
- Tool upgrades
- Automation expansion
- Team training

For each recommendation:
- What needs to be done
- Why it matters
- Who should do it
- When it should be done
- Expected impact

Prioritize by impact and effort.
</action>

<template-output>recommendations</template-output>
</step>

<step n="8" goal="Create executive summary">
<action>Summarize findings for stakeholders:

Create concise summary including:
- Overall quality status (Green/Yellow/Red)
- Key metrics (pass rate, coverage, defects)
- Top 3 concerns
- Top 3 recommendations
- Go/No-go recommendation for next phase

Use clear, non-technical language suitable for management.
Focus on business impact, not just technical details.

Provide confidence level in quality assessment.
</action>

<template-output>executive_summary</template-output>
</step>

<step n="9" goal="Finalize analysis report">
<action>Save to: {test_results_folder}/analysis-{date}.md</action>

<action>Address {user_name} in {communication_language}:

"✅ Test result analysis complete!

**Quality Status:** {{quality_status}}
**Pass Rate:** {{pass_rate}}%
**Critical Issues:** {{critical_count}}

**File saved:** {test_results_folder}/analysis-{date}.md

**Next steps:**
1. Review findings with team
2. Address critical issues
3. Implement recommended actions
4. Track improvements in next cycle

Your comprehensive analysis provides data-driven insights for quality improvement."
</action>

<template-output>completion_summary</template-output>
</step>

</workflow>
