---
layout: default
title: Free posts URIs from html extension
---
# {{ page.title }}

## Why

I am not comfortable with URIs having file extensions.

I don't like to couple how a resource is identified (URI) with the format used to represent the resource (HTML, XML, JSON, etc.). I prefer using the [content-type](http://www.w3.org/Protocols/rfc1341/4_Content-Type) and rely on the [content negotiation mechanism](http://en.wikipedia.org/wiki/Content_negotiation) to choose the proper representation of the resource.

I like the [W3C](http://www.w3.org/Consortium/) idea that [Cool URIs don't change](http://www.w3.org/Provider/Style/URI.html) althought not being strictly followed by themselves, at least in this particular URI. Notice the **.html** at the end of the URI (`http://www.w3.org/Provider/Style/URI.html`). Excusable since the document is from 1998 and it was probably a style recommendation not applied yet in those days. Anyway, if I remove the **.html** from the URI (`http://www.w3.org/Provider/Style/URI`) it works too. The language will probably depend on the one configured on the browser. Content negotiation in action!

## How

This sense of URI *immutability* is known as [permalink](http://en.wikipedia.org/wiki/Permalink) in the blogosphere. Jekyll supports a [flexible way to build permalinks](http://jekyllrb.com/docs/permalinks/). I picked the **pretty** permalink style adding the line below in the `_config.yml`:

    permalink: pretty

