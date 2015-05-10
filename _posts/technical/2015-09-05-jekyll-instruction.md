---
layout: page-fullwidth
title: "An Overview about Jekyll"
subheadline: "Jekyll Instruction"
teaser: "The documentation is a work in progress..."
categories:
    - technical
tags:
    - Blog Technical
    - Web Framework
    - Jekyll Framework
header: no
---
<div class="row">
<div class="medium-4 medium-push-8 columns" markdown="1">
<div class="panel radius" markdown="1">
**Table of Contents**
{: #toc }
*  TOC
{:toc}
</div>
</div><!-- /.medium-4.columns -->



<div class="medium-8 medium-pull-4 columns" markdown="1">
{% include improve_content.html %}

## An introduction about Jekyll {#formats}
In this part, I will introduction an overview about Jekyll framework. This is a good framework for whom want to create a digital porfolio. 

### What is Jekyll? ###
*Jekyll* is a parsing engine bundled as a ruby gem used to build static websites from dynamic components such as templates, partials, liquid code, markdown, etc. Jekyll is known as `a simple, blog aware, static site generator`.


### What does Jekyll do?###
*Jekyll* is installed as a ruby gem local computer. Once installed you can call `jekyll serve` in the terminal in a directory and provided that directory is setup in a way jekyll expects, it will do magic stuff like parse markdown/textile files, compute categories, tags, permalinks, and construct your pages from layout templates and partials.

Once parsed, Jekyll stores the result in a self-contained static `_site` folder. The intention here is that you can serve all contents in this folder statically from a plain static web-server.

You can think of Jekyll as a normalish dynamic blog but rather than parsing content, templates, and tags on each request, Jekyll does this once beforehand and caches the entire website in a folder for serving statically.

### Jekyll is Not Blogging Software.###

> Jekyll is a parsing engine.
<cite>Jekyll framework</cite>

*Jekyll* does not come with any content nor does it have any templates or design elements. This is a common source of confusion when getting started. Jekyll does not come with anything you actually use or see on your website - you have to make it.

### Why Should I Care?###
Jekyll is very minimalistic and very efficient. The most important thing to realize about Jekyll is that it creates a static representation of your website requiring only a static web-server. Traditional dynamic blogs like Wordpress require a database and server-side code. Heavily trafficked dynamic blogs must employ a caching layer that ultimately performs the same job Jekyll sets out to do; serve static content.

Therefore if you like to keep things simple and you prefer the command-line over an admin panel UI then give Jekyll a try.

> Developers like Jekyll because we can write content like we write code:
<cite>Jekyll framework</cite>

- Ability to write content in markdown or textile in your favorite text-editor.
- Ability to write and preview your content via localhost.
- No internet connection required.
- Ability to publish via git.
- Ability to host your blog on a static web-server.
- Ability to host freely on GitHub Pages.
- No database required.

## How Jekyll works

{% include alert info='<ins><b>Heads up!</b></ins><br>The following is a complete but concise outline of exactly how Jekyll works. Core concepts are introduced in rapid succession without code examples. This information is not intended to specifically teach you how to do anything, rather it is intended to give you the full picture relative to what is going on in Jekyll-world. Learning these core concepts should help you avoid common frustrations and ultimately help you better understand the code examples contained throughout Jekyll-Bootstrap.' %}

### Initial Setup
After [installing Jekyll][1] you'll need to format your website directory in a way jekyll expects. Jekyll-bootstrap conveniently provides the base directory format.

**The Jekyll Application Base Format:** 
Jekyll expects your website directory to be laid out like so:

~~~
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.markdown
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── assets
|   └── css
|   └── javascript
├── _site
├── .jekyll-metadata
└── index.html
~~~
**_config.yml**: Stores configuration data.

**_includes**: This folder is for partial views.

**_layouts**: This folder is for the main templates your content will be inserted into. You can have different layouts for different pages or page sections.

**_posts**: This folder contains your dynamic content/posts. the naming format is required to be `@YEAR-MONTH-DATE-title.MARKUP@.`

**_site**: This is where the generated site will be placed once Jekyll is done transforming it.

**assets**: This folder is not part of the standard jekyll structure. The assets folder represents any generic folder you happen to create in your root directory. Directories and files not properly formatted for jekyll will be left untouched for you to serve normally.
[read more] [2]

### Jekyll Configuration 
Jekyll supports various configuration options that are fully outlined [here:][3]

## Content in Jekyll
Content in Jekyll is either a post or a page. These content "objects" get inserted into one or more templates to build the final output for its respective static-page.

###Posts and Pages
Both posts and pages should be written in markdown, textile, or HTML and may also contain Liquid templating syntax. Both posts and pages can have meta-data assigned on a per-page basis such as title, url path, as well as arbitrary custom meta-data.

####Working With Posts
**Creating a Post:** Posts are created by properly formatting a file and placing it the _posts folder.

**Formatting:** A post must have a valid filename in the form `YEAR-MONTH-DATE-title.MARKUP` and be placed in the `_posts` directory. If the data format is invalid Jekyll will not recognize the file as a post. The date and title are automatically parsed from the filename of the post file. Additionally, each file must have YAML Front-Matter prepended to its content. YAML Front-Matter is a valid YAML syntax specifying meta-data for the given file.

**Order:** Ordering is an important part of Jekyll but it is hard to specify a custom ordering strategy. Only reverse chronological and chronological ordering is supported in Jekyll.

Since the date is hard-coded into the filename format, to change the order, you must change the dates in the filenames.

**Tags:** Posts can have tags associated with them as part of their `meta-data`. Tags may be placed on posts by providing them in the post's YAML front matter. You have access to the post-specific tags in the templates. These tags also get added to the sitewide collection.

**Categories:** Posts may be categorized by providing one or more categories in the YAML front matter. Categories offer more significance over tags in that they can be reflected in the URL path to the given post. Note categories in Jekyll work in a specific way. If you define more than one category you are defining a category hierarchy "set". Example:

~~~
1.    ---
2.    title :  Hello World
3.    categories : [lessons, beginner]
4     ---
~~~

This defines the category hierarchy "lessons/beginner". Note this is one category node in Jekyll. You won't find "lessons" and "beginner" as two separate categories unless you define them elsewhere as singular categories.

####Working With Pages
**Creating a Page:** Pages are created by properly formatting a file and placing it anywhere in the root directory or subdirectories that do not start with an underscore.

**Formatting**: In order to register as a Jekyll page the file must contain YAML Front-Matter. Registering a page means **1)** that Jekyll will process the page and **2)** that the page object will be available in the site.pages array for inclusion into your templates.

