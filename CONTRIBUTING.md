# Contributing to Automaker

Thank you for your interest in contributing to Automaker! This document provides guidelines and information for contributors.

## Table of Contents

- [Community](#community)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Project Structure](#project-structure)
- [Making Changes](#making-changes)
- [Commit Guidelines](#commit-guidelines)
- [Pull Request Process](#pull-request-process)
- [Code Style](#code-style)
- [Testing](#testing)
- [Reporting Issues](#reporting-issues)

## Community

**Join our Discord community:** [discord.gg/JUDWZDN3VT](https://discord.gg/JUDWZDN3VT)

> **Important:** Before working on new features, please discuss your ideas on Discord first. This helps ensure your contribution aligns with the project direction and prevents duplicate work.

## Getting Started

1. **Join the [Discord](https://discord.gg/JUDWZDN3VT)** and introduce yourself
2. **Fork the repository** on GitHub
3. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR-USERNAME/automaker.git
   cd automaker
   ```
4. **Add the upstream remote**:
   ```bash
   git remote add upstream https://github.com/AutoMaker-Org/automaker.git
   ```
5. **Install dependencies**:
   ```bash
   npm install
   ```

## Development Setup

### Prerequisites

- Node.js 18+
- npm 9+
- Git

### Running Locally

```bash
# Build shared packages first
npm run build:packages

# Run in development mode (interactive selector)
npm run dev

# Or run specific modes:
npm run dev:electron    # Desktop app
npm run dev:web         # Web browser
npm run dev:server      # Server only
npm run dev:full        # Server + Web UI
```

## Project Structure

Automaker is a monorepo using npm workspaces:

```
automaker/
├── apps/
│   ├── server/          # Express backend API
│   └── ui/              # React frontend (Vite + Electron)
├── libs/
│   ├── types/           # Shared TypeScript types
│   ├── utils/           # Shared utilities
│   ├── prompts/         # AI prompt templates
│   ├── platform/        # Platform detection utilities
│   ├── model-resolver/  # AI model selection logic
│   ├── dependency-resolver/  # Feature dependency management
│   └── git-utils/       # Git operations utilities
├── docs/                # Documentation
├── scripts/             # Build and utility scripts
└── test/                # Integration tests
```

### Key Technologies

- **Frontend**: React, Vite, TailwindCSS, Zustand, TanStack Router
- **Backend**: Express, TypeScript
- **Desktop**: Electron
- **AI**: Claude Agent SDK

## Making Changes

1. **Discuss on Discord first** - For new features, share your idea in the appropriate channel before starting work

2. **Create a branch** from `main`:

   ```bash
   git fetch upstream
   git checkout -b feature/your-feature-name upstream/main
   ```

3. **Make your changes** following the [code style guidelines](#code-style)

4. **Write tests** for new functionality (highly encouraged)

5. **Test your changes**:

   ```bash
   npm run test
   npm run lint
   ```

6. **Commit your changes** following the [commit guidelines](#commit-guidelines)

## Commit Guidelines

We follow [Conventional Commits](https://www.conventionalcommits.org/) for clear and consistent commit history.

### Format

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

### Types

| Type       | Description                                       |
| ---------- | ------------------------------------------------- |
| `feat`     | New feature                                       |
| `fix`      | Bug fix                                           |
| `docs`     | Documentation changes                             |
| `style`    | Code style changes (formatting, no logic changes) |
| `refactor` | Code refactoring (no feature or fix)              |
| `perf`     | Performance improvements                          |
| `test`     | Adding or updating tests                          |
| `chore`    | Maintenance tasks, dependency updates             |
| `ci`       | CI/CD changes                                     |

### Examples

```
feat(ui): add dark mode toggle to settings
fix(server): prevent command injection in update routes
docs: add contributing guidelines
refactor(utils): extract shared helper function
```

## Pull Request Process

1. **Discuss first** - Ensure you've discussed the change on Discord (for features)

2. **Update your branch** with the latest upstream changes:

   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

3. **Push your branch** to your fork:

   ```bash
   git push origin feature/your-feature-name
   ```

4. **Open a Pull Request** against `main` branch and fill out the PR template

5. **Wait for review** - All PRs require approval from a maintainer

6. **Address AI reviewer comments** - All comments from automated reviewers (CodeRabbit, Gemini, etc.) must be resolved before merge. For each comment, either apply the fix or reply with a clear rationale why it doesn't apply.

7. **Address review feedback** promptly

8. **Ensure CI passes** before requesting final review

### PR Requirements

- All tests must pass
- Code must be formatted (Prettier)
- No linting errors
- Commits follow conventional commit format
- PR description clearly explains the changes
- Tests for new functionality are highly encouraged

## Code Style

### General Guidelines

- Use TypeScript for all new code
- Follow existing patterns in the codebase
- Keep functions small and focused
- Write self-documenting code with clear names
- Add comments only for complex logic

### Formatting

We use Prettier for code formatting. The pre-commit hook will automatically format staged files.

### TypeScript

- Use strict type checking
- Avoid `any` types when possible
- Export types from `libs/types` for shared interfaces

### React Components

- Use functional components with hooks
- Keep components focused on a single responsibility
- Use Zustand for global state management
- Follow the existing component structure in `apps/ui/src/components`

## Testing

Tests for new functionality are highly encouraged.

### Running Tests

```bash
# Run all tests
npm run test

# Run tests in watch mode
npm run test:watch
```

### Writing Tests

- Place tests next to the code they test (`*.test.ts` or `*.spec.ts`)
- Use descriptive test names
- Test both success and error cases
- Mock external dependencies

## Reporting Issues

### Bug Reports

When reporting bugs, please include:

1. **Description**: Clear description of the issue
2. **Steps to Reproduce**: Detailed steps to reproduce the bug
3. **Expected Behavior**: What you expected to happen
4. **Actual Behavior**: What actually happened
5. **Environment**: OS, Node version, browser (if applicable)
6. **Screenshots/Logs**: If applicable

### Feature Requests

For feature requests:

1. **Discuss on Discord first** in the appropriate channel
2. If agreed upon, open an issue with:
   - Problem description
   - Proposed solution
   - Any alternatives considered

## Questions?

Join our [Discord community](https://discord.gg/JUDWZDN3VT) - we're happy to help!

Thank you for contributing to Automaker!
