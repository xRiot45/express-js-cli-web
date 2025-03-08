# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## 📌 Changelog Categories

| Category          | Icon | Description                                                                                                              |
| ----------------- | ---- | ------------------------------------------------------------------------------------------------------------------------ |
| **Added**         | ✨   | New features added                                                                                                       |
| **Changed**       | 🔄   | Changes to existing features                                                                                             |
| **Deprecated**    | ⚠️   | Features that are deprecated and will be removed in the future                                                           |
| **Removed**       | ❌   | Removed feature                                                                                                          |
| **Fixed**         | 🛠    | Bug fixes                                                                                                                |
| **Security**      | 🔒   | Security-related changes                                                                                                 |
| **Performance**   | 🚀   | Changes that improve application performance, such as database query optimization or data processing speed improvements. |
| **Refactored**    | 🏗    | Changes in code structure without changing functionality (e.g. improving code readability or improving architecture).    |
| **Documentation** | 📚   | Changes or additions to project documentation.                                                                           |
| **UI/UX**         | 🎨   | Changes to the look or user experience.                                                                                  |
| **Build**         | 🏗    | Changes related to the build system or CI/CD (Continuous Integration / Deployment).                                      |
| **Dependencies**  | 📦   | Changes related to updating or removing external dependencies.                                                           |
| **Hotfix**        | 🔥   | Urgent fixes to critical bugs that affect production.                                                                    |
| **Configuration** | ⚙️   | Changes to system configuration, environment variables, or application settings.                                         |

---

## [v1.2.5] - 2025-03-07

### 🚀 Release Highlights

- This update enhances project transparency and security by adding a `SECURITY.md` file and refining the project metadata.

### 🔄 Changed

- Changing the homepage url link in `package.json`

### 🔒 Security

- Introduced `SECURITY.md` to provide guidelines on reporting vulnerabilities and maintaining project security.

### 📚 Documentation

- Added `SECURITY.md` with details on how to report security issues.

---

## [v1.2.4] - 2025-03-05

### 🚀 Release Highlights

- This update improves the user experience by adding a default template for the root endpoint (`/`) when generating a new Express.js project using the CLI.
- The default template includes a simple welcome message, making it easier for users to see an initial response without additional setup.
- Updated `README.md` to reflect the changes.

### ✨ Added

- The generated project now includes a default route (`/`) with a simple welcome message. This can be removed from `app.js` or `app.ts` if not needed.

### 📚 Documentation

- Updated `README.md` to describe the new default template behavior.

---

## [v1.2.3] - 2025-03-05

### 🚀 Release Highlights

- This version improves project metadata, making it easier for developers and users to track the project's repository and homepage.
- Enhancements ensure better traceability and transparency for the project.

### ⚙️ Configuration

- Added `repository` and `homepage` fields in `package.json` to provide direct links to the project documentation and source code.

---

## [v1.2.1] - 2025-03-04

### 🚀 Release Highlights

- Fixed a critical issue where users were unnecessarily prompted to select the test option again when creating a new file.
- This fix ensures a more seamless and efficient experience when generating files using the CLI.

### 🛠 Fixed

- Fixed an issue where users were prompted to select the test option again when trying to create a new file. This ensures a smoother CLI experience.

---

## [v1.2.0] - 2025-03-03

### 🚀 Release Highlights

- Introduced built-in testing features using Jest & Supertest, and Mocha & Chai, allowing users to test their API endpoints more easily.
- Added the `test` command, which helps in regenerating test files automatically for seamless testing setup.

### ✨ Added

- Implemented Jest & Supertest as the default testing framework for API testing.
- Added Mocha & Chai as alternative testing frameworks for API testing.
- Introduced the `test` command to automatically generate test files, making it easier for developers to maintain and update tests.