**Categories and Tags**
Pages do not compute categories nor tags so defining them will have no effect.

**Sub-Directories**
If pages are defined in sub-directories, the path to the page will be reflected in the url. Example:

~~~
├── people
|     ├── DuyBui
|            └──  eassy.html
~~~

This page will be available at `http://yourdomain.com/people/DuyBui/essay.html`

**Recommended Pages**
    - **index.html**: You will always want to define the root index.html page as this will display on your root URL.
    - **404.html**: Create a root 404.html page and GitHub Pages will serve it as your 404 response.
    - **sitemap.html**: Generating a sitemap is good practice for SEO.
    - **about.html**: A nice about page is easy to do and gives the human perspective to your website.

### Templates in Jekyll
Templates are used to contain a page's or post's content. All templates have access to a global site object variable: site as well as a page object variable: page. The site variable holds all accessible content and metadata relative to the site. The page variable holds accessible data for the given page or post being rendered at that point.

**Create a Template:** Templates are created by properly formatting a file and placing it in the `_layouts` directory.

**Formatting:** Templates should be coded in HTML and contain YAML Front Matter. All templates can contain Liquid code to work with your site's data.

**Rending Page/Post Content in a Template:** There is a special variable in all templates named : `content`. The content variable holds the page/post content including any sub-template content previously defined. Render the content variable wherever you want your main content to be injected into your template:

**Sub-Templates**
Sub-templates are exactly templates with the only difference being they define another "root" layout/template within their YAML Front Matter. This essentially means a template will render inside of another template.

**Includes**
In Jekyll you can define include files by placing them in the `_includes` folder. Includes are NOT templates, rather they are just code snippets that get included into templates. In this way, you can treat the code inside includes as if it was native to the parent template.

Any valid template code may be used in includes.

## Using Liquid for Templating
Templating is perhaps the most confusing and frustrating part of Jekyll. This is mainly due to the fact that Jekyll templates must use the Liquid Templating Language.

