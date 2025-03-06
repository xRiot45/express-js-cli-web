# Route Module

## Description

This module defines the routing logic for handling HTTP requests in an Express.js application. It connects the client requests to the corresponding controller functions, ensuring that each route triggers the correct CRUD operation. There are two implementations of the code: one using JavaScript and another using TypeScript.

---

## Code Implementation

Below is the implementation of the route code.

### JavaScript Version

```javascript
import { Router } from "express";
import testController from "../controllers/test.controller.js";

const testRouter = Router();

testRouter.get("/", testController.get);
testRouter.get("/:id", testController.getById);
testRouter.post("/", testController.create);
testRouter.put("/:id", testController.update);
testRouter.delete("/:id", testController.remove);

export default testRouter;
```

#### Explanation of Functions

1. **GET `/`** → Calls `get` method in the controller to retrieve a list of data.
2. **GET `/:id`** → Calls `getById` method in the controller to retrieve data by ID.
3. **POST `/`** → Calls `create` method in the controller to create new data.
4. **PUT `/:id`** → Calls `update` method in the controller to update existing data by ID.
5. **DELETE `/:id`** → Calls `remove` method in the controller to delete data by ID.

> Each route maps an HTTP method and endpoint to a corresponding function in the controller.

---

### TypeScript Version

```javascript
import { Router } from "express";
import testController from "../controllers/test.controller.ts";

const testRouter: Router = Router();

testRouter.get("/", testController.get);
testRouter.get("/:id", testController.getById);
testRouter.post("/", testController.create);
testRouter.put("/:id", testController.update);
testRouter.delete("/:id", testController.remove);

export default testRouter;
```

#### Explanation of Functions

1. **GET `/`** → Calls `get` method in the controller to retrieve a list of data.
2. **GET `/:id`** → Calls `getById` method in the controller to retrieve data by ID.
3. **POST `/`** → Calls `create` method in the controller to create new data.
4. **PUT `/:id`** → Calls `update` method in the controller to update existing data by ID.
5. **DELETE `/:id`** → Calls `remove` method in the controller to delete data by ID.

> The TypeScript version explicitly declares the `testRouter` as a `Router` type, ensuring proper type-checking and reducing runtime errors.

---

## How to Use

1. **Import the router into the main application file:**

   ```javascript
   import testRouter from "./routes/test.route.js/ts";
   ```

2. **Use it in an Express application:**

   ```javascript
   import express from "express";
   const app = express();

   app.use("/test", testRouter);

   app.listen(3000, () => {
     console.log("Server is running on port 3000");
   });
   ```

---

## Conclusion

This module provides a routing system that connects HTTP requests to their respective controller functions. The TypeScript implementation offers additional type safety, making the code more robust and maintainable. Using Express Router, we efficiently define routes for CRUD operations while maintaining a clean and modular structure.
