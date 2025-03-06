# Model Module

## Description

This module defines a database model using Sequelize, a promise-based Node.js ORM for SQL databases. The model serves as a blueprint for interacting with the database, enabling structured queries and operations. The implementation is compatible with both JavaScript and TypeScript.

---

## Code Implementation

Below is the code for defining a model code.

### Structure Code

```javascript
import sequelize from "../configs/sequelize.config.js";

const testModel = sequelize.define("test", {
  // Define your model attributes here
});

export default testModel;
```

### Explanation

1. **Import `sequelize` configuration** → The Sequelize instance is imported from the configuration file to establish the database connection.
2. **Define the model using `sequelize.define()`**:
   - `'test'` → This is the name of the table in the database.
   - `{}` → Inside this object, you can define attributes (columns) and their data types.
3. **Export the model** → The model is exported so it can be used in controllers, services, or other parts of the application.

---

## Defining Model Attributes

Sequelize allows defining attributes with specific data types and constraints. Here’s an example of a complete model definition:

### Using sequelize.define

```javascript
import { DataTypes } from "sequelize";
import sequelize from "../configs/sequelize.config.js";

const testModel = sequelize.define(
  "test",
  {
    id: {
      type: DataTypes.INTEGER,
      primaryKey: true,
      autoIncrement: true,
      allowNull: false,
    },
    name: {
      type: DataTypes.STRING,
      allowNull: false,
    },
  },
  {
    timestamps: true,
  },
);

export default testModel;
```

#### Attribute Explanation

- **`id`** → A unique identifier for each record (auto-incremented primary key).
- **`name`** → A string field that cannot be null.
- **`timestamps`** → Timestamp fields that default to the current date and time.

### Extending model (Using TypeScript)

```javascript
import { Model, DataTypes } from "sequelize";
import sequelize from "../configs/sequelize.config";

interface TestAttributes {
  id?: number;
  name: string;
  createdAt?: Date;
  updatedAt?: Date;
}

class TestModel extends Model<TestAttributes> implements TestAttributes {
  public id!: number;
  public name!: string;
  public readonly createdAt!: Date;
  public readonly updatedAt!: Date;
}

TestModel.init(
  {
    id: {
      type: DataTypes.INTEGER,
      primaryKey: true,
      autoIncrement: true,
      allowNull: false,
    },
    name: {
      type: DataTypes.STRING,
      allowNull: false,
    },
  },
  {
    sequelize,
    modelName: "test",
    timestamps: true,
  },
);

export default TestModel;
```

#### Attribute Explanation

- **`id`** → A unique identifier for each record (auto-incremented primary key).
- **`name`** → A string field that cannot be null.
- **`sequelize`** → Sequelize instance used for model initialization
- **`modelName`** → Table name
- **`timestamps`** → Timestamp fields that default to the current date and time.

---

## How to Use

1. **Sync the model with the database inside the `connectToDatabase` function in the `src/configs/database.config.js` file.**

   ```javascript
   import testModel from "./models/test.model.js";
   import logger from "./logger.config.js";
   import sequelize from "./sequelize.config.js";

   export default async function connectToDatabase() {
     try {
       await sequelize.authenticate();
       logger.info(
         "Connection to the database has been established successfully.",
       );

       await testModel.sync({ alter: true }); // Sync Here
     } catch (error) {
       await sequelize.close();
       logger.error("Unable to connect to the database:", error);
     }
   }
   ```

2. **Perform CRUD operations**

   ```javascript
   // Create a new record
   await testModel.create({ name: "Example" });

   // Retrieve all records
   const data = await testModel.findAll();
   console.log(data);
   ```

---

## Conclusion

This model module helps in defining database tables using Sequelize, making database interactions easier and more structured. The TypeScript implementation offers better type safety and maintainability for larger applications.
