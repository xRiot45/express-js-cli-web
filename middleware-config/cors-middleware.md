# CORS Middleware

This middleware uses the `cors` module to enable Cross-Origin Resource Sharing (CORS) in an Express application. It allows your server to handle requests from different origins, improving flexibility while maintaining security.

## Middleware Configuration

This middleware is configured to:

- Allow requests from any origin (`*`)
- Permit HTTP methods: `GET`, `POST`, `PUT`, `DELETE`, and `OPTIONS`
- Allow headers: `Content-Type` and `Authorization`
- Support credentials (cookies, authorization headers, etc.)

### JavaScript Implementation

```javascript
import cors from "cors";

const corsMiddleware = cors({
  origin: "*",
  methods: ["GET", "POST", "PUT", "DELETE", "OPTIONS"],
  allowedHeaders: ["Content-Type", "Authorization"],
  credentials: true,
});

export default corsMiddleware;
```

### TypeScript Implementation

```javascript
import cors from "cors";
import { CorsOptions } from "cors";

const corsOptions: CorsOptions = {
  origin: "*",
  methods: ["GET", "POST", "PUT", "DELETE", "OPTIONS"],
  allowedHeaders: ["Content-Type", "Authorization"],
  credentials: true,
};

const corsMiddleware = cors(corsOptions);

export default corsMiddleware;
```

## Usage

Add this middleware to your Express application as follows:

```javascript
import express from "express";
import { corsMiddleware } from "../middlewares/index.js/ts";

const configureExpress = () => {
  const app = express();

  // Add cors middleware in here
  app.use(corsMiddleware);

  return app;
};

export default configureExpress;
```

## Explanation of Options

- `origin: '*'` → Allows all origins to access the server.
- `methods: ['GET', 'POST', 'PUT', 'DELETE', 'OPTIONS']` → Specifies allowed HTTP methods.
- `allowedHeaders: ['Content-Type', 'Authorization']` → Defines which headers are allowed in requests.
- `credentials: true` → Allows cookies and authentication headers to be sent with requests.

## Conclusion

This middleware helps handle cross-origin requests efficiently while ensuring the necessary security controls are in place. Modify the configuration as needed to restrict access based on your application's requirements.
