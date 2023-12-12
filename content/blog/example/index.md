---
title: "Example Post"
description: "Just an example post."
summary: ""
date: 2023-09-07T16:27:22+02:00
lastmod: 2023-09-07T16:27:22+02:00
draft: false
weight: 50
categories: []
tags: []
contributors: []
pinned: false
homepage: false
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

<a href="images/CIC_Buchansicht-header.jpg" data-dimbox="my-gallery">

  ![CALL IT CORONA Buchansicht](images/CIC_Buchansicht-header.jpg)

</a>

## Gallery Shortcode

Just a quick example to help you get started.

I've added `layouts/shortcodes/gallery.html` with the following contents:

```html
<div class="{{ .Get "class" }}">
  {{- $images := .Page.Resources.ByType "image" -}}
  {{- $featured := $images.GetMatch "*feature*" -}}
  {{- if not $featured }}{{ $featured = $images.GetMatch "{*cover*,*thumbnail*}" }}{{ end -}}
  {{- if $featured -}}
    {{- partial "picture" (dict "page" .Page "src" $featured) }}
  {{ end -}}
</div>
```

Note that you'll need `.Page` in stead of just [the dot](https://www.regisphilibert.com/blog/2018/02/hugo-the-scope-the-context-and-the-dot/) to make it work :

```html
{{- $images := .Page.Resources.ByType "image" -}}
```

```html
{{- partial "picture" (dict "page" .Page "src" $featured) }}
```

Use the shortcode:

```md
{{</* gallery class="content-gallery" */>}}
```

this will generate into:

{{< gallery class="content-gallery" >}}

## Render Hook

```md
![CALL IT CORONA Buchansicht](images/CIC_Buchansicht-header.jpg)
```

![CALL IT CORONA Buchansicht](images/CIC_Buchansicht-header.jpg)

## Shortcode

```md
{{</* img src="images/CIC_Buchansicht-header.jpg" alt="CALL IT CORONA Buchansicht" */>}}
```

{{< img src="images/CIC_Buchansicht-header.jpg" alt="CALL IT CORONA Buchansicht" >}}
