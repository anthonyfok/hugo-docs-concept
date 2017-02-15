---
title: Archetypes
linktitle:
description: Archetypes allow you to create and set default parameters from the command line according to the content section.
date: 2017-02-01
publishdate: 2017-02-01
lastmod: 2017-02-01
tags: [archetypes,generators,metadata,front matter]
categories: [content]
weight: 50
draft: false
slug:
aliases: []
notes:
---

**Archetypes** are content files in the [archetypes directory][] of your project that contain pre-configured [front matter][] for your site's [content types][]. Archetypes facilitate consistent metadata in your website's content and allow content authors to quickly generate instances of a content type via the `hugo new` command.

Hugo's generator assumes your working directory is the content folder at the root of your project. Hugo is able to infer the appropriate archetype by assuming the content type from the content section passed to the CLI command:

```bash
hugo new [content-section/file-name.md]
```

We can use this pattern to create a new `.md` file in the `posts` section of the [example site][]:

{{% input "archetype-example.sh" %}}
```bash
hugo new posts/my-first-post.md
```
{{% /input %}}

{{% note "Override Content Type in a New File" %}}
To override the content type Hugo infers from `[content-section]`, you can include the `--kind` flag at the end of the `hugo new` command.
{{% /note %}}

If you were to run this command in a new site that does not contain any default or custom archetypes, Hugo will create the following file.

{{% output "content/posts/my-first-post.md" %}}
```toml
+++
date = "2017-02-01T19:20:04-07:00"
title: my first post
+++
```
{{% /output %}}

Note that if you do not already have a `posts` directory in `content`, Hugo will create both `content/posts/` and `content/posts/my-first-post.md`.

`date` and `title` are the key-values that ship with Hugo and are therefore included in *all* content files created with the Hugo CLI. `title` is generated from the new content's filename. `date` is generated in [RFC 3339 format][] by way of Golang's [`now()`][] function, which returns the current time.

Two key-values are often not enough for effective content management of larger websites. As such, Hugo provides a simple mechanism for extending these key-values through default and custom archetypes.

## Lookup Order for Archetypes

Similar to the lookup order for [templates in the layouts folder][], Hugo looks for a default file before falling back on the base/internal archetype. For the `my-first-post.md` example, Hugo looks for the new content's archetype file in the following order:

1. `archetypes/posts.md`
2. `archetypes/default.md`
3. `themes/theme-name/archetypes/posts.md`
4. `themes/theme-name/archetypes/default.md`
5. `_internal` (i.e., `title` and `date`)

{{% note "Using a Theme Archetype" %}}
If you wish to use archetypes that ship with a theme, `theme` must be specified in your [configuration file](/project-organization/configuration/).
{{% /note %}}

## Choosing Your Front Matter Format

By default, `hugo new` content files include front matter in the TOML format regardless of the format used in `archetypes/*md`.

You can specify a different default format in your site [configuration file][] file using the `metaDataFormat` directive. Possible values are `toml`, `yaml`, and `json`.

## Creating a Default Archetype

Default archetypes are convenient if your content's front matter stays consistent across multiple [content sections][].

The [example site][] includes `tags` and `categories` as [taxonomies][]. If we assume that all content files will require these two key-values, we can create a `default.md` archetype that *extends* Hugo's base archetype. In this example, we are including "golang" and "hugo" as tags and "web development" as a category.

{{% input "archetypes/default.md" %}}
```toml
+++
tags = ["golang", "hugo"]
categories = ["web development"]
+++
```
{{% /input %}}

{{% caution "EOL Characters in Text Editors"%}}
If you get an `EOF error` when using `hugo new`, add a carriage return after the closing `+++` or `---` for your TOML or YAML front matter, respectively. (See [troubleshooting](/troubleshooting/eof-error/).)
{{% /caution %}}

## Using the Default Archetype

With an `archetypes/default.md` in place, we can use the CLI to create a new post in the `posts` content section:

{{% input "new-post-from-default.sh" %}}
```bash
$ hugo new posts/my-new-post.md
```
{{% /input %}}

Hugo then creates a new markdown file with the following front matter:

{{% output "content/posts/my-new-post.md" %}}
```toml
+++
categories = ["web development"]
date = "2017-02-01T19:20:04-07:00"
tags = ["golang", "hugo"]
title = "my new post"
+++
```
{{% /output %}}

We see that the `title` and `date` key-values have been added in addition to the `tags` and `categories` key-values from `archetypes/default.md`.

{{% note "Ordering of Front Matter" %}}
You may notice that content files created with `hugo new` do not observe the order of the key-values specified in your archetype files and instead list your front matter alphabetically. This is a known issue ({{< issue 452 >}}).
{{% /note %}}

## Creating Custom Archetypes

Suppose the example site's `posts` section requires more sophisticated front matter than what has been specified in `archetypes/default.md`. We can create a custom archetype for our posts at `archetypes/posts.md` that includes the full set of front matter.

{{% input "archetypes/posts.md"%}}
```toml
+++
subtitle = ""
author = ""
publishdate = ""
description = ""
tags = ""
categories = ""
+++
```
{{% /input %}}

## Using Custom Archetypes

With an `archetypes/posts.md` in place, we can use the CLI to create a new posts with custom `posts` metadata in the `posts` content section:

{{% input "new-post-from-custom.sh" %}}
```bash
$ hugo new posts/post-from-custom.md
```
{{% /input %}}

This time, Hugo recognizes our custom `archetypes/posts.md` archetype and uses it instead of `archetypes/default.md`. The generated file will now include the full list of front matter parameters, as well as the base archetype's `title` and `date`.

{{% output "content/posts/post-from-custom.md" %}}
```toml
+++
author = ""
categories = ""
date = 2017-02-13T17:24:43-08:00
description = ""
publishdate = ""
subtitle = ""
tags = ""
title = post from custom
+++
```
{{% /output %}}

[archetypes directory]: /project-organization/directory-structure/
[`now()`]: http://golang.org/pkg/time/#Now
[configuration file]: /project-organization/configuration/
[content sections]: /content-sections/
[content types]: /content-management/content-types/
[example site]: /getting-started/
[front matter]: /content-management/front-matter/
[RFC 3339 format]: https://www.ietf.org/rfc/rfc3339.txt
[taxonomies]: /content-management/taxonomies/
[templates in the layouts folder]: /templates/base-templates-and-blocks/
[templates]: /templates/
