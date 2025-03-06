# Husky and Commitlint Configuration

This document provides an explanation of the **Husky** and **CommitLint** configurations used in the project. These tools enforce consistent commit messages and ensure code quality before commits.

## CommitLint Configuration

### **File: `commitlint.config.js`**

```javascript
export default {
  extends: ["@commitlint/config-conventional"],
};
```

### **Explanation:**

| Option                                         | Description                                                                                          |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `extends: ['@commitlint/config-conventional']` | Enforces conventional commit message rules, ensuring better commit history and changelog generation. |

## Husky Hooks

### File: `.husky/commit-msg`

```sh
npx --no-install commitlint --edit "$1"
```

### Explanation

| Command                                   | Description                                                                           |
| ----------------------------------------- | ------------------------------------------------------------------------------------- |
| `npx --no-install commitlint --edit "$1"` | Runs CommitLint to validate the commit message format before the commit is finalized. |

## Pre-commit Hook

### File: `.husky/pre-commit`

```sh
npm run lint && npm run format
```

### Explanation

| Command          | Description                                               |
| ---------------- | --------------------------------------------------------- |
| `npm run lint`   | Runs the project's linter to check for code style errors. |
| `npm run format` | Ensures code is formatted correctly before committing.    |

## Why Use Husky and CommitLint?

1. **CommitLint** enforces structured commit messages, improving project history readability.
2. **Husky** automates code quality checks before commits, ensuring a clean and standardized codebase.
3. The **pre-commit** hook prevents poorly formatted or incorrect code from being committed.

## Notes

- **Husky hooks** ensure that all commits meet quality standards before being accepted.
- **CommitLint** helps enforce meaningful commit messages, improving project documentation and collaboration.
- Modify the **pre-commit** hook according to your project’s requirements (e.g., running tests, checking types).

This setup ensures a clean, maintainable, and professional development workflow.
