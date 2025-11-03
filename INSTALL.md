# Thoth QA Agent - Installation Guide

Complete QA automation module with Thoth agent and automation-generation workflow.

---

## 📦 What's Included

### Thoth Agent 📜
- **Senior QA Engineer** with 10+ years expertise
- **14 Commands** (1 workflow ready, 2 quick actions working, 9 to be built)
- **Multi-Framework Support**: Selenium, Selenide, Cypress, Appium, RestAssured
- **Hybrid Selector Approach**: Adapts to screenshots, HTML, context, or placeholders

### Ready-to-Use Workflow
- **automation-generation**: Generate production-ready test code with POM pattern

### Quick Actions (Work Immediately)
- **quick-bug**: Fast bug report template
- **suggest-tests**: Test scenario suggestions

---

## 🚀 Installation Steps

### Step 1: Copy the QA Module

Copy the entire module folder to your target project. You can choose any location - here are some popular options:

```bash
# Option 1: Copy to project root as 'thoth-qa' (Recommended)
cp -r qa /path/to/your-project/thoth-qa

# Option 2: Copy to '.claude' directory (if using Claude Code)
cp -r qa /path/to/your-project/.claude/thoth-qa

# Option 3: Copy to 'tools' directory
cp -r qa /path/to/your-project/tools/thoth-qa

# Option 4: Use your own custom location
cp -r qa /path/to/your-project/your-custom-folder/thoth-qa
```

**What gets copied:**
```
thoth-qa/
├── agents/
│   ├── thoth.agent.yaml         # Source YAML
│   └── thoth.md                 # Compiled agent (ready to use)
├── config.yaml                   # Configuration
├── workflows/
│   └── automation-generation/
│       ├── workflow.yaml         # Workflow config
│       ├── instructions.md       # 7-step process
│       ├── template.md           # Output template
│       ├── checklist.md          # 83+ validation criteria
│       └── README.md             # Workflow documentation
├── INSTALL.md                    # This file
└── README.md                     # Module overview
```

**Note:** Throughout this guide, we use `thoth-qa` as the directory name. If you chose a different location or name, replace `thoth-qa` with your actual path in all commands below.

---

### Step 2: Create Output Directories

Create the required output folders in your project:

```bash
cd /path/to/your-project
mkdir -p qa-output/{test-plans,test-cases,automation,bug-reports,test-results}
```

**Directory structure:**
```
your-project/
├── thoth-qa/                      # QA module (copied)
└── qa-output/                    # Output folders (created)
    ├── test-plans/
    ├── test-cases/
    ├── automation/               # Generated test code goes here
    ├── bug-reports/
    └── test-results/
```

---

### Step 3: Customize Configuration

Edit `thoth-qa/config.yaml` for your project:

```yaml
# Update these values:
user_name: 'YourName'             # Your name
communication_language: 'english' # Your preferred language

# Verify/update paths (usually these are fine):
output_folder: '{project-root}/qa-output'
automation_folder: '{project-root}/qa-output/automation'
# ... (other folders)

# QA preferences (optional):
default_test_framework: 'selenium'
default_assertion_framework: 'testng'
default_language: 'java'
```

---

### Step 4: Verify Installation

Check that all files are in place:

```bash
# From your project root (adjust 'thoth-qa' to your chosen directory name)
ls -la thoth-qa/agents/thoth.md              # Should exist
ls -la thoth-qa/workflows/automation-generation/workflow.yaml  # Should exist
ls -la thoth-qa/config.yaml                  # Should exist
ls -la qa-output/automation/                # Should exist (empty)
```

---

## ✅ Using Thoth

### Method 1: Direct Load (Recommended)

Read the agent file to activate Thoth:

```
Read file: thoth-qa/agents/thoth.md
```

Then use any command:
```
*help                    # Show all commands
*generate-automation     # Generate test automation
*quick-bug              # Fast bug report
*suggest-tests          # Test suggestions
```

---

### Method 2: Slash Command (If Supported)

Create a slash command for quick access:

```bash
# Copy to commands folder
mkdir -p .claude/commands
cp thoth-qa/agents/thoth.md .claude/commands/thoth.md
```

Then use:
```
/thoth
*generate-automation
```

---

## 🎯 Quick Start Example

Let's generate your first automated test:

**1. Load Thoth:**
```
Read: thoth-qa/agents/thoth.md
```

**2. Start automation generation:**
```
*generate-automation
```

