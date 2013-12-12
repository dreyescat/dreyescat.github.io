---
layout: default
title: Include shared page header and footer
---

# {{ page.title }}

I have a header and a footer that I would like to keep as fixed sections across all pages. As I think these small pages are susceptible to be reused in other pages as fragments or partials, I am going to create them as Jekyll [includes](http://jekyllrb.com/docs/templates/#includes).

    vi vi _includes/header.html

    <h1>dreyescat.github.io</h1>
    <p>Howtos, code snippets, comments, ...</p>
    <p>Stuff I think it's worth to keep and might be useful to others</p>


    vi _includes/footer.html

    <p>This blog is maintained by <a href="https://github.com/dreyescat">dreyescat</a></p>
    <p><small>Hosted on GitHub Pages &mdash; Theme by <a href="https://github.com/orderedlist">orderedlist</a></small></p>

Now, as I want to include those fragments on all my pages, I am going to modify the `default.html` layout. Just wrap {% raw %}{{ content }}{% endraw %} between a `header` and a `footer`.

    vi _layout/default.html

    {% raw %}
    ...
    <div class="wrapper">
      <header>
        {% include header.html %}
      </header>
      <section>
        {{ content }}
      </section>
      <footer>
        {% include footer.html %}
      </footer>
    </div>
    ...
    {% endraw %}
