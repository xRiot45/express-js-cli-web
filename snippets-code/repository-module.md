# Repository Module

## Description

The repository module is responsible for handling data operations between the application and the database. It abstracts database queries, making the service layer more readable and maintainable. This module uses Sequelize ORM for database interactions and is implemented in both JavaScript and TypeScript.

---

## Code Implementation

Below is the implementation of the repository code.

### JavaScript Version

```javascript
import testModel from "../models/test.model.js";

const getAllData = async () => await testModel.findAll();

const getDataById = async (id) => await testModel.findOne({ where: id });

const createData = async (data) => await testModel.create(data);

const updateData = async (id, data) => {
  await testModel.update(data, { where: { id } });
  return await testModel.findOne({ where: id });
};

const deleteData = async (id) => {
  const data = await testModel.findOne({ where: id });
  await testModel.destroy({ where: { id } });
  return data;
};

export default { getAllData, getDataById, createData, updateData, deleteData };
```

### TypeScript Version

```javascript
import { Model } from "sequelize";
import testModel from "../models/test.model.ts";
import testInterface from "../interfaces/test.interface.ts";

const getAllData = async (): Promise<Model<testInterface>[]> => {
  return await testModel.findAll();
};

const getDataById = async (
  id: number,
): Promise<Model<testInterface> | null> => {
  return await testModel.findOne({ where: id });
};

const createData = async (
  data: Partial<testInterface>,
): Promise<Model<testInterface>> => {
  return await testModel.create(data);
};

const updateData = async (
  id: number,
  data: Partial<testInterface>,
): Promise<Model<testInterface> | null> => {
  await testModel.update(data, { where: { id } });
  return await testModel.findOne({ where: id });
};

const deleteData = async (id: number): Promise<Model<testInterface> | null> => {
  const data = await testModel.findOne({ where: id });
  if (data) {
    await testModel.destroy({ where: { id } });
  }
  return data;
};

export default { getAllData, getDataById, createData, updateData, deleteData };
```

---

## Explanation

### Key Functions

1. **`getAllData()`** → Fetches all records from the database.
2. **`getDataById(id)`** → Retrieves a single record based on the provided ID.
3. **`createData(data)`** → Inserts a new record into the database.
4. **`updateData(id, data)`** → Updates an existing record with new data and returns the updated record.
5. **`deleteData(id)`** → Finds and deletes a record based on the provided ID.

### How It Works

- The repository interacts directly with the database through the **testModel**.
- Each function uses **Sequelize ORM** to execute database queries.
- The **TypeScript version** provides additional type safety by using `testInterface`.

---

## How to Use

### Importing the Repository in a Service Layer

```javascript
import testRepository from "../repositories/test.repository.js";

const fetchData = async () => {
  const data = await testRepository.getAllData();
  console.log(data);
};

fetchData();
```

### Example CRUD Operations

```javascript
// Create a new record
await testRepository.createData({ name: "Example" });

// Retrieve a record by ID
const data = await testRepository.getDataById(1);

// Update a record
await testRepository.updateData(1, { name: "Updated Example" });

// Delete a record
await testRepository.deleteData(1);
```

---

## Conclusion

This repository module simplifies data access logic by providing a structured way to interact with the database. The TypeScript implementation enhances maintainability and type safety for larger applications. Using a repository pattern improves separation of concerns, making the application more scalable and easier to manage.
