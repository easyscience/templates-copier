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
template_type: lib  # or "app"
project_name: EasyPeasy
project_short_description: Imaginary data analysis
project_extended_description: For performing imaginary calculations based on a theoretical model
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

2. Run Copier with the `--data-file` option:

```bash
copier copy gh:easyscience/templates-copier . --trust --data-file .project/project.yaml
```

### Interactive mode

```bash
copier copy gh:easyscience/templates-copier . --trust
```

You'll be prompted to select `lib` or `app` template, then answer the relevant questions.

### Using a specific version/tag

```bash
copier copy gh:easyscience/templates-copier . --trust --vcs-ref=v1.0.0
```

## Updating a project

To update an existing project with template changes:

```bash
copier update --trust
```

## Project Structure

```
templates-copier/
├── copier.yml              # Root config with template selection + all questions
├── lib/                    # Library template files
│   └── README.md.jinja
├── app/                    # Application template files
│   └── (template files)
└── shared/
    └── copier.yml          # Shared questions (included by root copier.yml)
```

The root `copier.yml` uses:
- `!include shared/copier.yml` to include shared questions
- `_subdirectory: '{{ template_type }}'` to dynamically select lib/ or app/
- `when:` conditions to show template-specific questions only when relevant

## Data File Location

You can store your project configuration in `.project/project.yaml` as a submodule or local file:

```bash
git submodule add https://github.com/easyscience/peasy .project
```

## License

BSD 3-Clause License
