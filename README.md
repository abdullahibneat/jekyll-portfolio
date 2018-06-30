# Jekyll template
This branch contains the template currently used in my online portfolio. It has been developed using HTML and [Liquid](https://shopify.github.io/liquid/) for use with [Jekyll](https://jekyllrb.com/). A demo can be seen running at [https://abdu.io](https://abdu.io).
The HTML source can be found on the [html-template branch](https://github.com/abdullahibneat/abdullahibneat.github.io/tree/html-template).


# Getting started

## For use with GitHub Pages
Fork this repository, naming your repository in the following format: `yourusername.github.io` if you plan to use [GitHub Pages](https://pages.github.com/).

## Configuring Jekyll
Configure the `_config.yml` file with your own details. Use the comments as a guide. Remember to change the URL to `yourusername.github.io`.

## Logo and images
The main media resources are stored in the `assets/images` folder. You might want to replace the logo and favicon with your own ones, as well as changing the `siteFT.jpg` image used for social network purposes *(i.e. the image displayed on Twitter or Facebook when your website is linked)*.

## Creating a new article
Create a new article by simply creating a new `.md` file within the `_posts` folder. The following naming convention must be used for the template to work properly: `YYYY-MM-DD-your-title.md`.
The file should be structured as follows:
```
---
title: "Your article title"
description: "A brief description of the article"
layout: post

imgpath: "ArticleImages/"
ft: "ft.jpg"
sketchfab: "9b454db8b20b43549a7457c964b360dc"
renders: "1.jpg,2.jpg"
---

My article is about this content.
```
| Name        | Description                                                                                                                                         |
|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| title       | **Required.** *The title of the article*                                                                                                            |
| description | **Required.** *A brief description of the article*                                                                                                  |
| layout      | **Required.** *The layout of the document. This is an article, or post.*                                                                            |
| imgpath     | *Create a folder in the `assets/renders` folder to use this variable. Such folder will contain images to be displayed at the end of the article.*   |
| ft          | *The name of the featured image within the above folder. It will be displayed on the index page.*                                                   |
| sketchfab   | *The UID of the Sketchfab model to be displayed. It's the long string of characters at the end of the URL address of the Sketchfab model.*          |
| renders     | *The names of the images to be displayed on the article, separated by commas.*                                                                      |

## Creating a new page
Create a new `.html` file on the root of the repository. The page should follow the following structure to be on par with the theme:
```
---
layout: page
title: My new page
permalink: /test-page.html
---

This is a new .html page. I can use standard <a href="https://www.w3schools.com/Html/">HTML</a> tags if I wish to.
```
| Name      | Description                                                |
|-----------|------------------------------------------------------------|
| layout    | **Required.** *The layout of the document. This is a page* |
| title     | **Required.** *The title of the page*                      |
| permalink | **Required.** *The file name of the page*                  |