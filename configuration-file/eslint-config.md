# ESLint Configuration

This document explains the **eslint.config.js** file for both **JavaScript** and **TypeScript** projects. The configuration ensures code quality, best practices, and consistency across the codebase.

## ESLint Configuration for JavaScript

### File: `eslint.config.js` (JavaScript)

```javascript
import globals from "globals";
import js from "@eslint/js";
import pluginJs from "@eslint/js";

/** @type {import('eslint').Linter.Config[]} */
export default [
  { files: ["**/*.{js,mjs,cjs,ts}"] },
  {
    languageOptions: {
      ecmaVersion: "latest",
      sourceType: "module",
      globals: { ...globals.browser, ...globals.node },
    },
    rules: {
      "no-console": "warn",
      "no-unused-vars": ["error", { argsIgnorePattern: "^_" }],
      eqeqeq: ["error", "always"],
      curly: ["error", "all"],
      "no-var": "error",
      "prefer-const": "error",
      "arrow-body-style": ["error", "as-needed"],
      "object-shorthand": ["error", "always"],
    },
  },
  {
    ignores: ["node_modules/", "dist/", "test/", "coverage/"],
  },
  {
    files: ["**/*.js", "**/*.ts"],
    rules: {
      "arrow-body-style": "off",
    },
  },
  js.configs.recommended,
  pluginJs.configs.recommended,
];
```

### Explanation of the Configuration

| Option                          | Description                                                                           |
| ------------------------------- | ------------------------------------------------------------------------------------- |
| `languageOptions.ecmaVersion`   | Uses the latest ECMAScript version.                                                   |
| `languageOptions.sourceType`    | Treats the code as ES modules.                                                        |
| `globals.browser, globals.node` | Supports browser and Node.js global variables.                                        |
| `no-console: warn`              | Warns about console statements (useful for debugging but not in production).          |
| `no-unused-vars: error`         | Throws an error if there are unused variables (ignoring variables prefixed with `_`). |
| `eqeqeq: always`                | Enforces strict equality (`===` and `!==`) for comparisons.                           |
| `curly: all`                    | Requires curly braces for all control statements (if, else, loops).                   |
| `no-var: error`                 | Prevents the use of `var`, enforcing `let` or `const` instead.                        |
| `prefer-const: error`           | Encourages the use of `const` when variables are not reassigned.                      |
| `arrow-body-style: as-needed`   | Allows omitting `{}` in arrow functions when unnecessary.                             |
| `object-shorthand: always`      | Enforces object shorthand syntax (`{ foo }` instead of `{ foo: foo }`).               |

## ESLint Configuration for TypeScript

### File: `eslint.config.js` (TypeScript)

```javascript
import tsEslintPlugin from "@typescript-eslint/eslint-plugin";
import eslintPluginComments from "eslint-plugin-eslint-comments";
import eslintPluginImport from "eslint-plugin-import";
import eslintPluginPrettier from "eslint-plugin-prettier";
import eslintPluginSort from "eslint-plugin-simple-import-sort";
import eslintPluginUnusedImports from "eslint-plugin-unused-imports";
import globals from "globals";
import jsPlugin from "@eslint/js";
import tsEslint from "typescript-eslint";

/** @type {import('eslint').Linter.Config[]} */
export default [
  {
    plugins: {
      "@typescript-eslint": tsEslintPlugin,
      prettier: eslintPluginPrettier,
      import: eslintPluginImport,
      "unused-imports": eslintPluginUnusedImports,
      "simple-import-sort": eslintPluginSort,
      "eslint-comments": eslintPluginComments,
    },
    rules: {
      "prettier/prettier": "error",
      "unused-imports/no-unused-imports": "error",
      "@typescript-eslint/no-unused-vars": [
        "warn",
        { argsIgnorePattern: "^_" },
      ],
      "@typescript-eslint/no-explicit-any": "error",
      "@typescript-eslint/no-unsafe-assignment": "error",
      "@typescript-eslint/no-unsafe-call": "error",
      "eslint-comments/no-unused-disable": "warn",
      "arrow-body-style": "off",
    },
  },
  { files: ["**/*.{js,mjs,cjs,ts}"] },
  {
    languageOptions: {
      globals: {
        ...globals.browser,
        ...globals.node,
      },
    },
  },
  {
    ignores: ["node_modules/", "dist/", "test/", "coverage/"],
  },
  jsPlugin.configs.recommended,
  ...tsEslint.configs.recommended,
];
```

### Explanation of the Configuration

| Option                                    | Description                                                    |
| ----------------------------------------- | -------------------------------------------------------------- |
| `@typescript-eslint/eslint-plugin`        | Provides TypeScript-specific linting rules.                    |
| `eslint-plugin-prettier`                  | Ensures code formatting follows Prettier rules.                |
| `eslint-plugin-import`                    | Enforces best practices for ES module imports.                 |
| `eslint-plugin-simple-import-sort`        | Automatically sorts imports.                                   |
| `eslint-plugin-unused-imports`            | Removes unused imports.                                        |
| `eslint-plugin-eslint-comments`           | Prevents unused ESLint disable comments.                       |
| `@typescript-eslint/no-unused-vars`       | Warns about unused variables (except those prefixed with `_`). |
| `@typescript-eslint/no-explicit-any`      | Prevents the use of `any` type in TypeScript.                  |
| `@typescript-eslint/no-unsafe-assignment` | Avoids assigning `any` type values without proper type safety. |
| `@typescript-eslint/no-unsafe-call`       | Prevents unsafe function calls when types are unknown.         |
| `eslint-comments/no-unused-disable`       | Warns when `eslint-disable` comments are no longer needed.     |

## Ignored Files and Directories

Both JavaScript and TypeScript configurations ignore the following directories:

- `node_modules/`
- `dist/`
- `test/`
- `coverage/`

## Notes

- The **JavaScript** ESLint config enforces modern JavaScript best practices.
- The **TypeScript** ESLint config adds additional rules to maintain strong type safety.
- Both configurations ensure consistent, error-free, and maintainable code.
- Integrating **Prettier** ensures that formatting rules are automatically enforced.

This setup enhances code quality, prevents bugs, and maintains a clean development workflow.
