
# Copilot Infrastructure: Prompts & Agents

This repository provides a robust framework for customizing GitHub Copilot’s behavior using structured instructions, agent roles, and reusable prompt templates. All configuration is managed in the `.github` folder. This Folder should be placed at repository root (or in certain cases, the location, where the solutionfile or workspace resides). The files mentioned in this document are partially taken from the open source project: 'Awesome Copilot' (link below).



## Precursor

Please note that these features are evolving rapidly and may change over time. As a result, some of the described behaviors might not always work as documented.

To get the most out of this setup, it’s recommended to create an `architecture.md` file in the `.github` directory at the root of your repository. This file should describe your project’s structure and technologies. See Chapter 3: Prompts for more details.

If you are using Visual Studio 2022 or 2026, make sure to enable custom instructions:
Go to **Tools → Options → GitHub → Copilot** and check **'Enable Custom instructions to be loaded ...'**

## Folder Structure

- `.github/copilot-instructions.md` — Global Copilot behavior and coding standards
- `.github/agents/` — Role-based agent instructions (how Copilot should act for specific personas)
- `.github/prompts/` — Reusable prompt templates for common tasks

---

## 1. Global Copilot Instructions

The file `.github/copilot-instructions.md` defines default guidelines for Copilot across your project. It covers:
- Coding conventions (e.g., C# standards, naming, documentation)
- Scope of assistance (only change what’s requested)
- How to clarify ambiguous requests
- When to use or minimize comments

**Tip:** Update this file to enforce your team’s coding and documentation standards.

---

## 2. Agents: Role-Based Copilot Behavior

The `.github/agents/` directory contains agent instruction files. Each file describes how Copilot should behave when acting as a specific role. Example agents:

- **janitor.agent.md** — Cleans codebases, removes tech debt, simplifies aggressively
- **mentor.agent.md** — Offers guidance, asks clarifying questions, never edits code directly
- **planner.agent.md** — Generates implementation plans, not code
- **principal-software-engineer.agent.md** — Provides expert engineering advice, reviews, and risk assessments
- **prompt-engineer.agent.md** — Analyzes and improves prompts, always outputs a better prompt

**How it works:**
- When your prompt specifies a role (e.g., “as a janitor”), Copilot uses the matching agent file for its behavior.
- If no agent matches, Copilot falls back to `.github/copilot-instructions.md`.

**To add a new agent:**
1. Create a new file in `.github/agents/` (e.g., `devops-engineer.agent.md`).
2. Describe the role’s philosophy, allowed actions, and any special tools or restrictions.

---

## 3. Prompts: Task Templates

The `.github/prompts/` directory contains prompt templates for common or complex tasks. Each file defines:
- The agent/persona to use
- The task description and requirements
- Tools or context needed

**Available prompt templates:**
- **ArchitectureDocGenerator.prompt.md** — Scans the codebase and generates a detailed architecture.md
- **CodebaseAnalysis.prompt.md** — Explains how features/classes work or where to find them
- **CodeStyling.prompt.md** — Applies formatting to selected files per .editorconfig
- **create-implementation-plan.prompt.md** — Produces a machine-readable, stepwise implementation plan
- **CreateUnitTest.prompt.md** — Generates NUnit unit tests for specified classes
- **prompt-builder.prompt.md** — Guides users through creating new, high-quality prompt files

**To use a prompt template:**
1. Copy or reference the template in your Copilot request.
2. Customize variables or context as needed.

**To add a new prompt:**
1. Create a `.prompt.md` file in `.github/prompts/`.
2. Follow the structure of existing prompts for consistency.

---

## Best Practices

- Keep agent and prompt files up to date as your team’s needs evolve.
- Review Copilot’s output for compliance with your standards.
- Use agents for specialized workflows to ensure consistency.
- Reference or reuse prompt templates for repeatable tasks.

---

## Example Usage

**Unittests**
- Visual Studio: 
    - type # and prompt, then you should be presented with prompts you can choose from
    - choose CreateUnitTest.prompt.md
    - add the files you want it to write you tests for.
    - check location and output, then answer with yes or suggestions
    - check generated files and tests

- Visual Studio code:
    - type / and choose the prompt CreateUnitTest
    - add files with #<filename> 
    - check location and output, then answer with yes or further suggestions
    - check generated files and unittests

**Formatting**
> Format `Inventum.UI.Items\ViewItems\CompressorController.cs` to resolve styling warnings according to `.editorconfig`.

---

## Troubleshooting

- If Copilot ignores your agent, check the filename and structure in `.github/agents/`.
- For general issues, review `.github/copilot-instructions.md` for missing or conflicting guidelines.

---

## Resources

- [Awesome Copilot Repository](https://github.com/github/awesome-copilot/tree/main)
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [VS Code Copilot Extension](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)

For questions or to contribute improvements, open an issue or pull request in this repository.
