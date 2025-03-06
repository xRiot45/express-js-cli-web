# Prettier Configuration

This document explains the configuration settings for **Prettier**, a popular code formatter used to maintain consistent code style across projects.

## Configuration Settings

The `.prettierrc` file includes the following options:

| Option        | Description                                                             | Default |
| ------------- | ----------------------------------------------------------------------- | ------- |
| `singleQuote` | Enforces the use of single quotes (`'`) instead of double quotes (`"`). | `true`  |
| `semi`        | Ensures that semicolons (`;`) are required at the end of statements.    | `true`  |

## Recommended Additional Settings

For better development experience, the following configurations are recommended:

| Option           | Description                                                         | Recommended Value |
| ---------------- | ------------------------------------------------------------------- | ----------------- |
| `trailingComma`  | Adds trailing commas where valid in ES5 (e.g., objects, arrays).    | `"es5"`           |
| `tabWidth`       | Specifies the number of spaces per indentation level.               | `2`               |
| `useTabs`        | Uses tabs instead of spaces for indentation.                        | `false`           |
| `bracketSpacing` | Adds spaces inside object brackets (`{ foo: bar }` vs `{foo:bar}`). | `true`            |
| `arrowParens`    | Always include parentheses around arrow function arguments.         | `"always"`        |
| `printWidth`     | Specifies the line length before Prettier wraps code.               | `80`              |
| `endOfLine`      | Ensures consistency in line endings across different OS.            | `"lf"`            |

## Example `.prettierrc` File

```json
{
  "singleQuote": true,
  "semi": true,
  "trailingComma": "es5",
  "tabWidth": 2,
  "useTabs": false,
  "bracketSpacing": true,
  "arrowParens": "always",
  "printWidth": 80,
  "endOfLine": "lf"
}
```

## Notes

- These settings help maintain a clean and readable codebase.
- The recommended settings ensure compatibility across different development environments.
- Modify the configurations based on your team’s preferences and project requirements.

This configuration ensures a **consistent** and **professional** coding style throughout the project.
