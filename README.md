# surferrr

Control web browser like a surfer.

## Development

```sh
# Setup
poetry install

# Lint & Test
mkdir -p report
poetry run flake8 --format=html --htmldir=report/flake-report src/ tests/
poetry run mypy src/ tests/ --html-report report/mypy
poetry run pytest \
   --html=report/pytest/index.html \
   --cov-report html:report/coverage

# Build and publish
poetry build
poetry publish
```
