# Themes and Templates

Webiny is a [headless Content Management System](./about.md), meaning it doesn't have a presentation layer. Themes in Webiny are simple definitions of the presentation layer structure. The presentation layer itself is de-attached from the system and is control by the developer.

[todo: image illustrating a theme, which is outside the webiny system, theme definition, which is on the border between the theme and the webiny system and the actual CMS which talks via the theme definition to the actual theme]

This approach gives you the ability to display the same content on many devices and screen sizes. For example you can display the content on a NodeJS powered website, smart watch or a SmartTV. The options are endless as the data returned from the CMS is a simple JSON object. 


## Theme structure
Theme is a simple JSON object. Theme doesn't contain any files, nor any assets. A theme has 3 layers:

1. **Theme** - tells basic information about the theme name, author and its version.
2. **Layout** - a theme can have multiple layouts. Layouts extract common elements usually presented in two or more templates. This way you don't need to define those elements in your templates.
3. **Template** - A template extends a layout, and defines additional elements. Layouts and templates have the same definition syntax.

Layouts and templates have two main goals. The first one is to define which **modules** need to load on pages using this template or layout. A typical example would be loading the "menu" module and passing the name of the menu you wish to load, i.e. main menu. This way you will get the main menu items in your page JSON object. ([click here to learn about the page JSON object](./page_api.md)) 

The second goal is to define zones. **Zones** are a high-level content group. A simple example would be, say you have a website template with a main content area and left sidebar area. Basically those are two zones. When creating your page, you can define in which zone should a certain page element be placed. 

[todo: image ilustrating the theme structure from theme, layouts templates to placeholders]

###Theme definition sample

```json
{
  "name": "Foo bar theme",
  "author": {
    "name": "Webiny",
    "email": "info@webiny.com",
    "url": "http://www.webiny.com/"
  },
  "description": "This is a test theme",
  "version": "0.1.0",
  "layouts": [
    {
      "name": "Master",
      "modules": [
        {
          "module": "menu",
          "options": {
            "name": "main-menu"
          }
        },
        {
          "module": "page",
          "options": {
            "url": "/about-us/"
          }
        }
      ]
    }
  ],
  "templates": [
    {
      "name": "Blog post",
      "filename": "blog-post.tpl",
      "description": "Used for displaying blog posts.",
      "layout": "Master",
      "zones": [
        "left-sidebar",
        "central-content",
        "right-sidebar"
      ],
      "items": [
        {
          "module": "menu",
          "options": {
            "name": "blog-post-sidebar"
          }
        }
      ]
    }
  ]
}
```


#### Theme

A the top we start off with a theme definition:

```json
 "name": "Foo bar theme",
  "author": {
    "name": "Webiny",
    "email": "info@webiny.com",
    "url": "http://www.webiny.com/"
  },
  "description": "This is a test theme",
  "version": "0.1.0"
```
This part describes the theme, author and provides some theme versioning info.

#### Layouts and templates

As mentioned `layouts` and `templates` sections use the same definition. The only difference is that a `template` needs to reference a `layout`.

The keys that you can define when describing a `template` or a `layout` are:

* **name** - name of the `template` or a `layout`.
* **filename** - this is an optional key that you can define. This key will be passed to all the page JSON objects using this template.
* **description** - few words to describe your `template` or `layout`.
* **zones** - this can be defined on both a `template` or a `layout`. If defined on both, the result will be a merged lists of both zones.
* **modules** - list of modules that need to be loaded when using this template. To each modules you can pass a set of `options`. For example on a master layout you might have a text describing "About us" that's displayed somewhere on the page. To load that text you can define the `page` module and pass the "/about-us/" as a url pattern. This will load that page and append that content into your page JSON object.
[todo: define a list of apps]


And here is a sample how the page output looks like:

```json
{
  "page": {
    "title": "page title",
    "author": "John D",
    "template": "blog-post.tpl",
    "content": {
      "zone-sidebar": [
        {
          "grid": "25-50-25",
          "items": [
            {
              "type": "wysiwyg",
              "content": "<html>",
              "meta":[]
            },
            {
              "type": "image_single",
              "src": "http://s3..."
            },
            {
              "type": "image_gallery",
              "images": [
                "http://img",
                "http://img2"
              ]
            }
          ]
        },
        {
          "grid": "100",
          "items": [
            {
              "type": "wysiwyg",
              "content": "<html>"
            }
          ]
        }
      ]
    }
  },
  "menu": {
    "main-menu": "<html>",
    "footer-menu": "<html>"
  }
}
```

[Click here to learn more about the page API and the output options.](./page_api.md)