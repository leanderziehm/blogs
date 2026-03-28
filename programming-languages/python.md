# Python



## Fastapi

```
from fastapi.openapi.docs import get_swagger_ui_html

...

@app.get("/", include_in_schema=False)
async def custom_swagger_ui():
    return get_swagger_ui_html(openapi_url="/openapi.json", title="API Docs")

```





## Pandas&#x20;

```
import pandas as pd
pd.set_option('display.max_columns', None)
pd.set_option('display.max_rows', None)
```

## VsCode Debugger settings&#x20;

```
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Python Debugger: JSON Sender",
      "type": "debugpy",
      "request": "launch",
      "module": "process_excel.main",
      "env": {},
      "envFile": "${workspaceFolder}/.env",
      "python": "${workspaceFolder}/process_excel/.venv/bin/python"
    },
    {
      "name": "Python Debugger: Backend",
      "type": "debugpy",
      "request": "launch",
      "module": "src.backend.main",
      "env": {
        "TESTING": "True",
        "PORT": "8080",
        "POSTGRES_HOST": "127.0.0.1",
        "POSTGRES_USER": "postgres",
        "POSTGRES_PASSWORD": "super-secret-password123",
        "POSTGRES_DB": "schmako",
        "POSTGRES_PORT": "5432",
        "API_AUTH_TOKEN": "123"
      },
      "envFile": "${workspaceFolder}/.env",
      "python": "${workspaceFolder}/.venv/bin/python"
    },
    {
      "name": "Python Debugger: LLM",
      "type": "debugpy",
      "request": "launch",
      "module": "src.backend.ai_llm",
      "env": {},
      "envFile": "${workspaceFolder}/.env",
      "python": "${workspaceFolder}/.venv/bin/python"
    }
  ]
}
```
