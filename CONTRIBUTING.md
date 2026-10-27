# Contributing recipes

Start with [recipe authoring](docs/authoring.md).
Include an original or redistributable fixture, its expected typed result,
required operation/adapter versions and the actual compatibility check.

Follow the [shared documentation guide](https://github.com/cubearc/docs/blob/main/content/contributing/documentation.md).
Keep usage instructions beside the recipe, link to canonical Cube semantics and
update an existing explanation before creating a new page.

Check local links with `python3 ../docs/tools/check_links.py .` when the
documentation repository is checked out beside this one. Run changed recipe
examples with the real Cube executable and report the result.

Use Conventional Commits and describe the reader task, affected pages and
validation in the PR. A private Play finding is not a published challenge solution
or independently verified answer.
