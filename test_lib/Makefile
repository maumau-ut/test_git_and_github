.PHONY: all
all: clean fmt lint test

.PHONY: clean
clean:
	@rm -rf build dist *.egg-info .coverage .coverage.* .eggs .mypy_cache .pytest_cache
	@find . -type f -name "*.pyc" -delete
	@find . -type d -name "__pycache__" | xargs rm -rf

.PHONY: black
black:
	@poetry run black .

.PHONY: flake8
flake8:
	@poetry run flake8 .

.PHONY: isort
isort:
	@poetry run isort .

.PHONY: mypy
mypy:
	@poetry run mypy --install-types --non-interactive --ignore-missing-imports .

.PHONY: fmt
fmt: black isort

.PHONY: lint
lint: flake8 mypy

.PHONY: pre-commit
pre-commit:
	@poetry run pre-commit

.PHONY: pre-commit-all
pre-commit-all:
	@poetry run pre-commit run --all-files

.PHONY: test
test:
	@poetry run pytest -vvs --cov=test_lib --cov-report=term-missing

.PHONY: tox
tox:
	@poetry run tox
