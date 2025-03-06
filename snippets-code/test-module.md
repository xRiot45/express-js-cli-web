# Test Module

## Description

This module contains API tests using **Jest** and **Supertest** or **Mocha** and **Chai**. These tests ensure that the API endpoints function correctly by verifying their responses to various request types and scenarios. The tests help validate expected behaviors, error handling, and overall API reliability.

---

## Setup

To set up API testing in your project, create a test file inside your `test` directory (for example, `users.test.js` or `users.test.ts` for TypeScript). Or you can run the command:

```bash
$ express generate test <test-name>
```

> Then, import the required modules and initialize the application accordingly.

### Using Jest & Supertest

For testing with Jest and Supertest, import Supertest and your app instance:

```javascript
import app from "../src/app.js";
import request from "supertest";
```

### Using Mocha & Chai

For testing with Mocha and Chai, import Chai, Chai HTTP, and your app instance:

```javascript
import app from "../src/app.js";
import { use, expect } from "chai";
import { default as chaiHttp, request } from "chai-http";

use(chaiHttp);
```

Define valid and invalid tokens for authentication

```javascript
# JavaScript Version
const validToken = "Bearer valid.token";
const invalidToken = "Bearer invalid.token";
let userId;

# TypeScript Version
const validToken: string = "Bearer valid.token";
const invalidToken: string = "Bearer invalid.token";
let userId: number;
```

**Before each test**, create a test user, and **after each test**, clean up:

```javascript
beforeEach(async () => {
  const res = await request(app)
    .post("/api/v1/users")
    .set("Authorization", validToken)
    .send({
      name: "Test User",
      email: "test@example.com",
      password: "password123",
    });
  userId = res.body.id;
});

afterEach(async () => {
  await request(app)
    .delete(`/api/v1/users/${userId}`)
    .set("Authorization", validToken);
});
```

---

## Test Structure

Each API endpoint is tested in individual test cases. The structure follows:

1. **Successful Cases:** Valid token and valid request body.
2. **Error Cases:** Invalid token, missing parameters, or duplicate data.
3. **Edge Cases:** Checking response codes for unexpected input.

---

## Test Cases

### `POST` /api/v1/users

- **201 Created:** Should return 201 (OK) if token is valid and request is valid
- **400 Bad Request:** Should return 400 (Bad Request) if the request is invalid
- **401 Unauthorized:** Should return 401 (Unauthorized) if the token does not exist
- **403 Forbidden:** Should return 403 (Forbidden) if token is invalid
- **409 Conflict:** Should return 409 (Conflict) if there is already the same data

### `GET` /api/v1/users

- **200 OK:** Should return 200 (OK) if token is valid and display all data
- **401 Unauthorized:** Should return 401 (Unauthorized) if the token does not exist
- **403 Forbidden:** Should return 403 (Forbidden) if the token is invalid

### `GET` /api/v1/users/:id

- **200 OK:** Should return 200 (OK) if token is valid and ID is correct
- **401 Unauthorized:** Should return 401 (Unauthorized) if the token does not exist
- **403 Forbidden:** Should return 403 (Forbidden) if the token is invalid
- **404 Not Found:** Should return 404 (Not Found) if the ID was not found

### `PUT` /api/v1/users/:id

- **200 OK:** Should return 201 (OK) if token is valid and request is valid and update success
- **400 Bad Request:** Should return 400 (Bad Request) if the request is invalid
- **401 Unauthorized:** Should return 401 (Unauthorized) if the token does not exist
- **403 Forbidden:** Should return 403 (Forbidden) if token is invalid
- **404 Not Found:** Should return 404 (Not Found) if the ID was not found
- **409 Conflict:** Should return 409 (Conflict) if there is already the same data

### `DELETE` /api/v1/users/:id

- **200 OK:** Should return 200 (OK) if token is valid and data was successfully deleted
- **401 Unauthorized:** Should return 401(Unauthorized) if the token does not exist
- **403 Forbidden:** Should return 403 (Forbidden) if the token is invalid
- **404 Not Found:** Should return 404 (Not Found) if the ID was not found

---

## Running Tests

Run tests using command:

```bash
$ npm run test
```

## Coverage Tests

To measure test coverage and identify untested parts of your code, use the following commands

```bash
$ npm run test:cov
```

> This will generate a coverage report displaying which parts of the code are covered by tests.

---

## Conclusion

This test suite ensures that all API endpoints handle requests and errors correctly. Jest and Supertest as well as Mocha and Chai make it easy to validate API functionality and maintain robust backend services.
