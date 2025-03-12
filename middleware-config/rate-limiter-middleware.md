# Rate Limiter Middleware

This middleware uses the `express-rate-limit` module to limit the number of requests a client can make to the server within a specific timeframe. This helps prevent abuse, brute-force attacks, and excessive load on the server.

## Middleware Configuration

This middleware is configured to:

- Limit requests to `100` per `15 minutes` (900,000 ms)
- Return a `429 Too Many Requests` error when the limit is exceeded
- Include rate limit headers in the response

### JavaScript Implementation

```javascript
import rateLimit from "express-rate-limit";

const limiterMiddleware = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // Limit each IP to 100 requests per windowMs
  message: {
    status: 429,
    error: "Too many requests, please try again later.",
  },
  headers: true,
});

export default limiterMiddleware;
```

### TypeScript Implementation

```javascript
import rateLimit from "express-rate-limit";
import { Request, Response, NextFunction } from "express";

const limiterMiddleware = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // Limit each IP to 100 requests per windowMs
  handler: (req: Request, res: Response, next: NextFunction) => {
    res.status(429).json({
      status: 429,
      error: "Too many requests, please try again later.",
    });
  },
  headers: true,
});

export default limiterMiddleware;
```

## Usage

Add this middleware to your Express application as follows:

```javascript
import express from "express";
import { limiterMiddleware } from "../middlewares/index.js/ts";

const configureExpress = () => {
  const app = express();

  // Add rate limiter middleware in here
  app.use(limiterMiddleware);

  return app;
};

export default configureExpress;
```

## Explanation of Options

- `windowMs: 15 * 60 * 1000` → Defines the rate limit window of `15 minutes`.
- `max: 100` → Allows up to `100` requests per client within the window.
- `message` / `handler` → Defines the response sent when the limit is exceeded.
- `headers: true` → Includes rate limit headers in the response.

## Conclusion

This middleware helps protect your application from excessive requests and potential abuse by enforcing rate limits. Adjust the settings based on your application's needs to ensure optimal security and performance.
