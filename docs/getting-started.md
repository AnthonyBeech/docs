# Getting Started

This guide will help you understand how to use and contribute to this knowledge database.

## Local Development

To work with this documentation locally:

### Prerequisites

- Python 3.8 or higher
- Git

### Setup

1. Clone the repository:
   ```bash
   git clone <your-repo-url>
   cd docs
   ```

2. Install dependencies:
   ```bash
   pip install -r docs/requirements.txt
   ```

3. Serve locally:
   ```bash
   mkdocs serve
   ```

4. Open your browser to `http://localhost:8000`

## Building the Documentation

To build the static site:

```bash
mkdocs build --strict
```

The built site will be in the `site/` directory.

## Adding Content

### Creating New Pages

1. Create a new Markdown file in the appropriate `docs/` subdirectory
2. Add the page to the navigation in `mkdocs.template.yml`
3. Use standard Markdown syntax with MkDocs extensions

### Organizing Content

- Use the `knowledge-base/` directory for topical content
- Create subdirectories for related topics
- Update navigation structure as needed

### Markdown Features

This site supports:

- Code highlighting
- Admonitions (notes, warnings, tips)
- Tables
- Footnotes
- Emoji
- Tabbed content

## Deployment

The site automatically deploys to GitHub Pages when changes are pushed to the main branch via GitHub Actions.