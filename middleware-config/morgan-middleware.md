# Morgan Middleware

This middleware utilizes the `morgan` module to log HTTP requests in an Express application. It helps track incoming requests, making debugging and monitoring easier.

## Middleware Configuration

This middleware is configured to:

- Use the `combined` logging format (standard Apache-style logging)
- Write log messages to a custom logger

### JavaScript Implementation

```javascript
import morgan from "morgan";
import logger from "../configs/logger.config.js";

const morganMiddleware = morgan("combined", {
  stream: {
    write: (message) => logger.info(message.trim()),
  },
});

export default morganMiddleware;
```

### TypeScript Implementation

```javascript
import morgan, { StreamOptions } from "morgan";
import logger from "../configs/logger.config.ts";

const stream: StreamOptions = {
  write: (message: string) => logger.info(message.trim()),
};

const morganMiddleware = morgan("combined", { stream });

export default morganMiddleware;
```

## Usage

Add this middleware to your Express application as follows:

```javascript
import express from "express";
import { morganMiddleware } from "../middlewares/index.js/ts";

const configureExpress = () => {
  const app = express();

  // Add morgan middleware in here
  app.use(morganMiddleware);

  return app;
};

export default configureExpress;
```

## Explanation of Configuration

- `morgan('combined')` → Uses the `combined` logging format, which includes details such as IP, method, status, and user agent.
- `stream.write(message)` → Redirects log output to a custom logger.

## Conclusion

This middleware enhances request logging in an Express application, ensuring better monitoring and debugging. You can modify the logging format or destination as needed based on your application's requirements.
