# Block Example

## Code Block

### Basic Code Block

=== "Result"

    ```py title="example.py" linenums="1"
    def greet(name):
      """Function to greet a person."""
      return f"Hello, {name}!"
    ```

=== "Code"

    ```
    py title="example.py" linenums="1"
    def greet(name):
      """Function to greet a person."""
      return f"Hello, {name}!"
    ```

### Highlighted Lines

=== "Result"
    ```py title="example.py" linenums="1" hl_lines="2"
    def greet(name):
      """Function to greet a person."""
      return f"Hello, {name}!"
    ```

=== "Code"
    ```
    py title="example.py" linenums="1" hl_lines="2"
    def greet(name):
      """Function to greet a person."""
      return f"Hello, {name}!"
    ```

---

## Tab Blocks
Enabled by the following configuration in `mkdocs.yml`:

```yml title="mkdocs.yml"
markdown_extensions:
  - pymdownx.tabbed:
      alternate_style: true
```

With the format below, you can create tabbed content:
```markdown
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
```

The result will look like this:

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

## [Admonitions](https://squidfunk.github.io/mkdocs-material/reference/admonitions/)
Amonitions start with `!!!` followed by the type of admonition.

=== "Result"

    !!! note "Note Title"

        This is a note admonition.

=== "Code"
    ```
    !!! note "Note Title"

        This is a note admonition.
    ```

Collapsible admonitions can be created using the `???`:

=== "Result"

    ??? info "Collapsible Info"

        This is a collapsible info admonition.

=== "Code"
    ```
    ??? info "Collapsible Info"

        This is a collapsible info admonition.
    ```

### Icons in Admonitions
note:
??? note "note"

info:
??? info "info"

tip:
??? tip "tip"

success:
??? success "success"

question:
??? question "question"

warning:
??? warning "warning"

failure:
??? failure "failure"

danger:
??? danger "danger"

bug:
??? bug "bug"

quote:
??? quote "quote"

