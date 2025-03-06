# Quick Start Guide

Follow these steps to set up and run the project locally on your machine.

## Prerequisites

Before getting started, ensure you have the following installed:

- **[Git](https://git-scm.com/)** - Version control system for managing code.
- **[Node.js](https://nodejs.org/en)** - JavaScript runtime required to run the project.
- **[npm](https://www.npmjs.com/)** - Node Package Manager to handle dependencies.

To verify if they are installed, run the following commands in your terminal:

```bash
$ git --version

$ node -v

$ npm -v

```

---

## Install Express JS CLI Tool

Run the following command to install the CLI globally:

```bash
$ npm install -g express-api-cli-tool
```

To verify if Express JS CLI is installed, run the following command in your terminal:

```bash
$ express -h
```

If your terminal appears like this when you run the `express -h` command, it means that Express JS CLI is already installed on your device.

```bash
Usage: express [options] [command]

Options:
  -v, --version                           Display the current version of express-cli
  -i, --info                              Display information about express-cli
  -h, --help                              display help for command

Commands:
  new       <project-name>                Create a new Express.js API project
  generate  <schematic> <file-name>       Generate a new file based on a schematic
  update                                  Update express-cli to the latest version

Schematics:
  controller        Generate a new controller file
  service           Generate a new service file
  route             Generate a new route file
  repository        Generate a new repository file
  validation        Generate a new validation file
  model             Generate a new model file
  interface         Generate a new interface file (if using TypeScript)
  types             Generate a new types file (if using TypeScript)
  resources         Generate a new resources file (controller, service, route, repository, validation, model, test, interface (If using typescript))
  config            Generate a new config file
  middleware        Generate a new middleware file
  util              Generate a new util file
  test              Generate a new test file
```

---

## Create new project

```bash
$ express new <project-name>
```

> All dependencies will be automatically installed after the project is created, so you don't need to run `npm install` manually.

---

## Follow the instructions

When running the above command, you will be asked to choose several options:

- **Select language** : JavaScript / TypeScript
- **Select database** : MySQL / PostgreSQL
- **Select testing** : Jest / Mocha
- **Use Eslint for code linting?** : Y / n
- **Use Husky and Commit lint for commit linting?** : Y / n
- **Initialize Git repository?** : Y / n

---

## Running your project

```bash
# Change directory to your project
$ cd <your-project>

# Format the code before running the project (recommended)
$ npm run format

# Running your project
$ npm run dev
```

---

## Verify the Setup

To ensure the server is running properly, open a browser and access:

```
http://localhost:3000
```

Or run the following command in the terminal:

```bash
$ curl http://localhost:3000
```

If the server is running properly, you will see a response from your server.
