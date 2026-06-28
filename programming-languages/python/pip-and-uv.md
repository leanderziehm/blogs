# Pip and uv

## pip

```
pip install --only-binary=:all: packagename
```

```
pip freeze > requirements.txt
```



project.toml

```
pip install .
```



## Venv



```
python3 -m venv .venv
source .venv/bin/activate
```







## Tools

#### uv&#x20;

```
uv init
uv add 
uv run
uv add --group dev pytest
```







