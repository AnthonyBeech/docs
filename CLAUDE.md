# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a knowledge database documentation site built with MkDocs and Material theme. It follows the same pattern as Astral's UV docs, using GitHub Actions for CI/CD and GitHub Pages for hosting.

## Architecture

### Documentation Structure
- `docs/` - All Markdown content lives here
- `mkdocs.template.yml` - Main configuration template defining theme, nav, extensions
- `mkdocs.yml` - Production configuration that inherits from template
- `docs/requirements.txt` - Python dependencies for MkDocs build
- `.github/workflows/publish-docs.yml` - CI/CD workflow for automatic deployment

### Content Organization
- `docs/index.md` - Homepage
- `docs/getting-started.md` - Setup and contribution guide
- `docs/knowledge-base/` - Main knowledge content directory
- `docs/references.md` - Quick reference materials

## Common Commands

### Local Development
```bash
# Install dependencies
pip install -r docs/requirements.txt

# Start development server
mkdocs serve

# Build static site
mkdocs build --strict
```

### Content Management
- Create new pages as Markdown files in `docs/` subdirectories
- Update navigation in `mkdocs.template.yml` under the `nav:` section
- Use MkDocs Material extensions for enhanced formatting

## Deployment

- Automatic deployment via GitHub Actions to GitHub Pages
- Triggered on pushes to main branch
- Requires GitHub Pages to be enabled in repository settings
- Site URL will be: `https://username.github.io/repository-name/`

## Key Features

- Material theme with dark/light mode
- Full-text search
- Code highlighting with copy buttons
- Responsive design
- Admonitions (notes, warnings, tips)
- Tabbed content support