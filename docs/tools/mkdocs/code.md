# Block Example

## Basic Code Block

```py title="example.py" linenums="1"
def greet(name):
  """Function to greet a person."""
  return f"Hello, {name}!"
```


```py title="example.py" linenums="1" hl_lines="2"
def greet(name):
  """Function to greet a person."""
  return f"Hello, {name}!"
```

## Tab Blocks
Enabled by the following configuration in `mkdocs.yml`:

```yml title="mkdocs.yml"
markdown_extensions:
  - pymdownx.tabbed:
      alternate_style: true
```

=== "Plain Text"

    This is a plain text file.

=== "Unordered List"

    - Item 1
    - Item 2
    - Item 3

=== "Ordered List"

    1. First item
    2. Second item
    3. Third item

## Admonitions
!!! note "Note Title"

    This is a note admonition.

??? info "Collapsible Info"

    This is a collapsible info admonition.
