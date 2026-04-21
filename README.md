# Hugo Natrium
This is a simple, responsive blog theme for [Hugo](https://gohugo.io/) based on [Lithium](https://github.com/jrutheiser/hugo-lithium-theme.git). [Hugo Natrium](https://github.com/mobybit/hugo-natrium-theme) was created by Tim ([mobybit](https://github.com/mobybit)). This fork of the theme is actively maintained (for new Hugo version compatibility).

## Changes
Changes introduced to make this theme compatible with the latest Hugo versions (0.156 and newer).

```diff
-These changes break the theme in older Hugo versions (0.155 and prior).
```
**Upgrading to at least Hugo 0.156 is required to maintain functionality.** The changes include:

* Replace instances of *.URL* with *.RelPermalink* (fixes "*WARN Page.URL is deprecated and will be removed in a future release. Use .Permalink or .RelPermalink.*")
* Replace instances of *.Hugo* with *hugo* (fixes "*WARN Page.Hugo is deprecated and will be removed in a future release. Use the global hugo function.*")
* Replace instances of *.RSSLink* with *.OutputFormats.Get "RSS"* (fixes: "*WARN Page.RSSLink is deprecated and will be removed in a future release. Use the Output Format's link.*")
* Replace instances of *.Data.Pages* with *.Site.RegularPages* (fixes "*Error <.Paginate>: error calling Paginate: cannot convert type page.PagesGroup to Pages*")
* Replace instances of *.Site.DisqusShortname* with *.Site.Config.Services.Disqus.Shortname* (fixes "*WARN deprecated: .Site.DisqusShortname was deprecated in Hugo v0.120.0 and will be removed in a future release.*")
* Replace *paginate =* with *pagination.pagerSize* in config.toml (fixes "*WARN  deprecated: site config key paginate was deprecated in Hugo v0.128.0 and will be removed in a future release. Use pagination.pagerSize instead.*")
* Replace *.Summary | html* with *.Summary | plainify | htmlUnescape* in layouts/rss.xml (fixes XML/RSS feed rendering issues)
* Replace instances of *.Site.Author.name* and *.Site.Author.email* with *.Site.Params.Author* and *.Site.Params.email* in layouts/rss.xml (fixes "Can't evaluate field Author in type page.Site")

Natrium includes: taxonomies (categories, tags), static footer, new fonts (Roboto Mono, Font Awesome), local fonts, comments (Disqus), syntax highlighting, better support for code, img and RSS, pagination, multiple design optimizations, i18n, 404.html...


## Features
- Blog
- Disqus (comments)
- Responsive
- Privacy (no Google)
- Taxonomies
- Syntax highlighting
- Pagination


## Installation
Run the following inside your Hugo site folder:

```
$ mkdir themes
$ cd themes
$ git clone https://github.com/mobybit/hugo-natrium-theme
```


## Configuration
Take a look at the sample [config.toml](https://github.com/neil-sabol/hugo-natrium-theme/blob/master/exampleSite/config.toml)
file located in the [exampleSite](https://github.com/neil-sabol/hugo-natrium-theme/blob/master/exampleSite) folder.


## Content Types

### Post
Used for blog posts. Blog posts are listed on the homepage.

Run `hugo new post/<post-name>.md` to create a post.

### Page
Used for site pages.

Run `hugo new page/<page-name>.md` to create a page.


## Syntax highlighting
Natrium is using [Chroma](https://gohugo.io/content-management/syntax-highlighting/) and `pygmentsStyle = "native"` by default. If you would like to use another style you have to adjust the colors in `pre` in main.css.


## Integration testing
`exampleSite\exampleSite.Tests.ps1` contains basic PowerShell [Pester](https://github.com/pester/Pester) tests that I use to validate this theme as new Hugo versions are released. To run the tests, you will need Pester 5+:

```
Install-Module -Name Pester -Force -SkipPublisherCheck
```

Once installed, the Pester tests can be invoked as follows:

```
cd <path-to-theme>\exampleSite
invoke-pester -Output Detailed
```


## License
The code is available under the [MIT License](https://github.com/mobybit/hugo-natrium-theme/blob/master/LICENSE.md). 

Natrium is using [Font Awesome](http://fontawesome.io) by Dave Gandy ([SIL OFL 1.1](http://scripts.sil.org/OFL)). Realated files (CSS, LESS, SCSS) are licensed under the [MIT License](http://opensource.org/licenses/mit-license.html).

Other used fonts are [Merriweather](https://github.com/EbenSorkin/Merriweather) by Sorkin Type (Copyright © 2016 The Merriweather Project, [SIL OFL 1.1](http://scripts.sil.org/OFL)), [Lato](http://www.latofonts.com/) by Łukasz Dziedzic (Copyright © 2010-2014 by tyPoland Lukasz Dziedzic, [SIL OFL 1.1](http://scripts.sil.org/OFL)) and [Roboto Mono](https://github.com/google/roboto/) by Christian Robertson (Copyright © 2015 Google Inc., [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0)).

Special thanks to [Artem Sidorenko](https://www.sidorenko.io/post/2017/07/nice-tagcloud-with-hugo/) (tag cloud).

The content of the example site is generated with [Metamorphosum](http://metaphorpsum.com/) (Copyright © 2014 Kyle Stetz, [MIT License](https://github.com/kylestetz/metaphorpsum/blob/master/LICENSE.md)).
