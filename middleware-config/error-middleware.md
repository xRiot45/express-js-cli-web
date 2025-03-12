# Error Handling Middleware

This middleware is used to handle errors in an Express application. It captures errors thrown during request processing and returns a standardized JSON response with an appropriate status code and error details.

## Implementation

### JavaScript Version

```javascript
const errorMiddleware = (err, req, res, _next) => {
  res.status(err.status || 500).json({
    message: err.message || "Internal Server Error",
    errors: err.errors || null,
  });
};

export default errorMiddleware;
```

### TypeScript Version

```javascript
import { Request, Response, NextFunction } from "express";

interface CustomError extends Error {
  status?: number;
  errors?: Record<string, string> | null;
}

const errorMiddleware = (
  err: CustomError,
  req: Request,
  res: Response,
  _next: NextFunction,
): void => {
  res.status(err.status || 500).json({
    message: err.message || "Internal Server Error",
    errors: err.errors || null,
  });
};

export default errorMiddleware;
```

## Usage

To use this middleware, add it to your Express application after defining all routes:

```javascript
import express from "express";
import { errorMiddleware } from "../middlewares/index.js/ts";

const configureExpress = () => {
  const app = express();

  // Add error middleware in here
  app.use(errorMiddleware);

  return app;
};

export default configureExpress;
```

## Explanation of Functionality

- `err.status || 500` → Sets the HTTP status code based on the error or defaults to `500` (Internal Server Error).
- `err.message || 'Internal Server Error'` → Provides a descriptive error message.
- `err.errors || null` → Optionally includes additional error details if available.

## Conclusion

This middleware provides a consistent way to handle errors in an Express application, ensuring meaningful error responses are sent to clients. Modify the response structure as needed to fit your application's requirements.
