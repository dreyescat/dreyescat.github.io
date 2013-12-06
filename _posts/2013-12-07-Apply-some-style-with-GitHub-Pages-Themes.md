---
layout: default
title: Apply some style with GitHub Pages Themes
---
# {{ page.title }} 

Time to add some basic style. I have found that [Minimal Theme](https://github.com/orderedlist/minimal) is a good candidate. It is one of the [GitHub Pages Themes](https://github.com/blog/1081-instantly-beautiful-project-pages).

Clone the minimal repository. I will assume it is cloned next to the website repository, that is, both repositories having the same parent folder.

    cd dreyescat.github.io
    git clone https://github.com/orderedlist/minimal.git ../minimal

Prepare an assets folder to hold all the website resources (images, javascripts, stylesheets, etc.).

    mkdir -p assets/javascripts
    mkdir -p assets/stylesheets

Copy the minimal theme assets.

    cp ../minimal/javascripts/* assets/javascripts
    cp ../minimal/stylesheets/* assets/stylesheets

Now we are ready to use those assets in our pages. But wait, instead of just copying the same boilerplate every time, we can just follow the [DRY](http://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle. Templating is our good ally. All these templates that wraps posts goes into the `_layout` folder.

    mkdir _layout

Create a default layout.

    vi _layout/default.html

    {% raw %}
    <!doctype html>
    <html lang="en">
      <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="chrome=1">
        <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
        <title>{{ page.title }}</title>
    
        <link rel="stylesheet" href="assets/stylesheets/styles.css">
        <link rel="stylesheet" href="assets/stylesheets/pygment_trac.css">
        <!--[if lt IE 9]>
        <script src="//html5shiv.googlecode.com/svn/trunk/html5.js"></script>
        <![endif]-->
      </head>
      <body>
        {{ content }}
        <script src="assets/javascripts/scale.fix.js"></script>
      </body>
    </html>
    {% endraw %}
    
Apply the default layout to our `index.html`. Here is when [front-matter](http://jekyllrb.com/docs/frontmatter/) comes into scene.

    vi index.html

    {% raw %}
    ---
    layout: default
    ---
    <h1>Recent Posts</h1>
    <ul>
      {% for post in site.posts %}
        <li>
          <a href="{{ post.url }}">{{ post.title }}</a>
        </li>
      {% endfor %}
    </ul>
    {% endraw %}

Congratulations! Now we have a more beautiful index page.

