---
title: numfmt
linktitle: NumFmt
description: "Formats a number with a given precision using the requested `decimal`, `grouping`, and `negative` characters."
godocref: ""
workson: []
date: 2017-02-01
publishdate: 2017-02-01
lastmod: 2017-02-01
categories: [functions]
tags: [numbers]
menu:
  docs:
    parent: "functions"
toc: false
ns: "lang"
signature: ["NumFmt <decimal> <grouping> <negative> <precision> <number>"]
workson: []
hugoversion:
relatedfuncs: []
deprecated: false
draft: false
aliases: []
comments:
---

`lang.NumFmt` formats a number with a given precision using the requested `decimal`, `grouping`, and `negative` characters. The default options value is `- . ,`.

Numbers greater than or equal to 5 are rounded up. For example, if precision is set to `0`, `1.5` becomes `2`, and `1.4` becomes `1`.

```
{{ lang.NumFmt "," "." "-" 2 12345.6789 }} → 12.345,68
{{ lang.NumFmt "." "" "-" 6 -12345.6789 }} → -12345.678900
{{ lang.NumFmt "." "," "-" 0 -12345.6789 }} → -12,346
{{ -98765.4321 | lang.NumFmt "." "," "-" 2 }} → -98,765.43
```
