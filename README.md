# Welcome to MoH Reborn documentation

Documentation is hosted at [mohreborn.com](https://mohreborn.com)

For documentation on how to develop and extend it visit:
* [MkDocs](https://www.mkdocs.org)
* [Material for MkDocs ](https://squidfunk.github.io/mkdocs-material)

## Markdown

When creating documentation, please try to follow good practice guidelines that can be found
[HERE](https://www.markdownguide.org)

Documentation uses Python's Markdown Flavor (*[more details](https://www.mkdocs.org/user-guide/writing-your-docs/#writing-with-markdown)*) 
which is also extended by plugins that come with "MkDocs" or "Material for MkDocs"

## Commands

* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml      # The configuration file.
    docs/
        assets/     # Assets such as images, styles etc.
        styles/     # CSS styles that extend MKDocs Material styles
        overrides/  # Homepage custom HTML that overrides index.md content
        index.md    # The documentation homepage placeholder.
        ...         # Other markdown pages, images and other files.

## Contributing

Please see our [Contributing Guide](.github/CONTRIBUTING.md)