# Integrated Workflow: Kilocode Modes + Memory Bank + GitFlow

This document outlines a comprehensive workflow that integrates Kilocode's agent modes, Memory Bank, and GitFlow to create a streamlined process for developing new features in any software project.

## 1. Feature Planning Phase

**Branch**: architecture/feature-name (from develop)
**Kilocode Mode**: Architect
**Memory Bank Focus**: brief.md, product.md, architecture.md

### Workflow Steps:
1. **Branch Creation for Planning**
   ```bash
   git checkout develop
   git pull
   git checkout -b architecture/feature-name
   ```

2. **Feature Request Analysis**
   - Use Architect mode to analyze the feature request against existing architecture
   - Review Memory Bank to understand system context and constraints
   - Create a feature specification document

3. **Architecture Planning**
   - Architect mode evaluates impact on existing architecture
   - Identify components that need modification
   - Document design decisions and update architecture.md if needed

4. **Task Breakdown**
   - Break down the feature into specific implementation tasks
   - Document dependencies between tasks
   - Estimate complexity and effort

5. **Architecture PR Review**
   ```bash
   git add .
   git commit -m "arch: Feature specification and architecture plan for [feature]"
   git push -u origin architecture/feature-name
   # Create PR through GitHub/GitLab interface for architecture review
   ```
   - Team reviews the architecture plan and proposed solution
   - Experts evaluate the approach before implementation begins
   - Prevents inefficient solutions and reduces potential rework
   - Merge the approved architecture PR before proceeding to implementation

## 2. Feature Development Phase

**Branch**: feature/feature-name (from develop)
**Kilocode Mode**: Code, Debug
**Memory Bank Focus**: architecture.md, tech.md, context.md

### Workflow Steps:
1. **Branch Creation**
   ```bash
   git checkout develop
   git pull
   git checkout -b feature/feature-name
   # Optionally, you can create the feature branch directly from the architecture branch
   # git checkout architecture/feature-name
   # git checkout -b feature/feature-name
   ```

2. **Implementation**
   - Use Code mode for implementation tasks
   - Reference Memory Bank for architectural guidance
   - Commit regularly with descriptive messages:
     ```bash
     git add .
     git commit -m "feat: Implement specific component"
     ```

3. **Testing & Debugging**
   - Switch to Debug mode for troubleshooting issues
   - Use Memory Bank to understand expected behavior
   - Add unit and integration tests
   - Commit test implementations:
     ```bash
     git add .
     git commit -m "test: Add tests for new feature"
     ```

4. **Memory Bank Updates**
   - Update context.md with new feature details
   - If the feature introduces architectural changes, update architecture.md
   - If implementing a repetitive task, add to tasks.md

## 3. Code Review Phase

**Branch**: feature/feature-name
**Kilocode Mode**: Code, Ask
**Memory Bank Focus**: All relevant files

### Workflow Steps:
1. **Self-Review**
   - Use Code mode to review implementation
   - Verify against Memory Bank architecture guidelines
   - Make final adjustments

2. **Pull Request Creation**
   ```bash
   git push -u origin feature/feature-name
   # Create PR through GitHub/GitLab interface
   ```

3. **Address Feedback**
   - Use Ask mode to clarify reviewer questions
   - Use Code mode to implement requested changes
   - Commit changes:
     ```bash
     git add .
     git commit -m "refactor: Address PR feedback"
     git push
     ```

## 4. Integration Phase

**Branch**: develop
**Kilocode Mode**: Debug, Orchestrator
**Memory Bank Focus**: context.md, tasks.md

### Workflow Steps:
1. **Merge to Develop**
   ```bash
   git checkout develop
   git pull
   git merge --no-ff feature/feature-name
   git push
   ```

2. **Integration Testing**
   - Use Debug mode to identify and fix integration issues
   - Verify feature works with other components

3. **Memory Bank Update**
   - Update context.md with current project state
   - Document any integration challenges in tasks.md

## 5. Release Phase

**Branch**: release/version
**Kilocode Mode**: Orchestrator, Debug
**Memory Bank Focus**: All files

### Workflow Steps:
1. **Create Release Branch**
   ```bash
   git checkout develop
   git checkout -b release/v1.x.0
   ```

2. **Release Preparation**
   - Use Orchestrator mode to coordinate final checks
   - Fix any release-specific issues
   - Update version numbers and documentation

