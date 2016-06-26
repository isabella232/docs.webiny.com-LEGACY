# About

## Headless CMS
Traditional systems are tightly coupled with their presentation layer. Many of them use MCV, or similar patterns, to separate the "presentation" layer, aka the theme, from the business logic. This approach still requires the presence of a presentation layer, which is a big limitation in today's multi-device / multi-screen world. 

Webiny is taking a device agnostic approach. We don't have a presentation layer, rather we return your pages in a JSON format. This enables you to use any device, any template and any development language to control how that data will be presented.


### Theme definition
Although Webiny doesn't have a presentation layer, it sill gives you the option to describe your presentation layer. This adds structure to the data returned in the JSON output.
The theme definition is a simple JSON object. [To learn more about Themes and Templates, follow this link](Docs/en/Guides/theme_and_templates.md).