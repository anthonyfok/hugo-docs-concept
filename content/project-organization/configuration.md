---
title: Configuration
linktitle:
description: Scaffolding new projects, configuration, and source organization.
date: 2017-01-02
tags: [configuration,fundamentals]
publishdate: 2017-01-02
lastmod: 2017-01-02
weight: 10
draft: false
slug:
aliases: [/overview/source-directory/]
notes:
---

The [directory structure][] of a Hugo website&mdash;or more precisely, the source organization of files containing the website's content and templates&mdash;provides most of the configuration information that Hugo needs in order to statically generate a finished website.

Therefore, many websites wouldn't actually need a configuration file. This is because Hugo is designed to recognize certain typical usage patterns (and expects them, by default).

Nevertheless, Hugo searches for a configuration file in the root of your website's source directory as a default behavior. First, it looks for a `./config.toml` file. If that's not present, it will seek a `./config.yaml` file,
followed by a `./config.json` file.

In this `config` file, you can include precise directions to Hugo regarding how it should render your website, control your website's menus, and arbitrarily define site-wide parameters specific to your project.

## Configuration in YAML

The following is a typical example of a YAML configuration file. Note the document opens with 3 hyphens and closes with 3 periods. The values nested under `params:` will populate the [`.Site.Params`][] variable for use in [templates][]:

{{% input "config.yml" %}}
```yaml
---
baseURL: "http://yoursite.example.com/"
title: "Yoyodyne Widget Blogging"
footnoteReturnLinkContents: "↩"
permalinks:
  post: /:year/:month/:title/
params:
  Subtitle: "Spinning the cogs in the widgets"
  AuthorName: "John Doe"
  GitHubUser: "spf13"
  ListOfFoo:
    - "foo1"
    - "foo2"
  SidebarRecentLimit: 5
...
```
{{% /input %}}

## Configuration in TOML

The following is an example of a TOML configuration file. The values under `[params]` will populate the `.Site.Params` variable for use in [templates][]:

```toml
contentDir = "content"
layoutDir = "layouts"
publishDir = "public"
buildDrafts = false
baseURL = "http://yoursite.example.com/"
canonifyURLs = true

[taxonomies]
  category = "categories"
  tag = "tags"

[params]
  description = "Tesla's Awesome Hugo Site"
  author = "Nikola Tesla"
```

## All Configuration Variables, YAML

The following is the full list of Hugo-defined variables in a example YAML file. The values provided in this example represent the default values used by Hugo if not otherwise specified.

{{% input "config.yml" %}}
```yaml
---
archetypeDir:               "archetypes"
# hostname (and path) to the root, e.g. http://spf13.com/
baseURL:                    ""
# include content marked as draft
buildDrafts:                false
# include content with publishdate in the future
buildFuture:                false
# include content already expired
buildExpired:               false
# enable this to make all relative URLs relative to content root. Note that this does not affect absolute URLs.
relativeURLs:               false
canonifyURLs:               false
# config file (default is path/config.yaml|json|toml)
config:                     "config.toml"
contentDir:                 "content"
dataDir:                    "data"
defaultExtension:           "html"
defaultLayout:              "post"
# Missing translations will default to this content language
defaultContentLanguage:     "en"
# Renders the default content language in subdir, e.g. /en/. The root directory / will redirect to /en/
defaultContentLanguageInSubdir: false
disableLiveReload:          false
# Do not build RSS files
disableRSS:                 false
# Do not build Sitemap file
disableSitemap:             false
# Enable GitInfo feature
enableGitInfo:              false
# Build robots.txt file
enableRobotsTXT:            false
# Do not render 404 page
disable404:                 false
# Do not inject generator meta tag on homepage
disableHugoGeneratorInject: false
# Do not make the url/path to lowercase
disablePathToLower:         false
# edit new content with this editor, if provided
editor:                     ""
# Enable Emoji emoticons support for page content.
# See www.emoji-cheat-sheet.com
enableEmoji:                false
# Show a placeholder instead of the default value or an empty string if a translation is missing
enableMissingTranslationPlaceholders: false
footnoteAnchorPrefix:       ""
footnoteReturnLinkContents: ""
# google analytics tracking id
googleAnalytics:            ""
# if true, auto-detect Chinese/Japanese/Korean Languages in the content. (.Summary and .WordCount can work properly in CJKLanguage)
hasCJKLanguage:             false
languageCode:               ""
layoutDir:                  "layouts"
# Enable Logging
log:                        false
# Log File path (if set, logging enabled automatically)
logFile:                    ""
# "toml","yaml", or "json"
metaDataFormat:             "toml"
newContentEditor:           ""
# Don't sync permission mode of files
noChmod:                    false
# Don't sync modification time of files
noTimes:                    false
# Pagination
paginate:                   10
paginatePath:               "page"
# See "content-management/permalinks"
permalinks:
# Pluralize titles in lists using inflect
pluralizeListTitles:        true
# Preserve special characters in taxonomy names ("Gérard Depardieu" vs "Gerard Depardieu")
preserveTaxonomyNames:      false
# filesystem path to write files to
publishDir:                 "public"
# enables syntax guessing for code fences without specified language
pygmentsCodeFencesGuessSyntax: false
# color-codes for highlighting derived from this style
pygmentsStyle:              "monokai"
# true: use pygments-css or false: color-codes directly
pygmentsUseClasses:         false
# default sitemap configuration map
sitemap:
# filesystem path to read files relative from
source:                     ""
staticDir:                  "static"
# display memory and timing of different steps of the program
stepAnalysis:               false
# theme to use (located by default in /themes/THEMENAME/)
themesDir:                  "themes"
theme:                      ""
title:                      ""
# if true, use /filename.html instead of /filename/
uglyURLs:                   false
# verbose output
verbose:                    false
# verbose logging
verboseLog:                 false
# watch filesystem for changes and recreate as needed
watch:                      true
taxonomies:
  - category:               "categories"
  - tag:                    "tags"
---
```
{{% /input %}}

