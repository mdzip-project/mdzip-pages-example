# MDZip pages example

A website whose pages are MDZip (`.mdz`) files: each page is one file holding its Markdown and its pictures. On every push, GitHub checks the pages, converts them to HTML with [Pandoc](https://pandoc.org) and publishes them on GitHub Pages. There's no website code in the repository, only pages, a template and a style sheet.

**See it live:** https://mdzip-project.github.io/mdzip-pages-example/

```
pages/*.mdz  →  mdz validate  →  Pandoc + template  →  GitHub Pages
```

## Make your own

1. Click **Use this template**, and create your repository.
2. In **Settings** > **Pages**, set **Source** to **GitHub Actions**.
3. Replace the pages in `pages/` with your own `.mdz` files, written in [MDZip Studio](https://mdzip.org/studio), [VS Code](https://mdzip.org/vscode) or [Obsidian](https://mdzip.org/obsidian), and push.

`pages/index.mdz` is the home page. Each page's title and description come from the details stored in its `.mdz`. Link between pages by file name (`[Setup](setup.mdz)`): the links work in your editor and on the site.

| Path | What it is |
|---|---|
| `pages/` | The pages, one `.mdz` each. Subfolders are kept. |
| `site/template.html` | The layout and menu, as a [Pandoc template](https://pandoc.org/MANUAL.html#templates). |
| `site/style.css` | How the pages look. |
| `.github/workflows/pages.yml` | Check, convert, publish. |

The workflow uses two actions:

- [setup-mdz](https://github.com/mdzip-project/setup-mdz) installs the `mdz` CLI, to check every page with `mdz validate`.
- [mdzip-pandoc](https://github.com/mdzip-project/mdzip-pandoc) converts the folder of `.mdz` pages to HTML pages.

## Seeing changes in a pull request

GitHub shows an `.mdz` as a binary file. To see what changed inside one on your own computer, set up [`mdz textconv`](https://github.com/mdzip-project/mdzip-cli#mdz-textconv-archive): this repository's `.gitattributes` already marks `.mdz` files for it.

## License

Apache License 2.0. See [LICENSE](LICENSE).
