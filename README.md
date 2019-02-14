
# Jekyll portfolio template
This branch contains the template currently used in my online portfolio. It has been developed using HTML and [Liquid](https://shopify.github.io/liquid/) for use with [Jekyll](https://jekyllrb.com/). A demo can be seen running at [https://abdu.io](https://abdu.io).
The HTML source can be found on the [html-template branch](https://github.com/abdullahibneat/abdullahibneat.github.io/tree/html-template).

![Render of the template](https://raw.githubusercontent.com/abdullahibneat/abdullahibneat.github.io/jekyll-template/render.jpg)

# Getting started

## For use with GitHub Pages
Fork this repository, naming your repository in the following format: `yourusername.github.io` if you plan to use [GitHub Pages](https://pages.github.com/).

## Configuring Jekyll
Configure the `_config.yml` file with your own details. Use the comments as a guide. Remember to change the URL to `yourusername.github.io`.

## Logo and images
The logo is now text based and can be changed from the `_config.yml` configuration file.
The main media resources are stored in the `assets/media` folder. You might want to replace the favicon with your own one, as well as changing the `siteFT.jpg` image used for social network purposes *(i.e. the image displayed on Twitter or Facebook when your website is linked)*.

## Creating a new article
Create a new article by simply creating a new `.md` file within the `_posts` folder. The following naming convention must be used for the template to work properly: `YYYY-MM-DD-your-title.md`.
The file should be structured as follows:
```
---
title: "Your article title"
description: "A brief description of the article"
layout: post

media-folder: "ArticleImages"
featured: "ft.jpg"
tags: [featured]
skills: [my, awesome, skills]
---

My article is about this content.
```
| Name         | Description                                                                                                                                         |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| title        | **Required.** *The title of the article*                                                                                                            |
| description  | **Required.** *A brief description of the article*                                                                                                  |
| layout       | **Required.** *The layout of the document. This is an article, or post.*                                                                            |
| media-folder | *Create a folder in the `assets/media` folder to use this variable. Such folder will contain images to be used in the article.*                     |
| featured     | *The name of the featured image within the above folder. It will be displayed on the index page as well as at the top of the post.*                 |
| tags         | *An array of tags. If the tag `featured` is used, the post will be displayed in the `featured projects` section on the homepage. *                  |
| skills       | *An array of skills to be displayed on the project container in the homepage, as well as underneath the title in the post.*                         |

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