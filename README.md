# Bootstrap Blog

![](screenshot.jpg)

**Bootstrap Blog** is a theme for [Grav CMS](http://github.com/getgrav/grav) built in with [Bootstrap v4.1](https://picturepan2.github.io/spectre/) framework and provides a powerful base to develope your own themes using SCSS. Also we use latest [FontAwesome 5](https://fontawesome.com/).

## Features

* Lightweight and minimal for optimal performance
* Bootstrap 4.1 Stable
* SCSS based CSS source files for easy customization
* 3 Portfolio Layouts
* Twitter Timeline sidebar widget
* Fill of color with Bootstrap styles
* Fontawesome 5

### Page Templates

* Default view template `default.md`
* Error view template `error.md`
* Blog view template `blog.md`
* Portfolio view template `portfolio.md`
* Blog and Portfolio item view template `item.md`
* Modular view templates: `modular.md`
  * Features Modular view template `features.md`
  * Showcase Modular view template `showcase.md`
  * Blog Modular view template `blog-modular.md`
  * Portfolio Modular view template `portfolio-modular.md`
  * Text Modular view template `text.md`

# Installation

Installing the Bootstrap Blog theme can be done in one of two ways. GPM (Grav Package Manager) installation method enables you to quickly and easily install the theme with a simple terminal command, while the manual method enables you to do so via a zip file.

## GPM Installation (Preferred)

The simplest way to install this theme is via the [Grav Package Manager (GPM)](http://learn.getgrav.org/advanced/grav-gpm) through your system's Terminal (also called the command line). From the root of your Grav install type:

    bin/gpm install bootstrap-blog

This will install the Quark theme into your `/user/themes` directory within Grav. Its files can be found under `/your/site/grav/user/themes/bootstrap-blog`.

## Manual Installation

To install this theme, just download the zip version of this repository and unzip it under `/your/site/grav/user/themes`. Then, rename the folder to `bootstrap-blog`. You can find these files either on [GitHub](https://github.com/ayozehd/bootstrap-blog) or via [GetGrav.org](http://getgrav.org/downloads/themes).

You should now have all the theme files under

    /your/site/grav/user/themes/bootstrap-blog

## Styles

Almost templates support a style parameter in headers. That means depending on the case some buttons, text colors and background change from [Bootstrap Theme Colors](https://getbootstrap.com/docs/4.0/getting-started/theming/#theme-colors). Don't be afraid to fill of color your site!

Templates supporting `style`:
* `item`
* `features`
* `showcase`
* `blog-modular`
* `portfolio-modular`
* `text`


## FontAwesome 5

Bootstrap Blog is builded with lastest [FontAwesome Icons 5](https://fontawesome.com/). This version has some [important changes from previous version 4](https://fontawesome.com/how-to-use/upgrading-from-4), now icons are divided in three groups: Solid, Brand and Regular (Light is only for _Pro_).

In this theme `fas` or Font Awesome Solid is selected by default. If you need to use Regular or Brand icons you just have to add `far` or `fab` respectively at the end.

Feel free to use them anywhere following [official usage](https://fontawesome.com/how-to-use/web-fonts-with-css).

## Default Options

Bootstrap Blog comes with a few default theme options that can be set site-wide. These options are:

```yaml
enabled: true                   # Enable the theme
cdn_enabled: false              # Get CSS and JS files from CDN servers
navbar:
  image:
  icon:
  style: default
  dropdown: true
  sticky: false

sidebar:
  enabled: true
  align: left
  twitter:
    enabled: true
    user: twitter
    height: 600
    theme: light
  about:
    enabled: true
    title: About me
    content: Some text about you...
    page:

item:
  show_prev_next: true
  dateformat: 'jS M Y'
  longdateformat: 'F jS \\a\\t g:ia'

comments:
  enabled: false
  disqus_shortname:

footer:
  style: dark
  text: 'Some footer text'
  legal:
```

To make modifications, you can copy the `user/themes/bootstrap-blog/bootstrap-blog.yaml` file to `user/config/themes/` folder and modify, or you can use the admin plugin.

> NOTE: Do not modify the `user/themes/bootstrap-blog/bootstrap-blog.yaml` file directly or your changes will be lost with any updates

## Showcase Modular

Showcase modular template is useful as page's heading. You can setup optionally a background image, or use instead Bootstrap Styles. This will try to set automatically first folder image as background or you can pick it via Admin Plugin. Additionally you can include some buttons at bottom.

**Still under heavy development!** Also you can setup your own image filters to override ours. You must use [Grav Media Actions](https://learn.getgrav.org/content/media#image-actions) in Twig way, separating arguments by comma (if there is no arguments you must type `null`).

```yaml
style: light|dark|primary|info|success|warning|danger
text_align: center|left|right
image_actions:
    brightness: -100
    colorize: -35,81,122
    negate: null
buttons:
    -
        text: 'Blog'
        url: /blog
        icon: rss
    -
        text: Portfolio
        url: /portfolio
        icon: flask
```
> Note style parameter just will work without background image

## Features Modular

You can apply a Bootstrap Style to icons, or a custom color. Also `text-align` param is supported as well as a `style` parameter in modular template, changing background and font color.

```yaml
style: light
text_align: center
features:
    -
        icon: rocket
        title: Title
        text: 'Text with HTML support'
        style: primary    # Optional style for icon
        color: '#fefefe;' # rgba or hex custom color

```

## Text Modular

This is the default modular template. It supports `style` parameter to change background and font color following [Bootstrap Theme Colors](https://getbootstrap.com/docs/4.1/getting-started/theming/#theme-colors). Also you are able to use `text_align`, and set the image width by columns with `header_image_size` taking values from 1 to 12 (default 6). Image will be retrieved automatically from first media founded in folder, or you can pick one on `header_image_file`.

## Blog & Portfolio

Blog and Porfolio content must be setting up with [Page Collections](https://learn.getgrav.org/content/collections), except in modular templates where `show_more` route parameter is used as fallback to get children. In addition, the showcase is included to customize Blog and Porfolio headers following the same structure mentioned above. While Blog items has always same design, it's possible to choose between 3 layouts (boxed, cards and masonry) to Portfolio items, also in modular.

```yaml
title: Blog
content:
    items: '@self.children'
    order:
        by: date
        dir: desc
    limit: 6
    pagination: true
```

```yaml
title: Portfolio Modular
layout: boxed|cards|masonry
show_more: /projects
content:
    items:
      '@page': '/projects'
    order:
        by: date
        dir: desc
    limit: 6
    pagination: false
```

## Item

Descendants of Blog and Portfolio are items. It get first folder image as header or you can pick it via `header_image_file` as in [Text Modular](#text-modular). In addition, `style` parameter is supported and `buttons` array to show some links at bottom.

Also you are able to disable sidebar and comments in each item, overriding theme settings.

```yaml
title: Title
style: primary
taxonomy:
    category:
        - post
    tag:
        - tag
sidebar:
    enabled: true
comments:
    enabled: true
buttons:
    -
        text: 'Link'
        url: 'http://example.com'
```

## Sidebar

Sidebar can be disabled in any page and it's possible to set on left or right side. It hasn't hierarchical support, so you need to do it in every item. Support by default some widgets from Grav like Taxonomy List, Archives, Simplesearch or Syndicate. We included a Twitter Timeline and About you widget which can be configured in Admin Panel theme settings. Last one lets you set a page as widget content to render text in different languages.

Feel free to extend `sidebar.html.twig` to add your own widgets!

### TODO
* Skills/animated bars modular template
* Carrousel modular template
* Go to top button
* Merge portfolio and blog items layouts