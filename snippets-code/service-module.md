# Service Module

## Description

This module provides a set of functions to perform CRUD (Create, Read, Update, Delete) operations on data. There are two code implementations, one using JavaScript and one using TypeScript with interfaces.

---

## Code Implementation

Below is the implementation of the service code.

### JavaScript Version

```javascript
const get = async () => {
  // Implementation of logic to get data
  return [];
};

const getById = async (id) => {
  // Implementation of logic to get data based on ID
  return null;
};

const create = async (data) => {
  // Implementation of logic to create new data
  return null;
};

const update = async (id, data) => {
  // Implementation of logic to update data based on ID
  return null;
};

const remove = async (id) => {
  // Implementation of logic to delete data based on ID
  return false;
};

export default { get, getById, create, update, remove };
```

#### Explanation of Functions

1. **get()** → Returns a list of data in the form of an empty array.
2. **getById(id)** → Returns the specified data by ID or `null` if not found.
3. **create(data)** → Adds new data, but currently only returns `null`.
4. **update(id, data)** → Updates data based on ID, but does not yet return the updated data.
5. **remove(id)** → Removes data based on ID, but always returns `false`.

---

### TypeScript Version

```javascript
import testInterface from "../interfaces/test.interface.ts";

const get = async (): Promise<testInterface[]> => {
  // Implementation of logic to get data
  return [];
};

const getById = async (id: string): Promise<testInterface | null> => {
  // Implementation of logic to get data based on ID
  return null;
};

const create = async (data: testInterface): Promise<testInterface> => {
  // Implementation of logic to create new data
  return data;
};

const update = async (
  id: string,
  data: Partial<testInterface>,
): Promise<testInterface | null> => {
  // Implementation of logic to update data based on ID
  return null;
};

const remove = async (id: string): Promise<boolean> => {
  // Implementation of logic to delete data based on ID
  return false;
};

export default { get, getById, create, update, remove };
```

#### Explanation of Functions

1. **get()** → Returns a list of data in the form of an empty array of type `testInterface[]`.
2. **getById(id)** → Returns the specified data by ID in the form of `testInterface` or `null` if not found.
3. **create(data)** → Adds new data and returns the data in the form of `testInterface`.
4. **update(id, data)** → Updates the data based on the ID and returns the updated data or `null` if not found.
5. **remove(id)** → Removes data based on ID and returns `true` if successful or `false` if failed.

---

## How To Use

1. **Import service into controller file**
   ```javascript
   import service from "../services/<service-name>.js";
   ```
2. **Call the required function**
   ```javascript
   const get = async (req, res, next) => {
     try {
       const data = await service.get();
       console.log(data);
     } catch (error) {
       next(error);
     }
   };
   ```

---

## Conclusion

This module provides CRUD functionality with two different implementations: JavaScript and TypeScript. TypeScript is safer to use because it provides static typing and interfaces to improve data security and project maintainability.
