# cleanwiki theme for hugo

this is a fork of [hugo-book](https://github.com/alex-shpak/hugo-book) which aims to be leaner.

## original features of hugo-book

- Clean simple design
- Light and Mobile-Friendly
- Multi-language support
- Customisable
- Zero initial configuration
- Handy shortcodes
- Comments support
- Simple blog and taxonomy
- Primary features work without JavaScript
- Dark Mode

## notable changes made by this fork
* removed comments
* removed blog posts (this is a wiki after all)
* removed js service worker
* removed multilanguage support
* removed google analytics integration
* removed opengraph integration
* removed forced use of proper capitalization
* simplfied the directory structure
* only menu structure is flat file structure in `content/`
* as well as stylistic changes


## Requirements

- Hugo 0.68 or higher
- Hugo extended version, read more [here](https://gohugo.io/news/0.48-relnotes/)

## Installation

### Install as git submodule
Navigate to your hugo project root and run:

```
git submodule add https://github.com/nunq/cleanwiki themes/cleanwiki
```

## Menu

the theme will render pages from the `content/` section as a menu in a tree structure.  
You can set `title` and `weight` in the front matter of pages to adjust the order and titles in the menu.

## Configuration

### Site Configuration

There are a few configuration options that you can add to your `config.toml` file.  
You can also see the `yaml` example [here](https://github.com/alex-shpak/hugo-book/blob/master/exampleSite/config.yaml).

```toml
# (Optional) Set this to true if you use capital letters in file names
disablePathToLower = true

# (Optional) Set this to true to enable 'Last Modified by' date and git author
#  information on 'doc' type pages.
enableGitInfo = true

[params]
  # (Optional, default light) Sets color theme: light, dark or auto.
  # Theme 'auto' switches between dark and light modes based on browser/os preferences
  BookTheme = 'light'

  # (Optional, default true) Controls table of contents visibility on right side of pages.
  # Start and end levels can be controlled with markup.tableOfContents setting.
  # You can also specify this parameter per page in front matter.
  BookToC = true

  # (Optional, default none) Set the path to a logo for the book. If the logo is
  # /static/logo.png then the path would be 'logo.png'
  BookLogo = 'logo.png'

  # Specify section of content to render as menu
  BookSection = '/'

  # Set source repository location.
  # Used for 'Last Modified' and 'Edit this page' links.
  BookRepo = 'https://github.com/user/repo'

  # Specifies commit portion of the link to the page's last modified commit hash for 'doc' page
  # type.
  # Required if 'BookRepo' param is set.
  # Value used to construct a URL consisting of BookRepo/BookCommitPath/<commit-hash>
  # Github uses 'commit', Bitbucket uses 'commits'
  BookCommitPath = 'commit'

  # Enable 'Edit this page' links for 'doc' page type.
  # Disabled by default. Uncomment to enable. Requires 'BookRepo' param.
  # Path must point to the site directory.
  BookEditPath = 'edit/branch/path'

  # (Optional, default January 2, 2006) Configure the date format used on the pages
  # - In git information
  # - In blog posts
  BookDateFormat = 'Jan 2, 2006'

  # (Optional, default true) Enables search function with flexsearch,
  # Index is built on fly, therefore it might slowdown your website.
  # Configuration for indexing can be adjusted in i18n folder per language.
  BookSearch = true

  # /!\ This is an experimental feature, might be removed or changed at any time
  # (Optional, experimental, default false) Enables portable links and link checks in markdown pages.
  # Portable links meant to work with text editors and let you write markdown without {{< relref >}} shortcode
  # Theme will print warning if page referenced in markdown does not exists.
  BookPortableLinks = true
```

### Page Configuration

You can specify additional params in the front matter of individual pages:

```toml
# Set page weight to re-arrange items in file-tree menu (if BookMenuBundle not set)
weight = 10

# (Optional) Set to 'true' to mark page as flat section in file-tree menu (if BookMenuBundle not set)
bookFlatSection = false

# (Optional) Set to hide nested sections or pages at that level. Works only with file-tree menu mode
bookCollapseSection = true

# (Optional) Set true to hide page or section from side menu (if BookMenuBundle not set)
bookHidden = false

# (Optional) Set 'false' to hide ToC from page
bookToC = true

# (Optional) Set to 'false' to exclude page from search index.
bookSearchExclude = true
```

### Partials

There are layout partials available for you to easily override components of the theme in `layouts/partials/`.

In addition to this, there are several empty partials you can override to easily add/inject code.

| Empty Partial                                      | Placement                                   |
| -------------------------------------------------- | ------------------------------------------- |
| `layouts/partials/inject/head.html`           | Before closing `<head>` tag                 |
| `layouts/partials/inject/body.html`           | Before closing `<body>` tag                 |
| `layouts/partials/inject/footer.html`         | After page footer content                   |
| `layouts/partials/inject/menu-before.html`    | At the beginning of `<nav>` menu block      |
| `layouts/partials/inject/menu-after.html`     | At the end of `<nav>` menu block            |
| `layouts/partials/inject/content-before.html` | Before page content                         |
| `layouts/partials/inject/content-after.html`  | After page content                          |
| `layouts/partials/inject/toc-before.html`     | At the beginning of table of contents block |
| `layouts/partials/inject/toc-after.html`      | At the end of table of contents block       |

### Extra Customisation

| File                     | Description                                                                           |
| ------------------------ | ------------------------------------------------------------------------------------- |
| `static/favicon.png`     | Override default favicon                                                              |
| `assets/_custom.scss`    | Customise or override scss styles                                                     |
| `assets/_variables.scss` | Override default SCSS variables                                                       |
| `assets/_fonts.scss`     | Replace default font with custom fonts (e.g. local files or remote like google fonts) |
| `assets/mermaid.json`    | Replace Mermaid initialization config                                                 |

### Plugins

There are a few features implemented as plugable `scss` styles. Usually these are features that don't make it to the core but can still be useful.

| Plugin                            | Description                                                 |
| --------------------------------- | ----------------------------------------------------------- |
| `assets/plugins/_numbered.scss`   | Makes headings in markdown numbered, e.g. `1.1`, `1.2`      |
| `assets/plugins/_scrollbars.scss` | Overrides scrollbar styles to look similar across platforms |

To enable plugins, add `@import "plugins/{name}";` to `assets/_custom.scss` in your website root.

## Shortcodes

see original hugo-book documentation:

- [Buttons](https://hugo-book-demo.netlify.app/docs/shortcodes/buttons/)
- [Columns](https://hugo-book-demo.netlify.app/docs/shortcodes/columns/)
- [Details](https://hugo-book-demo.netlify.app/docs/shortcodes/details/)
- [Hints](https://hugo-book-demo.netlify.app/docs/shortcodes/hints/)
- [KaTeX](https://hugo-book-demo.netlify.app/docs/shortcodes/katex/)
- [Mermaid](https://hugo-book-demo.netlify.app/docs/shortcodes/mermaid/)
- [Tabs](https://hugo-book-demo.netlify.app/docs/shortcodes/tabs/)

By default, Goldmark trims unsafe outputs which might prevent some shortcodes from rendering. It is recommended to set `markup.goldmark.renderer.unsafe=true` if you encounter problems.

```toml
[markup.goldmark.renderer]
  unsafe = true
```

If you are using `config.yaml` or `config.json`, consult the [configuration markup](https://gohugo.io/getting-started/configuration-markup/)


## etc

[Extra credits to hugo-book contributors](https://github.com/alex-shpak/hugo-book/graphs/contributors)

copyright for portions of this project are held by Alex Shpak, 2018 as part of
their project [hugo-book](https://github.com/alex-shpak/hugo-book). all copyright later than commit `98d19b8e95019534622fd4c5eae707423730df2c`, except patches merged from upstream is held by me under the MIT License, see LICENSE file.

