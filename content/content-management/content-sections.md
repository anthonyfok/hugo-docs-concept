---
title: Content Sections
linktitle: Content Sections
description:
date: 2017-02-01
publishdate: 2017-02-01
lastmod: 2017-02-01
tags: [lists,sections,content,types,organization]
weight: 30
draft: false
slug:
aliases: [/content-management/sections,/content/sections/]
notes:
---

## Content Organization

Hugo believes that you organize your content with a purpose. The same structure that works to organize your source content is used to organize the rendered site (see [directory structure][]).

Following this pattern, Hugo uses the top level of your content organization as the **content section**.

The [example site][] used throughout the Hugo docs includes three sections: "authors," "events," and "posts". The following illustrates both the source organization and the default URL structure for the rendered files:

```bash
.
└── content
    ├── authors
    |   ├── _index.md     // <- example.com/authors/
    |   ├── john-doe.md   // <- example.com/authors/john-doe/
    |   └── jane-doe.md   // <- example.com/authors/jane-doe/
    └── events
    |   ├── _index.md     // <- example.com/events/
    |   ├── event-1.md    // <- example.com/events/event-1/
    |   ├── event-2.md    // <- example.com/events/event-2/
    |   └── event-3.md    // <- example.com/events/event-3/
    └── posts
    |   ├── _index.md     // <- example.com/posts/
    |   ├── event-1.md    // <- example.com/posts/event-1/
    |   ├── event-2.md    // <- example.com/posts/event-2/
    |   ├── event-3.md    // <- example.com/posts/event-3/
    |   ├── event-4.md    // <- example.com/posts/event-4/
    |   └── event-5.md    // <- example.com/posts/event-5/
```

## Content Section Lists

Hugo will automatically create pages for each section root that list all of the content in that section. See [List and Section Page Templates][] for details on customizing the way these pages are rendered.

As of Hugo v0.18, section pages can also have a content file and front matter. These section content files must be placed in their corresponding section folder and named `_index.md` in order for Hugo to correctly render the front matter and content.

{{% warning "`index.md` vs `_index.md`" %}}
Hugo themes developed before v0.18 often used an `index.md` in a content section as a hack to emulate the behavior of `_index.md`. The hack may work...*sometimes*. The order of page rendering can be unpredictable in Hugo. What works now may fail to render appropriately once you begin adding more content to your site. It is *strongly advised* to use `_index.md` the *preferred* content section index page. **Note:** `_index.md`'s layout is a [list template](/templates/list-and-section-templates/).
{{% /warning %}}

## Content Section vs Content Types

By default, everything created within a section will use the [content type][] that matches the section name. For example, Hugo will assume that `posts/post-1.md` has a `posts` content type and if using an [archetype][] will generate front matter according to `archetypes/posts.md`.

[archetype]: /content-management/archetypes/
[content type]: /content-management/content-types/
[example site]: /getting-started/
[directory structure]: /project-organization/directory-structure/


