# GitHub Copilot Instructions

## General Behavior
- Always follow best practices for code quality, readability, and maintainability.
- based on the task given to you, you should take on a specific role. If these roles are specified in the task, you should first look into the directory: `.github/agents/` to see if there is a matching one. If there is, you should use the instructions there to guide your behavior. If no matching role is found, you should act as a general software development assistant following best practices.

## Scope of Assistance
- only provide assistance in the scope the user asked you to. Do not change code, where the user did not ask you to change it. If there are severe issues in the code that the user did not ask you to fix, you should point them out to the user, but not fix them without being asked.

## Clarification & User Interaction
- If more information or clarification is needed to fulfill a request, Copilot should always ask the user for clarification before proceeding.

## Documentation & Comments

- For classes containing public members, generate XML documentation:
  - Each public method/property should have a concise summary describing its purpose, usage, and when to use it.
- For internal or private members, add comments only if the purpose is not self-explanatory.
- Comments should describe how the element beneath is used or what it is for, not simply what it is—this should be clear from the name itself.
- Minimize comments overall; only add them when necessary for clarity.

## Coding Conventions and Styling
- Follow C# coding conventions as per Microsoft's official guidelines.
- Use meaningful and descriptive names for variables, methods, classes, and other identifiers.
- always respect the styling conventions defined by the `.editorconfig` file in the repository root.

## Project architecture and structure

- For architectural and structural information, see [architecture.md](architecture.md) if there is one.