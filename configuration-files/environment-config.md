# Environment Configuration

This documentation provides an overview of the environment variables used in the application. The `.env` file is used to configure different environments: **Development**, **Production**, and **Test**.

## Environment Variables

### 1. Application Settings

| Variable   | Description                                                | Example                 |
| ---------- | ---------------------------------------------------------- | ----------------------- |
| `APP_URL`  | The base URL of the application                            | `http://localhost:3000` |
| `APP_NAME` | The name of the application                                | `MyApp`                 |
| `APP_PORT` | The port where the application runs                        | `3000`                  |
| `NODE_ENV` | The environment mode (`development`, `production`, `test`) | `development`           |

### 2. Database Configuration

| Variable            | Description                                                    | Example       |
| ------------------- | -------------------------------------------------------------- | ------------- |
| `DIALECT`           | The database dialect using Sequelize ORM (`mysql`, `postgres`) | `mysql`       |
| `DATABASE_HOST`     | The database host                                              | `localhost`   |
| `DATABASE_PORT`     | The database port                                              | `3306`        |
| `DATABASE_USERNAME` | The database username                                          | `root`        |
| `DATABASE_PASSWORD` | The database password                                          | `password`    |
| `DATABASE_NAME`     | The name of the database                                       | `my_database` |

## Environment-Specific Configurations

### Development Environment

Used for local development and debugging.

```env
APP_URL=http://localhost:3000
APP_NAME=
APP_PORT=3000
NODE_ENV=development

DIALECT=
DATABASE_HOST=
DATABASE_PORT=
DATABASE_USERNAME=
DATABASE_PASSWORD=
DATABASE_NAME=
```

### Production Environment

Used for the live production system.

```env
APP_URL=http://localhost:3000
APP_NAME=
APP_PORT=3000
NODE_ENV=production

DIALECT=
DATABASE_HOST=
DATABASE_PORT=
DATABASE_USERNAME=
DATABASE_PASSWORD=
DATABASE_NAME=
```

### Test Environment

Used for running automated tests.

```env
APP_URL=http://localhost:3000
APP_NAME=
APP_PORT=3000
NODE_ENV=test

DIALECT=
DATABASE_HOST=
DATABASE_PORT=
DATABASE_USERNAME=
DATABASE_PASSWORD=
DATABASE_NAME=
```

## Notes

- Ensure that each environment has its respective values configured properly.
- Keep sensitive information like `DATABASE_PASSWORD` secret and do not expose it in public repositories.
- The `NODE_ENV` variable determines the execution mode of the application.
- Modify values according to your specific project requirements.
