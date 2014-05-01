---
layout: post
comments: true
---

Not long ago, I started using [Twitter Bootstrap](http://twitter.github.com/bootstrap/) with [Jekyll](http://jekyllrb.com/). Jekyll is awesome, so is Twitter Bootstrap.

But there are some minor things issues that I've encountered so far and wish to blog about in case you guys have problems with it and found my page while Googling my page.


#### Problem :

[Twitter Navs](http://twitter.github.com/bootstrap/components.html#navs)

When building a static marketing website, we can simple do a for loop in [liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) to display the pages in the navigation bar, but that would result in pages not being shown according to how you would want it to be.

The scenario would be something like this :

I wanted Number 3 tab to be at position 3! 
And Number 2 tab to be at position 2!

![Screwed up Navbar!](http://i.imgur.com/YLGGWQ6.png)

So, how do we get twitter's navigation bar to show pages accordingly to how we want it to be?

#### Solution:

[Weighted pages](https://github.com/aucor/jekyll-plugins#weighted_pagesrb)

I've found this useful plugin in [Jekyll's wiki](https://github.com/mojombo/jekyll/wiki/Plugins). Which allows us to weight each pages accordingly and display it out on the navigation bar nicely.

        {{% for node in pages_list %}}
          {{% if group == null or group == node.group %}}
            {{% if page.url == node.url %}}
              <li class="active"><a href="{{node.url}}" class="active">{{node.title}}</a></li>
            {{% else %}}
              <li class=""><a href="{{node.url}}">{{node.title}}</a></li>
            {{% endif %}}
          {{% endif %}}
        {{% endfor %}}
        {{% assign pages_list = nil %}}
        {{% assign group = nil %}}

then in our `default.html`, in the place where we want our navigation bar to be, we would code something like this.

    <ul class="nav nav-tabs">
      {{% assign pages_list = site.weighted_pages %}}
      {{% assign group = 'navigation' %}}
      {{% include pages_list %}}
    </ul>

Now, in the pages where you want to be displayed in the navigation bar,

we would do something like this in the [YAML Front Matter](https://github.com/mojombo/jekyll/wiki/yaml-front-matter).

In `Home` page:

    ---
    layout: default
    title: Home
    group: "navigation"
    weight: 1
    ---

In `Number 2` page:

    ---
    layout: default
    title: Number 2
    group: "navigation"
    weight: 2
    ---

In `Number 3` page:

    ---
    layout: default
    title: Number 3
    group: "navigation"
    weight: 3
    ---


And viola!

A nicely weighted navigation bar!

![A nicely weighted nav bar](http://i.imgur.com/DNO3DXj.png)

---
Soon, I'm going to release my codes on github which has various `_includes`, which you can add easily in your project, like [Thumbnails](http://twitter.github.com/bootstrap/components.html#thumbnails), [Carousel gallery](http://twitter.github.com/bootstrap/javascript.html#carousel), so stay tuned!

