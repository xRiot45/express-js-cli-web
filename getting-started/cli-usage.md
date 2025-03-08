# CLI Usage

### Display Help Information

To view the list of available commands and options, run:

```bash
$ express -h
```

**Output:**

```
Usage: express [options] [command]

Options:
  -v, --version                           Display the current version of express-cli
  -i, --info                              Display information about express-cli
  -h, --help                              Display help for command

Commands:
  new       <project-name>                Create a new Express.js API project
  generate  <schematic> <file-name>       Generate a new file based on a schematic
  update                                  Update express-cli to the latest version
```

### Display Express JS CLI Version

To showing Express JS CLI version, run command:

```bash
$ express -v
```

### Display Express JS CLI Info

To showing Express JS CLI info, run command:

```bash
$ express -i
```

### Update Express JS CLI

To update Express JS CLI to the latest version, run command:

```bash
$ express update
```

## Commands

### Create a New Express.js Project

To create a new Express.js API project, use:

```bash
$ express new my-project
```

> This will generate a new Express.js project with a pre-defined folder structure and all dependencies installed without you having to enter the `npm install` command again.

### Generate Files

You can generate different types of files using the `generate` command with the appropriate schematic.

**Syntax:**

```bash
$ express generate <schematic> <file-name>
```

### Schematics

- #### controller

  ```bash
  $ express generate controller user
  ```

  **Output:**

  - If the controller file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/controllers/user.controller.js
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/controllers/user.controller.js
    ```

- #### service

  ```bash
  $ express generate service user
  ```

  **Output:**

  - If the service file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/services/user.service.js
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/services/user.service.js
    ```

- #### route

  ```bash
  $ express generate route user
  ```

  **Output:**

  - If the route file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/routes/user.route.js
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/routes/user.route.js
    ```

- #### repository

  ```bash
  $ express generate repository user
  ```

  **Output:**

  - If the repository file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/repositories/user.repository.js
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/repositories/user.repository.js
    ```

- #### validation

  ```bash
  $ express generate validation user
  ```

  **Output:**

  - If the validation file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/validations/user.validation.js
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/validations/user.validation.js
    ```

- #### model

  ```bash
  $ express generate model user
  ```

  **Output:**

  - If the model file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/models/user.model.js
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/models/user.model.js
    ```

- #### interface (for TypeScript projects)

  ```bash
  $ express generate interface user
  ```

  **Output:**

  - If the interface file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/interfaces/user.interface.js
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/interfaces/user.interface.js
    ```
  - If you are using JavaScript language, the following message will appear.
    ```bash
    ✖ ERROR	Can't generate interface in JavaScript
    ```

- #### types (for TypeScript projects)

  ```bash
  $ express generate types global
  ```

  **Output:**

  - If the type file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/types/global.d.ts
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/types/global.d.ts
    ```
  - If you are using JavaScript language, the following message will appear.
    ```bash
    ✖ ERROR	Can't generate types in JavaScript
    ```

- #### resources

  ```bash
  $ express generate resources user
  ```

  **Output:**

  - If the resources file is successfully generated, the following message will appear:

    ```bash
    ✔ SUCCESS	 File generated: src/controllers/user.controller.js
    ✔ SUCCESS	 File generated: src/services/user.service.js
    ✔ SUCCESS	 File generated: src/routes/user.route.js
    ✔ SUCCESS	 File generated: src/validations/user.validation.js
    ✔ SUCCESS	 File generated: src/models/user.model.js
    ✔ SUCCESS	 File generated: src/repositories/user.repository.js
    ✔ SUCCESS	 File generated: test/user.test.js
    ```

  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR		 File already exists: src/controllers/user.controller.js
    ✖ ERROR		 File already exists: src/services/user.service.js
    ✖ ERROR		 File already exists: src/routes/user.route.js
    ✖ ERROR		 File already exists: src/validations/user.validation.js
    ✖ ERROR		 File already exists: src/models/user.model.js
    ✖ ERROR		 File already exists: src/repositories/user.repository.js
    ✖ ERROR		 File already exists: test/user.test.js
    ```

- #### config

  ```bash
  $ express generate config app
  ```

  **Output:**

  - If the config file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/configs/app.config.js/ts
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/configs/app.config.js/ts
    ```

- #### middleware

  ```bash
  $ express generate middleware auth
  ```

  **Output:**

  - If the middleware file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/middlewares/auth.middleware.js/ts
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/middlewares/auth.middleware.js/ts
    ```

- #### util

  ```bash
  $ express generate util format-date
  ```

  **Output:**

  - If the util file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: src/utils/format-date.util.js/ts
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: src/utils/format-date.util.js/ts
    ```

- #### test

  ```bash
  $ express generate test auth
  ```

  **Output:**

  - If the test file is successfully generated, the following message will appear:
    ```bash
    ✔ SUCCESS File generated: test/auth.test.js/ts
    ```
  - If it fails because the file already exists, the following message will appear:
    ```bash
    ✖ ERROR File already exists: test/auth.test.js/ts
    ```
