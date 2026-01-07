# EasyScience Copier Templates

Reusable [Copier](https://copier.readthedocs.io/) templates for EasyScience projects.

## Available Templates

| Template | Description |
|----------|-------------|
| `lib` | Python library template (e.g., diffraction-lib, peasy-lib) |
| `app` | Application template (e.g., diffraction-app) |

## Usage

### Using with a data file (recommended)

1. Create a `.project/project.yaml` file in your target project with your answers:

```yaml
project_name: EasyPeasy
project_short_description: Imaginary data analysis
project_extended_description: For performing imaginary calculations based on a theoretical model and refining its parameters against experimental data
project_copyright_years: 2021-2026
home_repo_name: peasy
homepage_url: https://easyscience.github.io/peasy
# For lib template:
lib_repo_name: peasy-lib
lib_package_name: peasy
lib_docs_url: https://easyscience.github.io/peasy-lib
# For app template:
# app_repo_name: peasy-app
# app_docs_url: https://easyscience.github.io/peasy-app
```

2. Run Copier with the `--data-file` option and specify the template type:

```bash
# For a library project
copier copy gh:easyscience/templates-copier . --data-file .project/project.yaml -d template_type=lib

# For an app project
copier copy gh:easyscience/templates-copier . --data-file .project/project.yaml -d template_type=app
```

### Interactive mode

```bash
copier copy gh:easyscience/templates-copier .
```

You'll be prompted to select `lib` or `app` template, then answer the relevant questions.

### Using a specific version/tag

```bash
copier copy gh:easyscience/templates-copier . --vcs-ref=v1.0.0 -d template_type=lib
```

## Updating a project

To update an existing project with template changes:

```bash
copier update
```

Or with updated data file:

```bash
copier update --data-file .project/project.yaml
```

## Project Structure

```
templates-copier/
├── copier.yml                    # Root config with template selection + all questions
├── shared/
│   └── questions.yml             # Shared questions (included by copier.yml)
└── template/                     # All template files (_subdirectory: template)
    ├── .gitignore.jinja          # Shared (always copied)
    ├── LICENSE.jinja             # Shared (always copied)
    ├── {{_copier_conf.answers_file}}.jinja
    ├── {% if template_type == 'lib' %}README.md{% endif %}.jinja   # lib-only
    ├── {% if template_type == 'app' %}README.md{% endif %}.jinja   # app-only
    └── .github/
        └── workflows/
            └── (CI workflow files with conditional names)
```

**How conditional files work:**
- Files named `{% if template_type == 'lib' %}filename{% endif %}.jinja` only appear when `template_type=lib`
- Shared files (no condition) are always copied
- Use `{% if %}` inside file content for conditional sections

## Data File Location

You can store your project configuration in `.project/project.yaml` as a submodule or local file:

```bash
git submodule add https://github.com/easyscience/peasy .project
```

## License

BSD 3-Clause License
