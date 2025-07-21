# References

Quick reference materials and lookup tables for common information.

## Command References

### Git Commands
```bash
# Common Git operations
git status                 # Check repository status
git add .                 # Stage all changes
git commit -m "message"   # Commit with message
git push origin main      # Push to remote
git pull origin main      # Pull from remote
```

### MkDocs Commands
```bash
# MkDocs operations
mkdocs serve             # Start development server
mkdocs build             # Build static site
mkdocs build --strict    # Build with strict mode
mkdocs new project-name  # Create new project
```

## Markdown Quick Reference

### Basic Formatting
- **Bold text**: `**bold**`
- *Italic text*: `*italic*`
- `Inline code`: `` `code` ``
- [Links](https://example.com): `[text](url)`

### Lists
- Unordered: `- item`
- Ordered: `1. item`
- Nested: Indent with spaces

### Code Blocks
````markdown
```python
def hello():
    print("Hello, world!")
```
````

### Tables
```markdown
| Column 1 | Column 2 |
|----------|----------|
| Data 1   | Data 2   |
```

### Admonitions
```markdown
!!! note "Title"
    This is a note admonition.

!!! warning
    This is a warning.

!!! tip
    This is a tip.
```

## Useful Links

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [PyMdown Extensions](https://facelessuser.github.io/pymdown-extensions/)
- [GitHub Pages](https://pages.github.com/)