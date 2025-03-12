# Compression Middleware

This middleware uses the `compression` module to compress HTTP responses in an Express application. Compression reduces the size of data sent to the client, improving performance and reducing bandwidth usage.

## Middleware Configuration

This middleware is configured to:

- Use compression level `6` (standard)
- Apply compression only for responses larger than `1024` bytes
- Exclude requests with the `x-no-compression` header

### JavaScript Implementation

```javascript
import compression from "compression";

const compressionMiddleware = compression({
  level: 6,
  threshold: 1024,
  filter: (req, res) => {
    if (req.headers["x-no-compression"]) {
      return false;
    }
    return compression.filter(req, res);
  },
});

export default compressionMiddleware;
```

### TypeScript Implementation

```javascript
import compression from "compression";
import { Request, Response } from "express";

const compressionMiddleware = compression({
  level: 6,
  threshold: 1024,
  filter: (req: Request, res: Response): boolean => {
    if (req.headers["x-no-compression"]) {
      return false;
    }
    return compression.filter(req, res);
  },
});

export default compressionMiddleware;
```

## Usage

Add this middleware to your Express application as follows:

```javascript
import express from "express";
import { compressionMiddleware } from "../middlewares/index.js/ts";

const configureExpress = () => {
  const app = express();

  // Add compression middleware in here
  app.use(compressionMiddleware);

  return app;
};

export default configureExpress;
```

## Explanation of Options

- `level: 6` → Sets the compression level (0-9, with 9 being the highest compression).
- `threshold: 1024` → Only compress responses larger than 1024 bytes.
- `filter(req, res)` → Excludes requests that have the `x-no-compression` header.

## Conclusion

This middleware helps optimize data transmission to the client by reducing the response payload size. By applying filters, we can control when compression is applied.
