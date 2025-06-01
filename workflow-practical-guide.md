# Practical Guide: Implementing the Integrated Workflow

This document provides practical steps and commands for implementing the integrated workflow that combines Kilocode modes, Memory Bank, and GitFlow for feature development in any software project.

## Quick Reference

| Phase | Kilocode Mode | GitFlow Branch | Memory Bank Focus |
|-------|--------------|----------------|-------------------|
| Planning | Architect | architecture/feature-name | brief.md, product.md, architecture.md |
| Development | Code, Debug | feature/feature-name | architecture.md, tech.md |
| Review | Code, Ask | feature/feature-name | All relevant files |
| Integration | Debug, Orchestrator | develop | context.md, tasks.md |
| Release | Orchestrator, Debug | release/version | All files |

## Detailed Steps

### 1. Feature Planning

1. **Create Architecture Branch**
   ```bash
   git checkout develop
   git pull
   git checkout -b architecture/feature-name
   ```

2. **Switch to Architect Mode**
   ```
   # In Kilocode
   /mode architect
   ```

3. **Review Memory Bank**
   ```
   # Request Memory Bank review
   Please help me understand the current architecture for implementing [feature]
   ```

4. **Create Feature Specification**
   ```
   # Request feature specification
   Please help me create a feature specification for [feature description]
   ```

5. **Update Architecture (if needed)**
   ```
   # Request architecture update
   Please update the Memory Bank architecture.md to reflect the changes needed for [feature]
   ```

6. **Commit Architecture Plan**
   ```bash
   # Create a markdown file with the architecture plan
   git add architecture-plan.md
   git commit -m "arch: Feature specification and architecture plan for [feature]"
   ```

7. **Create Architecture PR**
   ```bash
   git push -u origin architecture/feature-name
   # Create PR through GitHub/GitLab interface for architecture review
   ```

8. **Address Architecture Feedback**
   ```
   # In Kilocode
   /mode ask
   
   # Request help with feedback
   Can you help me address the feedback on the architecture plan for [feature]?
   ```

9. **Update and Merge Architecture PR**
   ```bash
   git add .
   git commit -m "arch: Address feedback on architecture plan"
   git push
   # Merge PR through GitHub/GitLab interface after approval
   ```

### 2. Feature Development

1. **Create Feature Branch**
   ```bash
   git checkout develop
   git pull
   git checkout -b feature/feature-name
   
   # Alternatively, create feature branch from approved architecture branch
   git checkout architecture/feature-name
   git checkout -b feature/feature-name
   ```

2. **Switch to Code Mode**
   ```
   # In Kilocode
   /mode code
   ```

3. **Implement Feature**
   ```
   # Request implementation help
   Please help me implement [specific component] according to the feature specification
   ```

4. **Commit Changes**
   ```bash
   git add .
   git commit -m "feat: Implement [specific component]"
   ```

5. **Switch to Debug Mode for Testing**
   ```
   # In Kilocode
   /mode debug
   ```

6. **Implement Tests**
   ```
   # Request test implementation
   Please help me write tests for [specific component]
   ```

7. **Commit Tests**
   ```bash
   git add .
   git commit -m "test: Add tests for [specific component]"
   ```

8. **Update Memory Bank**
   ```
   # Request Memory Bank update
   Please update the Memory Bank context.md with details about [feature]
   ```

### 3. Code Review

1. **Self-Review with Code Mode**
   ```
   # In Kilocode
   /mode code
   
   # Request code review
   Please review my implementation of [feature]
   ```

2. **Push Branch and Create PR**
   ```bash
   git push -u origin feature/feature-name
   # Create PR through GitHub/GitLab interface
   ```

3. **Address Feedback with Ask Mode**
   ```
   # In Kilocode
   /mode ask
   
   # Request clarification
   Can you explain what [reviewer comment] means and how I should address it?
   ```

4. **Implement Changes and Push**
   ```bash
   git add .
   git commit -m "refactor: Address PR feedback"
   git push
   ```

### 4. Integration

1. **Merge to Develop**
   ```bash
   git checkout develop
   git pull
   git merge --no-ff feature/feature-name
   git push
   ```

