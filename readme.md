# Integrated Workflow Documentation

This document serves as an index for the integrated workflow documentation that combines Kilocode modes, Memory Bank, and GitFlow for feature development in any software project.

## Overview

The integrated workflow is designed to streamline the development process by leveraging:

1. **Kilocode Modes**: Specialized AI assistance for different development phases
2. **Memory Bank**: Persistent project knowledge across sessions
3. **GitFlow**: Structured branching strategy for feature development and releases

This combination creates a powerful workflow that enhances knowledge retention, provides specialized expertise, structures the development process, reduces technical debt, and improves collaboration.

## Documentation Index

### Core Workflow Documents

1. [**Integrated Workflow**](./integrated-workflow.md)
   - Comprehensive overview of the workflow
   - Detailed description of each phase
   - Mode-specific responsibilities
   - Memory Bank integration
   - Implementation example

2. [**Workflow Diagram**](./workflow-diagram.md)
   - Visual representation of the workflow
   - Mermaid diagrams showing relationships between components
   - Simplified workflow diagram for quick reference

3. [**Practical Guide**](./workflow-practical-guide.md)
   - Step-by-step instructions for implementing the workflow
   - Specific commands and actions for each phase
   - Quick reference table
   - Example workflow for a specific feature

4. [**Benefits and Challenges**](./workflow-benefits-challenges.md)
   - Detailed benefits of the integrated approach
   - Potential challenges and mitigation strategies
   - Implementation recommendations
   - Success metrics

5. [**N1 Credits Implementation**](./n1-credits-workflow-implementation.md)
   - Project-specific workflow considerations
   - Memory Bank structure for N1 Credits
   - Detailed examples based on project architecture
   - Common patterns and tasks

## Quick Start

To get started with the integrated workflow:

1. **Review the Memory Bank**: Familiarize yourself with the current project state by reviewing the Memory Bank files in `.kilocode/rules/memory-bank/`.

2. **Select the Appropriate Mode**: Choose the Kilocode mode that matches your current task:
   - Architect mode for design and planning
   - Code mode for implementation
   - Debug mode for testing and troubleshooting
   - Ask mode for clarification and explanation
   - Orchestrator mode for coordination and release management

3. **Follow GitFlow Branching**: Create branches according to GitFlow conventions:
   - `architecture/feature-name` for architecture planning and design
   - `feature/feature-name` for new features implementation
   - `bugfix/bug-name` for bug fixes
   - `release/version` for releases
   - `hotfix/fix-name` for urgent production fixes

4. **Update Memory Bank**: Keep the Memory Bank updated as you make significant changes to the project.

## Workflow Phases

| Phase | Kilocode Mode | GitFlow Branch | Memory Bank Focus | Key Activities |
|-------|--------------|----------------|-------------------|----------------|
| Planning | Architect | architecture/feature-name | brief.md, product.md, architecture.md | Feature analysis, architecture planning, task breakdown, architecture PR |
| Development | Code, Debug | feature/feature-name | architecture.md, tech.md | Implementation, testing, documentation |
| Review | Code, Ask | feature/feature-name | All relevant files | Self-review, PR creation, feedback incorporation |
| Integration | Debug, Orchestrator | develop | context.md, tasks.md | Merge to develop, integration testing, Memory Bank updates |
| Release | Orchestrator, Debug | release/version | All files | Release preparation, final testing, version tagging |

## Memory Bank Structure

The Memory Bank for N1 Credits Backend consists of:

### Core Files
- **brief.md**: Project overview, objectives, features, and success criteria
- **product.md**: Purpose, problems solved, and user experience goals
- **context.md**: Current state, recent work, and next steps
- **architecture.md**: System architecture, components, and patterns
- **tech.md**: Technology stack and development setup

### Additional Files
- **tasks.md**: Documentation of repetitive tasks and their workflows
- Feature-specific documentation
- Integration specifications
- API documentation

## Best Practices

1. **Start Each Session with Memory Bank Review**
   - Always begin by reviewing the Memory Bank to understand the current context
   - Look for recent changes in context.md

2. **Use the Right Mode for Each Task**
   - Match the Kilocode mode to the specific task at hand
   - Switch modes as needed for different aspects of the same feature

3. **Keep Memory Bank Updated**
   - Update context.md after significant changes
   - Add repetitive tasks to tasks.md
   - Update architecture.md when making architectural changes

4. **Follow GitFlow Strictly**
   - Create architecture branches for planning and design
   - Get architecture PRs reviewed and approved before implementation
   - Always branch from develop for features
   - Use --no-ff when merging to preserve history
   - Tag releases properly

5. **Commit Best Practices**
   - Use conventional commit messages (feat, fix, docs, style, refactor, test, chore)
   - Keep commits focused on single changes
   - Write descriptive commit messages

## Getting Help

If you need assistance with the workflow:

1. **Consult the Documentation**: Review the relevant workflow document for guidance
2. **Use Ask Mode**: Switch to Ask mode to get clarification on workflow questions
3. **Update the Workflow**: If you discover improvements to the workflow, document them and share with the team

## Conclusion

This integrated workflow is designed to enhance the development process for the N1 Credits Backend project. By combining Kilocode modes, Memory Bank, and GitFlow, the team can work more efficiently, maintain high code quality, and ensure knowledge is preserved throughout the project lifecycle.

The workflow is not static—it should evolve as the team identifies improvements and as the project grows. Regular reviews of the workflow effectiveness will help ensure it continues to meet the team's needs.
