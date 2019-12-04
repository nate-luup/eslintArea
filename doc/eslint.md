# Eslint

> ESLint uses Espree for JavaScript parsing.
> ESLint uses an AST to evaluate patterns in code.
> **ESLint is completely pluggable, every single rule is a plugin and you can add more at runtime.**

- [Doc](#doc)
- [Generate Report](#report)
- [Reference](#Reference)

<h2 id="doc">DOC</h2>

- [Getting Started with ESLint](https://eslint.org/docs/user-guide/getting-started)
    - Installation and Usage
    - Configuration
- [Configuring ESLint](https://eslint.org/docs/user-guide/configuring)
    - Specifying Parser Options
    - Specifying Parser
    - Specifying Processor
    - Specifying Environments
    - Specifying Globals
    - Configuring Plugins
    - Configuring Rules
    - Disabling Rules with Inline Comments
    - Configuring Inline Comment Behaviors
    - Adding Shared Settings
    - Using Configuration Files
    - Configuration File Formats
    - Configuration Cascading and Hierarchy
    - Extending Configuration Files
    - Configuration Based on Glob Patterns
    - Comments in Configuration Files
    - Specifying File extensions to Lint
    - Ignoring Files and Directories
    - Personal Configuration File (deprecated)
- [Command Line Interface](https://eslint.org/docs/user-guide/command-line-interface)
- [Rules](https://eslint.org/docs/rules/)
- [Formatters](https://eslint.org/docs/user-guide/formatters/)
- [Integrations](https://eslint.org/docs/user-guide/integrations)

<h2 id="report">Generate Report</h2>

- [eslint-html-reporter](https://www.npmjs.com/package/eslint-html-reporter)

1. Generate report with `waring` and `error`

```bash
npx eslint src/**  -f node_modules/eslint-html-reporter/reporter.js -o report.html
```

2. Generate report only contains `error`

```bash
npx eslint src/** --quiet -f node_modules/eslint-html-reporter/reporter.js -o report.html
```

<h2 id="Reference">Reference</h2>

- [Eslint](https://eslint.org/)
- [Eslint 中文](https://cn.eslint.org/)
- [eslint-plugin 开发入门](https://www.jianshu.com/p/f3fddccb059a)