**3. Follow the workflow:**
- Describe what you're testing
- Select framework (Selenium/Cypress/etc.)
- Choose language (Java/JavaScript/TypeScript)
- Provide selector information (screenshots/HTML/context)
- Review generated code
- Get complete test file with instructions

**4. Find your generated test:**
```
qa-output/automation/YourTestName.java
```

---

## 📚 What Each Command Does

### Core Workflows (Require Building)
- `*plan-tests` - Comprehensive test planning
- `*design-cases` - Test case design
- `*report-bug` - Detailed bug reports
- `*analyze-results` - Results analysis
- `*identify-edges` - Edge case identification
- `*analyze-coverage` - Coverage analysis
- `*design-api-tests` - API test design
- `*guide-accessibility` - Accessibility guidance
- `*plan-performance` - Performance planning

### Ready Now
- `*generate-automation` ✅ - Full workflow ready
- `*quick-bug` ✅ - Works immediately
- `*suggest-tests` ✅ - Works immediately

---

## 🔧 Customization

### Update Output Locations

Edit `thoth-qa/config.yaml`:

```yaml
# Change where files are generated
output_folder: '{project-root}/custom-output'
automation_folder: '{project-root}/tests/automation'
```

Then create the new folders:
```bash
mkdir -p custom-output tests/automation
```

### Add More Frameworks

The automation workflow supports:
- **Web**: Selenium, Selenide, Cypress
- **Mobile**: Appium
- **API**: RestAssured

No additional setup needed - just select during workflow!

### Change Defaults

Update preferences in `config.yaml`:

```yaml
default_test_framework: 'cypress'      # Change to Cypress
default_assertion_framework: 'jest'    # Change to Jest
default_language: 'typescript'         # Change to TypeScript
```

---

## 🐛 Troubleshooting

### Issue: "File not found" errors

**Solution:** Ensure paths use `{project-root}` not absolute paths
- Check `workflow.yaml` → config_source path
- Check `config.yaml` → all folder paths

### Issue: Output folders don't exist

**Solution:** Create them manually:
```bash
mkdir -p qa-output/{test-plans,test-cases,automation,bug-reports,test-results}
```

### Issue: Config variables not loading

**Solution:** Verify `config.yaml` exists at `thoth-qa/config.yaml` and has proper structure

---

## 📖 Documentation

- **Thoth Agent**: See `thoth-qa/agents/thoth.md`
- **Automation Workflow**: See `thoth-qa/workflows/automation-generation/README.md`
- **Workflow Details**: See `thoth-qa/workflows/automation-generation/instructions.md`
- **Validation**: See `thoth-qa/workflows/automation-generation/checklist.md`

---

## 🚀 Next Steps

1. **Test the installation**: Run `*quick-bug` or `*suggest-tests`
2. **Generate your first test**: Use `*generate-automation`
3. **Build more workflows**: Create the 9 remaining workflows for full Thoth capability
4. **Customize**: Adjust config for your team's preferences

---

## 💡 Tips

- **Start Simple**: Try `*quick-bug` first to verify everything works
- **Use Hybrid Approach**: Provide screenshots or HTML for best selector generation
- **Follow POM Pattern**: Generated code uses Page Object Model best practices
- **Review Code**: Always review generated tests before running
- **Update Selectors**: If using context-only, update placeholder selectors

---

## ⚡ Performance

- **Installation**: < 1 minute (just copy files)
- **First Use**: Instant (no compilation needed)
- **Workflow Execution**: 5-10 minutes for full automation generation
- **Code Generation**: Production-ready tests with 200+ lines of code

---

## 🤝 Support

For issues or questions:
1. Check workflow README files
2. Review validation checklist
3. Verify configuration settings
4. Ensure output folders exist

---

## 📋 Checklist

Before using in a new project:

- [ ] Copied `thoth-qa/` folder to project
- [ ] Created `qa-output/` folders (5 subfolders)
- [ ] Updated `config.yaml` with your name
- [ ] Verified paths in `config.yaml`
- [ ] Tested loading `thoth.md`
- [ ] Tried a quick command (`*quick-bug`)
- [ ] Generated first test (`*generate-automation`)

---

**You're ready to go! Start by loading Thoth and running `*help` to see all available commands.**

---

**Created by:** Franzy
**Date:** 2025-11-03
**Version:** 1.0.0
**Module:** qa (Quality Assurance)
