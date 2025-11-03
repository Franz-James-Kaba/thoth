# Thoth QA Agent 📜

**Senior Quality Assurance Engineer AI Agent** with automated test generation, hybrid selector approach, and comprehensive QA workflows.

[![Framework](https://img.shields.io/badge/Framework-BMAD-blue)]()
[![Status](https://img.shields.io/badge/Status-Production-green)]()
[![License](https://img.shields.io/badge/License-MIT-yellow)]()

---

## 🎯 Overview

Thoth is a comprehensive QA automation agent that generates production-ready test code with intelligent framework selection and adaptive selector strategies. Built with 10+ years of QA expertise encoded into a conversational AI agent.

### Key Features

✅ **Multi-Framework Support**: Selenium, Selenide, Cypress, Appium, RestAssured
✅ **Hybrid Selector Approach**: Adapts to screenshots, HTML, context, or existing selectors
✅ **Page Object Model**: Industry-standard patterns and best practices
✅ **Multiple Languages**: Java, JavaScript, TypeScript
✅ **Test Frameworks**: TestNG, JUnit 5, Mocha, Jest
✅ **14 QA Commands**: From test planning to automation generation

---

## 📦 What's Included

### Thoth Agent
- Senior QA Engineer persona with 10+ years experience
- 14 commands covering test planning, automation, analysis
- Professional, evidence-based communication
- Detective-level curiosity and systematic rigor

### Ready-to-Use Workflow
- **automation-generation**: Complete workflow for generating automated tests
  - 7 comprehensive steps
  - Intent-based + prescriptive hybrid approach
  - 83+ validation criteria
  - Production-ready code generation

### Quick Actions (Work Immediately)
- **quick-bug**: Fast bug report template generation
- **suggest-tests**: Intelligent test scenario suggestions

---

## 🚀 Quick Start

### Installation

**Option 1: Clone Repository**

```bash
# Clone to your project
cd your-project
git clone <this-repo-url> bmad/qa

# Create output folders
mkdir -p qa-output/{test-plans,test-cases,automation,bug-reports,test-results}
```

**Option 2: Download ZIP**

1. Download ZIP from GitHub
2. Extract to `your-project/bmad/qa/`
3. Create output folders (see above)

**Option 3: Git Submodule**

```bash
cd your-project
git submodule add <this-repo-url> bmad/qa
git submodule update --init
mkdir -p qa-output/{test-plans,test-cases,automation,bug-reports,test-results}
```

---

### Configuration

Edit `bmad/qa/config.yaml`:

```yaml
# Update with your information
user_name: 'YourName'
communication_language: 'english'

# Paths (usually these are fine)
output_folder: '{project-root}/qa-output'
automation_folder: '{project-root}/qa-output/automation'

# Preferences
default_test_framework: 'selenium'
default_assertion_framework: 'testng'
default_language: 'java'
```

---

### Usage

**Load Thoth:**
```
Read file: bmad/qa/agents/thoth.md
```

**Use commands:**
```
*help                    # Show all commands
*generate-automation     # Generate test automation ✅
*quick-bug              # Fast bug report ✅
*suggest-tests          # Test suggestions ✅
```

---

## 🎬 Demo: Generate Your First Test

```bash
# 1. Load Thoth
Read: bmad/qa/agents/thoth.md

# 2. Start automation generation
*generate-automation

# 3. Follow the prompts:
# - Describe what you're testing (e.g., "login page")
# - Select framework (Selenium/Cypress/Appium/RestAssured)
# - Choose language (Java/JavaScript/TypeScript)
# - Provide selector info (screenshots/HTML/context)

# 4. Get your test!
# Output: qa-output/automation/YourTest.java
```

**Result**: 200+ lines of production-ready test code with:
- Page Object Model structure
- Proper waits and assertions
- Comprehensive comments
- Execution instructions
- Best practices built-in

---

## 🏗️ Architecture

```
bmad/qa/
├── agents/
│   ├── thoth.agent.yaml         # Source configuration
│   └── thoth.md                 # Compiled agent (XML)
│
├── workflows/
│   └── automation-generation/
│       ├── workflow.yaml         # Workflow config
│       ├── instructions.md       # 7-step process
│       ├── template.md           # Output template
│       ├── checklist.md          # Validation (83+ criteria)
│       └── README.md             # Workflow docs
│
├── config.yaml                   # User configuration
├── INSTALL.md                    # Detailed installation guide
└── README.md                     # This file
```

---

## 🎯 Features Deep Dive

### Hybrid Selector Approach

Thoth intelligently adapts to whatever information you can provide:

| What You Provide | What Thoth Does |
|-----------------|-----------------|
| **Screenshots** | Analyzes elements, suggests robust selectors with priority (data-testid > id > name > CSS > XPath) |
| **HTML Snippets** | Parses structure, generates optimal selectors, validates syntax |
| **URL + Context** | Creates framework with placeholder selectors + comprehensive DevTools guide |
| **Existing Selectors** | Validates syntax, uses directly in generated code |
| **General Structure** | Generates best-practice framework with descriptive placeholders |

### Multi-Framework Support

**Web Automation:**
- **Selenium**: Industry standard, cross-browser, Java-based
- **Selenide**: Concise wrapper, built-in waits, Java
- **Cypress**: Modern JavaScript, fast, developer-friendly

**Mobile Automation:**
- **Appium**: Cross-platform (iOS/Android), touch gestures

**API Testing:**
- **RestAssured**: Fluent Java API, JSON/XML validation

### Code Quality Standards

All generated code includes:
- ✅ Page Object Model pattern
- ✅ Explicit waits (no Thread.sleep)
- ✅ Proper annotations (@Test, @BeforeMethod, etc.)
- ✅ Comprehensive comments
- ✅ Exception handling
- ✅ Configurable timeouts
- ✅ Reusable methods
- ✅ Language-specific conventions

---

## 📋 Available Commands

### Core Workflows
| Command | Status | Description |
|---------|--------|-------------|
| `*plan-tests` | 🔨 To Build | Create comprehensive test plan with risk assessment |
| `*design-cases` | 🔨 To Build | Design detailed test cases and scenarios |
| `*generate-automation` | ✅ **Ready** | Generate automated test code |
| `*report-bug` | 🔨 To Build | Create detailed bug report with repro steps |
| `*analyze-results` | 🔨 To Build | Analyze test results and identify patterns |

### Advanced Workflows
| Command | Status | Description |
|---------|--------|-------------|
| `*identify-edges` | 🔨 To Build | Identify edge cases and boundary conditions |
| `*analyze-coverage` | 🔨 To Build | Analyze test coverage gaps |
| `*design-api-tests` | 🔨 To Build | Design API test suite with RestAssured |
| `*guide-accessibility` | 🔨 To Build | WCAG compliance testing guidance |
| `*plan-performance` | 🔨 To Build | Performance testing strategy |

### Quick Actions
| Command | Status | Description |
|---------|--------|-------------|
| `*quick-bug` | ✅ Works Now | Fast bug report template |
| `*suggest-tests` | ✅ Works Now | Test scenario suggestions |

**Note**: Commands marked 🔨 require workflow creation (contributions welcome!)

---

## 🔧 Requirements

- Text editor or IDE supporting markdown/YAML
- AI assistant capable of reading XML/markdown files
- Java 11+ (for Selenium/TestNG tests)
- Node.js 16+ (for Cypress tests)
- Maven or Gradle (for Java projects)
- npm or yarn (for JavaScript projects)

---

## 📖 Documentation

- **[INSTALL.md](INSTALL.md)** - Detailed installation guide
- **[automation-generation/README.md](workflows/automation-generation/README.md)** - Workflow documentation
- **[automation-generation/instructions.md](workflows/automation-generation/instructions.md)** - Step-by-step workflow
- **[automation-generation/checklist.md](workflows/automation-generation/checklist.md)** - 83+ validation criteria

---

## 🤝 Contributing

We welcome contributions! Here's how:

### Add New Workflows

The 9 remaining workflows need to be built:
- test-planning
- test-case-design
- bug-reporting
- result-analysis
- edge-case-identification
- coverage-analysis
- api-test-design
- accessibility-guidance
- performance-planning

See `workflows/automation-generation/` as a template.

### Improve Existing Workflows

- Add more framework support
- Enhance selector strategies
- Improve code templates
- Add validation criteria

### Report Issues

Found a bug or have a suggestion? Open an issue!

---

## 🧪 Testing

Before using in production:

1. **Test Installation**: Copy to test project, verify files exist
2. **Test Configuration**: Update config.yaml, verify paths
3. **Test Quick Actions**: Try `*quick-bug` and `*suggest-tests`
4. **Test Workflow**: Run `*generate-automation` end-to-end
5. **Test Generated Code**: Verify syntax, compile, run tests

---

## 🎓 Use Cases

### Individual QA Engineers
- Generate test automation quickly
- Maintain consistent code quality
- Follow industry best practices
- Learn automation patterns

### QA Teams
- Standardize test code patterns
- Accelerate test development
- Share common workflows
- Improve test coverage

### Development Teams
- Add QA expertise to AI assistant
- Generate tests during development
- Shift-left testing approach
- Continuous quality improvement

---

## 📊 Metrics

- **Code Generated**: 200+ lines per test
- **Frameworks Supported**: 5 (Selenium, Selenide, Cypress, Appium, RestAssured)
- **Languages**: 3 (Java, JavaScript, TypeScript)
- **Test Frameworks**: 4 (TestNG, JUnit 5, Mocha, Jest)
- **Validation Criteria**: 83+ checks
- **Time to First Test**: < 10 minutes

---

## 🗺️ Roadmap

**v1.0 (Current)**
- ✅ Thoth agent with 14 commands
- ✅ automation-generation workflow
- ✅ Hybrid selector approach
- ✅ Multi-framework support

**v1.1 (Planned)**
- 🔨 test-planning workflow
- 🔨 test-case-design workflow
- 🔨 bug-reporting workflow

**v2.0 (Future)**
- 🔮 Visual test generation from screenshots
- 🔮 AI-powered selector recommendations
- 🔮 Test maintenance suggestions
- 🔮 Coverage gap analysis

---

## 📄 License

MIT License - Feel free to use in personal or commercial projects.

---

## 🙏 Acknowledgments

Built with:
- BMAD Framework (Business Method Automation Development)
- Claude Code (Anthropic)
- Industry QA best practices

Created by: **Franzy**
Date: 2025-11-03
Version: 1.0.0

---

## 🔗 Links

- [BMAD Framework](#) - Coming soon
- [Documentation](#) - Full docs
- [Examples](#) - Sample tests
- [Community](#) - Discord/Forum

---

## ⚡ Quick Links

- [Installation Guide](INSTALL.md)
- [Automation Workflow Docs](workflows/automation-generation/README.md)
- [Configuration Reference](config.yaml)
- [Validation Checklist](workflows/automation-generation/checklist.md)

---

**Ready to supercharge your QA automation? Install Thoth today!** 🚀

```bash
git clone <repo-url> bmad/qa
cd bmad/qa
# Update config.yaml
# Load thoth.md
# Run *generate-automation
```

---

**Questions? Issues? Contributions?** Open an issue or PR!
