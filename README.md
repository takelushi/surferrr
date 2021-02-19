# surferrr

Control web browser like a surfer.

## Getting start

### Install

```sh
pip install -U surferrr
# Install chromedriver for your Google Chrome
pip install chromedriver-binary==88.0.4324.96.0

# Check Google Chrom version.
google-chrome --version | awk '{print $3}'
# => e.g. 88.0.4324.182
```

### Browser Automation

```python
import chromedriver_binary  # noqa: F401

from surferrr import Chrome

with Chrome(headless=False) as browser:
    browser.access('http://google.com')
    browser.type_text('//form//input[@type="text"]', 'Python')
    browser.submit('//form')
    browser.capture('./capture.png')
```

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