3. **Final Testing**
   - Use Debug mode for final verification
   - Address any last-minute issues

4. **Merge to Main and Develop**
   ```bash
   git checkout main
   git merge --no-ff release/v1.x.0
   git tag -a v1.x.0 -m "Release v1.x.0"
   git push --follow-tags
   
   git checkout develop
   git merge --no-ff release/v1.x.0
   git push
   ```

5. **Complete Memory Bank Update**
   - Update all Memory Bank files to reflect the new release
   - Document new features in product.md
   - Update context.md with next steps

## Mode-Specific Responsibilities

### Architect Mode
- System design and architecture planning
- Evaluating feature impact on existing architecture
- Documenting architectural decisions
- Updating architecture.md

### Code Mode
- Implementation of new features
- Code refactoring
- Test implementation
- Documentation updates

### Debug Mode
- Troubleshooting issues
- Integration testing
- Performance optimization
- Security testing

### Ask Mode
- Clarifying requirements
- Answering technical questions
- Explaining implementation decisions
- Supporting code reviews

### Orchestrator Mode
- Coordinating complex tasks
- Managing release processes
- Ensuring all steps are completed
- Delegating to specialized modes when needed

## Memory Bank Integration

1. **Before Starting a Feature**:
   - Review all Memory Bank files to understand current context
   - Verify architecture.md for design patterns and constraints

2. **During Development**:
   - Reference tech.md for technology stack details
   - Use tasks.md for guidance on repetitive tasks

3. **After Completing a Feature**:
   - Update context.md with new feature details
   - Add to tasks.md if implementing a repetitive pattern
   - Suggest Memory Bank updates for significant changes

## Implementation Example

Let's illustrate with an example of adding a new loan purpose:

1. **Planning (Architect Mode)**:
   - Review Memory Bank to understand current loan purposes
   - Design changes needed to support new loan purpose
   - Document in a feature specification

2. **Development (Code Mode)**:
   - Create branch: `feature/add-personal-loan-purpose`
   - Add new enum value in `src/Application/Common/Enums/LoanPurpose.cs`
   - Update product selection logic in services
   - Implement tests

3. **Review & Integration**:
   - Create PR for review
   - Merge to develop after approval
   - Update Memory Bank context.md with new loan purpose

4. **Release**:
   - Include in next release branch
   - Update Memory Bank product.md with new capability

## Workflow Diagram

```
Feature Request → Architect Mode (Planning) → Code Mode (Implementation) → Debug Mode (Testing)
       ↓                  ↓                           ↓                          ↓
Memory Bank ←→ GitFlow (feature branch) ←→ Code Review ←→ GitFlow (develop) ←→ Release
```

This integrated workflow leverages the strengths of each component:
- Kilocode modes for specialized tasks
- Memory Bank for knowledge continuity
- GitFlow for structured version control
- Architecture PR reviews to ensure solution quality before implementation

## Benefits of Architecture PR Reviews

1. **Early Expert Validation**
   - Solutions are evaluated by team experts before implementation begins
   - Architectural flaws are caught early when they're easier to fix
   - Team alignment on approach before investing in implementation

2. **Token Efficiency**
   - Prevents inefficient implementations that might require extensive rework
   - Reduces token usage by ensuring the right solution is implemented the first time
   - More efficient use of Kilocode modes by focusing on validated approaches

3. **Knowledge Sharing**
   - Architecture reviews spread knowledge across the team
   - Junior developers learn from feedback on architectural decisions
   - Creates a record of architectural decisions and their rationales

4. **Quality Improvement**
   - Enforces architectural consistency across features
   - Ensures adherence to project patterns and best practices
   - Reduces technical debt by preventing architectural shortcuts

## Benefits of This Integrated Approach

1. **Improved Knowledge Retention**
   - Memory Bank ensures knowledge is preserved between sessions
   - Reduces ramp-up time for developers switching between features

2. **Specialized Expertise**
   - Each Kilocode mode provides specialized capabilities for different phases
   - Ensures the right approach is used for each task

3. **Structured Development Process**
   - GitFlow provides a clear branching strategy
   - Predictable process for feature development through release

4. **Reduced Technical Debt**
   - Architecture mode ensures proper design before implementation
   - Memory Bank updates keep documentation current with code

5. **Efficient Collaboration**
   - Clear process for code reviews and feedback
   - Shared understanding through Memory Bank documentation