###What is Liquid?###
[Liquid][4] is a secure templating language developed by [Shopify][5]. Liquid is designed for end-users to be able to execute logic within template files without imposing any security risk on the hosting server.

Jekyll uses Liquid to generate the post content within the final page layout structure and as the primary interface for working with your site and post/page data.

###Why Do We Have to Use Liquid?##
GitHub uses Jekyll to power [GitHub Pages][6]. GitHub cannot afford to run arbitrary code on their servers so they lock developers down via Liquid.

###Liquid is Not Programmer-Friendly.###

The short story is liquid is not real code and its not intended to execute real code. The point being you can't do jackshit in liquid that hasn't been allowed explicitly by the implementation. What's more you can only access data-structures that have been explicitly passed to the template.

In Jekyll's case it is not possible to alter what is passed to Liquid without hacking the gem or running custom plugins. Both of which cannot be supported by GitHub Pages.

{% include alert info='My personal stance is to not invest time trying to hack liquid. It is really unnecessary from a <i>programmer's</i> perspective. That is to say if you have the ability to run custom plugins (i.e. run arbitrary ruby code) you are better off sticking with ruby. Toward that end I have built <a href="http://github.com/plusjade/mustache-with-jekyll">Mustache-with-Jekyll</a> which is now abandoned =/. You should use <a href="http://ruhoh.com">http://ruhoh.com</a> instead =D.' %}

## Static Assets

Static assets are any file in the root or non-underscored subfolders that are not pages. That is they have no valid YAML Front Matter and are thus not treated as Jekyll Pages. Static assets should be used for images, css, and javascript files.

## Images: Title, Thumbnails, Homepage   {#images}

There are several types of images you can define via front matter. If you want to change the images used in the header have a look at [Style your Header]({{ site.url }}/headers/). 


### Title Images

~~~
image:
    title: image.jpg
~~~


### Thumbnails

Thumbnails are used on archive pages like the [blog index][2]. They have a size of 150x150 pixels. Define them in front matter like this:

~~~
image:
    thumb: thumbnail_image.jpg
~~~


### Homepage Image

If you want to feature an article on the homepage with a huge image, than use the homepage image with a width of 970 pixels. If no homepage image is defined *Feeling Responsive* writes instead *New Blog Articles* over the blog entries. Define the homepage image like this:

~~~
image:
    homepage: header_homepage_13.jpg
~~~



### Captions with URL

Sometimes you want to give credit to the creator of your images, maybe with a link. Especially when you use Creative Commons-images like I do for this website. Just add the following front matter and *Feeling Responsive* does the rest:

~~~
image:
    title: header_image.jpg
    caption: Image by Phlow
    caption_url: "http://phlow.de/"
~~~

### Define all images for an article

~~~
image:
    title: title_image.jpg
    thumb: thumbnail_image.jpg
    homepage: header_homepage_13.jpg
    caption: Image by Phlow
    caption_url: "http://phlow.de/"
~~~


<small markdown="1">[Up to table of contents](#toc)</small>
{: .text-right }


## Create a Table of Content
{: .t60}

With the Kramdown parser for Markdown you can render a table of contents for your documents. Just insert the following HTML in your post before the actual content. More information on [»Automatic ›Table of Contents‹ Generation«][1].

### Bare Bones Version
{% highlight html %}
### Table of Contents
*  Auto generated table of contents
{:toc}
{% endhighlight %}

### Foundation panel version

{% highlight html %}
<div class="panel radius" markdown="1">
**Table of Contents**
{: #toc }
*  TOC
{:toc}
</div>
{% endhighlight %}
<small markdown="1">[Up to table of contents](#toc)</small>
{: .text-right }

## Breadcrumbs

To turn on breadcrumbs, just use...

{% highlight html %}
breadcrumb: true
{% endhighlight %}


## Includes
{: .t60}

Includes can be very helpful to spice up your content. You can use includes in your Markdown-files with ease: Just call them with some Liquid code.

### list-posts.html

The `list-posts.html`-include is a loop to list posts. It's a helper to add some additional content fast and easy. You can use it in individual posts for example. Which parameters you use, depends on you.

Possible parameter for the loop:

- entries › define the number of entries to show
- offset › define the offset (number of entries to skip before displaying the first one)
- category › define **only one** category to display according entries

The loop looks when you use all parameters. Single parameters are possible of course.

~~~
{% raw %}{% include list-posts.html entries='3' offset='1' category='design' %}{% endraw %}
~~~

### next-previous-post-in-category.html

This include creates a next/previous link to a post of the same category using the first categories-variable in front matter.

~~~
{% raw %}{% include next-previous-post-in-category.html %}{% endraw %}
~~~


### improve_content.html

If your content is on Jekyll you can use this include to automatically generate a »Edit on GitHub Link« to give people a possibility to improve your content. Got the idea from [Ben Balters Blog](http://ben.balter.com/).

~~~
{% raw %}{% include improve_content.html %}{% endraw %}
~~~


### list-collection.html

This include lets you loop through a collection to list all entries in that collection. If you set »published: false« in front matter of a collection page the page gots filtered out via unless. The following example loops through a collection called *wordpress*.

~~~
{% raw %}{% include list-collection.html collection='wordpress' %}{% endraw %}
~~~


### alert – Embed an alert in your content

This include lets you easily display an alert. To use the include no `.html` ending is necessary. You can use five different kinds of alerts: `warning`, `info`, `success`, `alert` and `text`. 

~~~
{% raw %}{% include alert warning='This is a warning.' %}
{% include alert info='An info box.' %}
{% include alert success='Yeah, you made it!' %}
{% include alert alert='Danger!' %}
{% include alert terminal='jekyll -serve' %}
{% include alert text='Just a note!' %}{% endraw %}
~~~

{% include alert warning='This is a warning.' %}
{% include alert info='<b>Heads up!</b> The following is a complete but concise outline of exactly how Jekyll works. Core concepts are introduced in rapid succession without code examples. This information is not intended to specifically teach you how to do anything, rather it is intended to give you the full picture relative to what is going on in Jekyll-world. Learning these core concepts should help you avoid common frustrations and ultimately help you better understand the code examples contained throughout Jekyll-Bootstrap.' %}
{% include alert success='Yeah, you made it!' %}
{% include alert alert='Danger!' %}
{% include alert terminal='jekyll -serve' %}
{% include alert text='Just a note!' %}

You can even use `<html>`-tags inside the alert. Beware: Use " and ' properly.

~~~
{% raw %}{% include alert info='<em>Feeling Responsive</em> is listed on <a href="http://jekyllthemes.org/">http://jekyllthemes.org</a>' %}{% endraw %}
~~~

{% include alert info='<b>Heads up!</b> The following is a complete but concise outline of exactly how Jekyll works. Core concepts are introduced in rapid succession without code examples. This information is not intended to specifically teach you how to do anything, rather it is intended to give you the full picture relative to what is going on in Jekyll-world. Learning these core concepts should help you avoid common frustrations and ultimately help you better understand the code examples contained throughout Jekyll-Bootstrap.' %}

<small markdown="1">[Up to table of contents](#toc)</small>
{: .text-right }


## Javascript/Foundation modules

*Feeling Responsive* uses the foundation framework and some of its javascript components. I reduced the modules, to decrease page load and make the theme faster.

I only added one other javascript-module: [`backstretch`][3] by Scott Robbin. These modules are currently used by the theme and included in `javascript.min.js`. There is also a non-minified version, if you want to take a closer look: `javascript.js`.

~~~
/foundation/bower_components/foundation/js/vendor/jquery.js'
/foundation/bower_components/foundation/js/vendor/fastclick.js'
/foundation/bower_components/foundation/js/foundation.accordion.js'
/foundation/bower_components/foundation/js/foundation.clearing.js'
/foundation/bower_components/foundation/js/foundation.dropdown.js'
/foundation/bower_components/foundation/js/foundation.equalizer.js'
/foundation/bower_components/foundation/js/foundation.magellan.js'
/foundation/bower_components/foundation/js/foundation.topbar.js'
/foundation/js/jquery.backstretch.js'
~~~

{% include improve_content.html %}

</div><!-- /.medium-8.columns -->
</div><!-- /.row -->

 [1]: http://jekyllrb.com/docs/installation/
 [2]: http://jekyllrb.com/docs/usage/
 [3]: http://jekyllrb.com/docs/configuration/
 [4]: https://github.com/Shopify/liquid/
 [5]: http://www.shopify.com/
 [6]: https://pages.github.com/
 [7]: #
 [8]: #
 [9]: #
 [10]: #