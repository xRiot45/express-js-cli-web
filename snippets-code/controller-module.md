# Controller Module

## Description

This module provides a set of controller functions for handling HTTP requests and responses. It includes operations for fetching, creating, updating, and deleting data. There are two implementations: one using JavaScript and another using TypeScript with type definitions.

---

## Code Implementation

Below is the implementation of the controller code.

### JavaScript Version

```javascript
const get = async (req, res, next) => {
  try {
    // Implement your logic to get data here
  } catch (error) {
    next(error);
  }
};

const getById = async (req, res, next) => {
  try {
    // Implement your logic to get data by ID here
  } catch (error) {
    next(error);
  }
};

const create = async (req, res, next) => {
  try {
    // Implement your logic to create data here
  } catch (error) {
    next(error);
  }
};

const update = async (req, res, next) => {
  try {
    // Implement your logic to update data here
  } catch (error) {
    next(error);
  }
};

const remove = async (req, res, next) => {
  try {
    // Implement your logic to remove data here
  } catch (error) {
    next(error);
  }
};

export default { get, getById, create, update, remove };
```

#### Explanation of Functions

1. **get(req, res, next)** → Handles retrieving all data.
2. **getById(req, res, next)** → Handles retrieving data by ID.
3. **create(req, res, next)** → Handles creating new data.
4. **update(req, res, next)** → Handles updating existing data by ID.
5. **remove(req, res, next)** → Handles deleting data by ID.

> Each function includes a `try-catch` block to catch errors and pass them to the `next` middleware.

---

### TypeScript Version

```javascript
import { Request, Response, NextFunction } from "express";

const get = async (
  req: Request,
  res: Response,
  next: NextFunction,
): Promise<void> => {
  try {
    // Implement your logic to get data here
  } catch (error) {
    next(error);
  }
};

const getById = async (
  req: Request,
  res: Response,
  next: NextFunction,
): Promise<void> => {
  try {
    // Implement your logic to get data by ID here
  } catch (error) {
    next(error);
  }
};

const create = async (
  req: Request,
  res: Response,
  next: NextFunction,
): Promise<void> => {
  try {
    // Implement your logic to create data here
  } catch (error) {
    next(error);
  }
};

const update = async (
  req: Request,
  res: Response,
  next: NextFunction,
): Promise<void> => {
  try {
    // Implement your logic to update data here
  } catch (error) {
    next(error);
  }
};

const remove = async (
  req: Request,
  res: Response,
  next: NextFunction,
): Promise<void> => {
  try {
    // Implement your logic to remove data here
  } catch (error) {
    next(error);
  }
};

export default { get, getById, create, update, remove };
```

#### Explanation of Functions

1. **get(req, res, next)** → Retrieves all data.
2. **getById(req, res, next)** → Retrieves a specific data entry by ID.
3. **create(req, res, next)** → Creates new data.
4. **update(req, res, next)** → Updates an existing data entry.
5. **remove(req, res, next)** → Deletes a data entry.

> All functions use `Request`, `Response`, and `NextFunction` from Express to ensure type safety.

---

## How To Use

1. **Import controller into route file**
   ```javascript
   import controller from "../controllers/<controller-name>.js";
   ```
2. **Use in Express routing**

   ```javascript
   import express from "express";
   const router = express.Router();

   router.get("/", controller.get);
   router.get("/:id", controller.getById);
   router.post("/", controller.create);
   router.put("/:id", controller.update);
   router.delete("/:id", controller.remove);

   export default router;
   ```

---

## Conclusion

This module provides controller functions to handle HTTP requests in an Express.js application. The TypeScript version ensures better type safety and maintainability. Both implementations include error handling using `next(error)`, making them suitable for integration with Express error-handling middleware.
