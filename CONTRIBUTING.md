# Contributing to OpenMettle

OpenMettle aims to make capable AI systems easier to run and use. Improvements to setup, documentation, accessibility and recovery are as valuable as new features.

## Before you begin

Read the repository's README and current issues. Use Discussions for open design questions. For a substantial change, describe the user problem and proposed behavior in an issue before implementing it.

The project is in early development. A documented implementation in one environment does not establish support for every machine, model or operating system.

## Make a change

1. Fork the relevant repository and create a short-lived branch.
2. Make a focused change with clear, readable names.
3. Run the checks listed in that repository and add meaningful tests for changed behavior.
4. Update affected configuration examples and user documentation.
5. Open a pull request describing the problem, new behavior, validation and any migration or rollback steps.

State which checks you ran, which were not run, and why. For model or performance work, report hardware, software versions, model and quantization, workload, context length and concurrency. Include quality checks when a change can affect output; a faster result alone does not demonstrate a better assistant.

## Configuration and documentation

- Keep installation-specific values in local configuration or secrets; publish sanitized examples.
- Use reserved example domains and non-sensitive sample data. Never include live tokens, private keys, personal conversations, internal endpoints or customer data.
- Explain prerequisites, verification and recovery next to operational commands.
- Clearly mark destructive commands and require explicit execution for destructive automation.
- Separate planned features, experimental behavior and verified support.
- Keep original copyright notices, licenses and upstream attribution when importing material.

## Review

Maintainers review behavior, maintainability and the user experience. Pull requests may be squash-merged after the required checks pass. No contributor license agreement is introduced by this guide; contributions are governed by the applicable repository license.

See the [code of conduct](https://github.com/OpenMettle/.github/blob/main/CODE_OF_CONDUCT.md) and [security policy](https://github.com/OpenMettle/.github/blob/main/SECURITY.md).