## All Configuration Variables, TOML

The following is the full list of Hugo-defined variables in a example YAML file. The values provided in this example represent the default values used by Hugo if not otherwise specified.

{{% input "config.toml" %}}
```toml
---
archetypeDir =                "archetypes"
# hostname (and path) to the root, e.g. http://spf13.com/
baseURL =                     ""
# include content marked as draft
buildDrafts =                 false
# include content with publishdate in the future
buildFuture =                 false
# include content already expired
buildExpired =                false
# enable this to make all relative URLs relative to content root. Note that this does not affect absolute URLs.
relativeURLs =                false
canonifyURLs =                false
# config file (default is path/config.yaml|json|toml)
config =                     "config.toml"
contentDir =                  "content"
dataDir =                     "data"
defaultExtension =            "html"
defaultLayout =               "post"
# Missing translations will default to this content language
defaultContentLanguage =      "en"
# Renders the default content language in subdir, e.g. /en/. The root directory / will redirect to /en/
defaultContentLanguageInSubdir =  false
disableLiveReload =           false
# Do not build RSS files
disableRSS =                  false
# Do not build Sitemap file
disableSitemap =              false
# Enable GitInfo feature
enableGitInfo =               false
# Build robots.txt file
enableRobotsTXT =             false
# Do not render 404 page
disable404 =                  false
# Do not inject generator meta tag on homepage
disableHugoGeneratorInject =  false
# Do not make the url/path to lowercase
disablePathToLower =          false
# edit new content with this editor, if provided
editor =                      ""
# Enable Emoji emoticons support for page content.
# See www.emoji-cheat-sheet.com
enableEmoji =                 false
# Show a placeholder instead of the default value or an empty string if a translation is missing
enableMissingTranslationPlaceholders = false
footnoteAnchorPrefix =        ""
footnoteReturnLinkContents =  ""
# google analytics tracking id
googleAnalytics =             ""
# if true, auto-detect Chinese/Japanese/Korean Languages in the content. (.Summary and .WordCount can work properly in CJKLanguage)
hasCJKLanguage =              false
languageCode =                ""
layoutDir =                   "layouts"
# Enable Logging
log =                         false
# Log File path (if set, logging enabled automatically)
logFile =                     ""
# "toml","yaml", or "json"
metaDataFormat =              "toml"
newContentEditor =            ""
# Don't sync permission mode of files
noChmod =                     false
# Don't sync modification time of files
noTimes =                     false
# Pagination
paginate =                    10
paginatePath =                "page"
# See "content-management/permalinks"
permalinks =
# Pluralize titles in lists using inflect
pluralizeListTitles =         true
# Preserve special characters in taxonomy names ("Gérard Depardieu" vs "Gerard Depardieu")
preserveTaxonomyNames =       false
# filesystem path to write files to
publishDir =                  "public"
# enables syntax guessing for code fences without specified language
pygmentsCodeFencesGuessSyntax = false
# color-codes for highlighting derived from this style
pygmentsStyle =               "monokai"
# true: use pygments-css or false: color-codes directly
pygmentsUseClasses =          false
# default sitemap configuration map
sitemap =
# filesystem path to read files relative from
source =                      ""
staticDir =                   "static"
# display memory and timing of different steps of the program
stepAnalysis =                false
# theme to use (located by default in /themes/THEMENAME/)
themesDir =                   "themes"
theme =                       ""
title =                       ""
# if true, use /filename.html instead of /filename/
uglyURLs =                    false
# verbose output
verbose =                     false
# verbose logging
verboseLog =                  false
# watch filesystem for changes and recreate as needed
watch =                       true
[taxonomies]
  category = "categories"
  tag = "tags"
---
```
{{% /input %}}

## Configure Through Environmental Variables

In addition to the 3 configuration file options already mentioned, website configuration can be accomplished through operating system environment variables.

For example, the following command will effectively set a website's title on Unix-like systems:

```bash
$ env HUGO_TITLE="Some Title" hugo
```

{{% note "Setting Environment Variables" %}}
names must be prefixed with `HUGO_` when setting environment variables through operating system environment variables.
{{% /note %}}

## Ignoring Files When Rendering

The following statement inside `./config.toml` will cause Hugo to ignore files
ending with `.foo` and `.boo` when rendering:

```toml
ignoreFiles = [ "\\.foo$", "\\.boo$" ]
```
The above is a list of regular expressions. Note that the backslash (`\`) character is escaped in this example to keep TOML happy.

## Additional Resources

* [TOML Spec][]
* [YAML Spec][]
* [JSON Spec][]

[`.Site.Params`]: /variables-and-params/
[directory structure]: /project-organization/directory-structure
[JSON Spec]: /documents/ecma-404-json-spec.pdf
[templates]: /templates
[TOML Spec]: https://github.com/toml-lang/toml
[YAML Spec]: http://yaml.org/spec/