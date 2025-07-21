# Knowledge Database

A comprehensive knowledge database built with MkDocs and Material theme. This repository serves as a centralized location for documentation, tutorials, references, and best practices.

## =Ö View the Documentation

**[Visit the Knowledge Database ’](https://anthonybeech.github.io/docs/)**

## Features

- **Modern Interface**: Built with Material for MkDocs
- **Full-Text Search**: Find information quickly across all content
- **Dark/Light Mode**: Automatic theme switching based on preference
- **Mobile-Friendly**: Responsive design that works on all devices
- **Easy Navigation**: Organized sidebar navigation with expandable sections

## Local Development

To work with this documentation locally:

```bash
# Install dependencies
pip install -r docs/requirements.txt

# Start development server
mkdocs serve
```

Open your browser to `http://localhost:8000` to view the site.

## Contributing

1. Create new Markdown files in the `docs/` directory
2. Update navigation in `mkdocs.template.yml` if needed
3. Use MkDocs Material extensions for enhanced formatting
4. The site automatically deploys to GitHub Pages on push to main

## Architecture

This follows the same pattern as [Astral's UV documentation](https://docs.astral.sh/uv/), using:
- MkDocs with Material theme
- GitHub Actions for CI/CD
- GitHub Pages for free hosting
- Organized content structure for easy maintenance