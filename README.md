# EasyScience Copier Templates

Reusable [Copier](https://copier.readthedocs.io/) templates for EasyScience projects.

## Available Templates

| Template | Description |
|----------|-------------|
| `shared` | Shared base template with common files (README header, LICENSE, .gitignore) |
| `lib` | Python library template (e.g., diffraction-lib, peasy-lib) |
| `app` | Application template (e.g., diffraction-app) |

## Usage

### Multi-template approach (recommended)

Apply templates in layers using a shared data file:

1. Create a `.project/project.yaml` file in your target project with your answers:

```yaml
# Shared questions
project_name: EasyPeasy
project_short_description: Imaginary data analysis
project_extended_description: For performing imaginary calculations based on a theoretical model and refining its parameters against experimental data
project_copyright_years: 2021-2026
home_repo_name: peasy
homepage_url: https://easyscience.github.io/peasy

# Lib-specific questions
lib_repo_name: peasy-lib
lib_package_name: peasy
lib_docs_url: https://easyscience.github.io/peasy-lib

# App-specific questions (if needed)
app_repo_name: peasy-app
app_docs_url: https://easyscience.github.io/peasy-app
```

2. Apply templates in sequence:

```bash
# For a library project
copier copy gh:easyscience/templates-copier/shared . --data-file .project/project.yaml
copier copy gh:easyscience/templates-copier/lib . --data-file .project/project.yaml

# For an app project
copier copy gh:easyscience/templates-copier/shared . --data-file .project/project.yaml
copier copy gh:easyscience/templates-copier/app . --data-file .project/project.yaml
```

**Note:** Each template uses its own answer file (`.copier-answers.shared.yml`, `.copier-answers.lib.yml`, `.copier-answers.app.yml`) to track updates independently.

### Interactive mode

You can also run each template interactively:

```bash
# Apply shared base first
copier copy gh:easyscience/templates-copier/shared .

# Then apply specific template
copier copy gh:easyscience/templates-copier/lib .
# or
copier copy gh:easyscience/templates-copier/app .
```

### Using a specific version/tag

```bash
copier copy gh:easyscience/templates-copier/shared . --vcs-ref=v1.0.0 --data-file .project/project.yaml
copier copy gh:easyscience/templates-copier/lib . --vcs-ref=v1.0.0 --data-file .project/project.yaml
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
├── shared/
│   ├── copier.yml                # Shared questions
│   └── template/
│       ├── .gitignore.jinja
│       ├── LICENSE.jinja
│       ├── README.md.jinja       # Base README header
│       └── {{_copier_conf.answers_file}}.jinja
├── lib/
│   ├── copier.yml                # Lib-specific questions
│   └── template/
│       ├── README.md.jinja       # Lib-specific content
│       ├── pyproject.toml.jinja
│       ├── pixi.toml.jinja
│       ├── src/
│       ├── docs/
│       └── tools/
└── app/
    ├── copier.yml                # App-specific questions
    └── template/
        └── README.md.jinja       # App-specific content
```

**Benefits of multi-template approach:**
- Clean separation of shared vs specific files
- No conditional logic in templates
- Single source of truth via shared data file
- Each template is simpler and easier to maintain
- Independent update tracking via separate answer files (`.copier-answers.shared.yml`, `.copier-answers.lib.yml`)
- Can reuse shared template independently

## Data File Location

You can store your project configuration in `.project/project.yaml` as a submodule or local file:

```bash
git submodule add https://github.com/easyscience/peasy .project
```
```

## License

BSD 3-Clause License
