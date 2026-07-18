# Python

## Raise Exceptions:

```
raise Exception("Sorry, no numbers below zero")
```

## Fastapi

```
from fastapi.openapi.docs import get_swagger_ui_html

...

@app.get("/", include_in_schema=False)
async def custom_swagger_ui():
    return get_swagger_ui_html(openapi_url="/openapi.json", title="API Docs")

```

## Pandas

```
import pandas as pd
pd.set_option('display.max_columns', None)
pd.set_option('display.max_rows', None)
```

```
def dataframe_summary(df: pd.DataFrame) -> pd.DataFrame:
    summary = []

    for col in df.columns:
        col_data = df[col]

        unique_values = col_data.dropna().unique()
        unique_count = len(unique_values)

        summary.append({
            "column": col,
            "unique_count": unique_count,
            "missing_values": col_data.isna().sum(),
            "non_nan_values": col_data.notna().sum(),
            "sample_values": unique_values.tolist()
        })

    result = pd.DataFrame(summary)

    # sort by unique value count descending
    result = result.sort_values(by="unique_count", ascending=False).reset_index(drop=True)

    return result


# usage:
summary_df = dataframe_summary(df)
summary_df
```

## VsCode Debugger settings

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





```
all:
	[ ! -d "venv" ] && python -m venv venv && venv/bin/pip install -r requirements.txt; set -a && . ./.env && set +a && venv/bin/uvicorn main:app --reload

run:
	uvicorn main:app --port 8803

uv_run:
	uv run uvicorn main:app --port 8803

uv_req:
	uv pip freeze > requirements.txt

uv_req_no_v:
	uv pip freeze | cut -d= -f1 > requirements.txt

```
