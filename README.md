# My notes

## proxy for api

To see how it works, open apps/todos/project.json and find the serve target of the todos app.

```json
{
  "serve": {
    "executor": "@angular-devkit/build-angular:dev-server",
    "configurations": {
      "production": {
        "browserTarget": "todos:build:production"
      },
      "development": {
        "browserTarget": "todos:build:development"
      }
    },
    "defaultConfiguration": "development",
    "options": {
      "proxyConfig": "apps/todos/proxy.conf.json"
    }
  }
}
```

Note the proxyConfig property.

Now open apps/todos/proxy.conf.json:

```json
{
  "/api": {
    "target": "http://localhost:3333",
    "secure": false
  }
}
```

This configuration tells nx serve to forward all requests starting with /api to the process listening on port 3333.