2. **Switch to Debug Mode for Integration Testing**
   ```
   # In Kilocode
   /mode debug
   
   # Request integration testing
   Please help me test if [feature] integrates properly with the existing system
   ```

3. **Update Memory Bank Context**
   ```
   # Request Memory Bank update
   Please update the Memory Bank context.md with the current project state after integrating [feature]
   ```

### 5. Release

1. **Create Release Branch**
   ```bash
   git checkout develop
   git checkout -b release/v1.x.0
   ```

2. **Switch to Orchestrator Mode**
   ```
   # In Kilocode
   /mode orchestrator
   
   # Request release coordination
   Please help coordinate the release process for version v1.x.0 including [feature]
   ```

3. **Final Testing with Debug Mode**
   ```
   # In Kilocode
   /mode debug
   
   # Request final verification
   Please help verify that all features in release v1.x.0 are working correctly
   ```

4. **Merge to Main and Tag**
   ```bash
   git checkout main
   git merge --no-ff release/v1.x.0
   git tag -a v1.x.0 -m "Release v1.x.0"
   git push --follow-tags
   ```

5. **Merge Back to Develop**
   ```bash
   git checkout develop
   git merge --no-ff release/v1.x.0
   git push
   ```

6. **Complete Memory Bank Update**
   ```
   # Request comprehensive Memory Bank update
   Please update all Memory Bank files to reflect the new release v1.x.0
   ```

## Memory Bank Update Commands

### Update Context
```
# Request context update
Please update the Memory Bank context.md with information about [specific change or feature]
```

### Update Architecture
```
# Request architecture update
Please update the Memory Bank architecture.md to reflect [architectural change]
```

### Add Task
```
# Request task addition
Please add a task to the Memory Bank tasks.md for [repetitive task]
```

### Complete Update
```
# Request complete update
Please update all Memory Bank files to reflect the current state of the project
```

## Tips for Effective Workflow

1. **Start Each Session with Memory Bank Review**
   - Always begin by reviewing the Memory Bank to understand the current context
   - Look for recent changes in context.md

2. **Use the Right Mode for Each Task**
   - Architect mode for design and planning
   - Code mode for implementation
   - Debug mode for testing and troubleshooting
   - Ask mode for clarification and explanation
   - Orchestrator mode for coordination and release management

3. **Keep Memory Bank Updated**
   - Update context.md after significant changes
   - Add repetitive tasks to tasks.md
   - Update architecture.md when making architectural changes

4. **Follow GitFlow Strictly**
   - Always branch from develop for features
   - Use --no-ff when merging to preserve history
   - Tag releases properly

5. **Commit Best Practices**
   - Use conventional commit messages (feat, fix, docs, style, refactor, test, chore)
   - Keep commits focused on single changes
   - Write descriptive commit messages

## Example Workflow for Adding a New Feature

### 1. Planning
```bash
# Create architecture branch
git checkout develop
git pull
git checkout -b architecture/add-new-feature
```

```
/mode architect

Please help me understand the current architecture for implementing a new feature.

Please create a feature specification for adding the new feature to the system.
```

```bash
# Create architecture plan document
touch feature-architecture.md
# Edit the file with the architecture plan
git add feature-architecture.md
git commit -m "arch: Architecture plan for new feature"
git push -u origin architecture/add-new-feature
# Create PR for architecture review
```

```
# After PR approval and merge
git checkout develop
git pull
```

### 2. Development
```bash
git checkout develop
git pull
git checkout -b feature/add-new-feature
```

```
/mode code

Please help me implement the new feature according to the architecture plan.
```

```bash
git add .
git commit -m "feat: Implement core functionality for new feature"
```

```
/mode debug

Please help me write tests for the new feature implementation.
```

```bash
git add .
git commit -m "test: Add tests for new feature"
```

### 3. Review and Integration
```
/mode code

Please review my implementation of the new feature.
```

```bash
git push -u origin feature/add-new-feature
# Create PR through GitHub/GitLab interface
```

```
/mode ask

Can you explain how to address the feedback about performance optimization?
```

```bash
git add .
git commit -m "refactor: Address PR feedback for performance optimization"
git push
```

### 4. Memory Bank Update
```
Please update the Memory Bank context.md with details about the new feature.
```

This practical guide provides a step-by-step reference for implementing the integrated workflow in day-to-day development activities.