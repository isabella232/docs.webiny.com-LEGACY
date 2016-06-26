# Themes and Templates

Webiny is a [headless Content Management System](./about.md), meaning it doesn't have a presentation layer. Themes in Webiny are simple definitions of the presentation layer structure. The presentation layer itself is de-attached from the system and is control by the developer.

[todo: image illustrating a theme, which is outside the webiny system, theme definition, which is on the border between the theme and the webiny system and the actual CMS which talks via the theme definition to the actual theme]

This approach gives you the ability to display the same content on many devices and screen sizes. For example you can display the content on a NodeJS powered website, smart watch or a SmartTV. The options are endless as the date returned from the CMS is a simple JSON object. 


## Theme structure
Theme is a simple JSON object. Theme doesn't contain any files, nor any assets. A theme has 3 layers:
1. **Theme** - tells basic information about the theme name, author and the version.
2. **Layout** - a theme can have multiple layouts. Layouts extract common elements usually presented in two or more templates. This way you don't need to define those elements in your templates.
3. **Template** - A template extends a layout, and defines additional elements. Layouts and templates have the same definition syntax.

Layouts and templates have two main goals. The first one is to define which **modules** need to load on pages using this template or layout. A typical example would be loading the "menu" module and passing the name of the menu you wish to load, i.e. main menu. This way you will get the main menu items in your page JSON output. 

The second goal is to define zones. **Zones** are a high-level content group. A simple example would be, say you have a website template with a main content area and left sidebar area. Basically those are zones. When creating your page, you can define in which zone should a certain page element be placed. 

[todo: image ilustrating the theme structure from theme, layouts templates to placeholders]

