# MkDocs

<https://www.mkdocs.org/getting-started/>

<https://www.mkdocs.org/user-guide/writing-your-docs/>

Markdown is expected in top-level `docs/` dir, with `docs/index.md` being the home page.

<!-- INDEX_START -->

- [Install](#install)
- [Template](#template)
- [Build](#build)
- [Preview Locally](#preview-locally)
- [MkDocs Gotchas](#mkdocs-gotchas)
  - [Bare URLs Are Not Clickable](#bare-urls-are-not-clickable)
  - [Quadruple Backticks work in GitHub but not in MKDocs](#quadruple-backticks-work-in-github-but-not-in-mkdocs)

<!-- INDEX_END -->

## Install

```shell
pip install mkdocs
```

## Template

[nholuongut/templates - mkdocs.yml](https://github.com/nholuongut/templates/blob/master/mkdocs.yml)

## Build

- build the `site/` dir, containing the HTML, Javascript, `sitemap.xml` and `mkdocs/search_index.json`
- `site/` should be added to [.gitignore](https://github.com/nholuongut/devops-bash-tools/blob/master/.gitignore)

```shell
mkdocs build
```

## Preview Locally

Launch a local web server at <http://127.0.0.1:8000>:

```shell
mkdocs serve
```

On Mac, you can open this from the CLI:

```shell
open http://127.0.0.1:8000
```

## MkDocs Gotchas

Some things that render fine in Markdown break in MKDocs:

### Bare URLs Are Not Clickable

Bare URLs are links on GitHub `README.md` but not in MKDocs generated pages

Enclose them in `<` and `>` to make sure they become links.

### Quadruple Backticks don't work in MKDocs

A stray backtick on a triple backticks code block,
or an intentional quadruple backticks used to enclose a code sample containing
triple backticks (such as seen in the [Markdown](markdown.md) doc page) will work in GitHub Markdown
and [IntelliJ](intellij.md) local rendering
but break formatting in MKDocs.
