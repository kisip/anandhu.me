+++
date = '2025-04-19T18:23:00+05:30'
draft = false
title = 'How to setup a free website using Hugo and GitHub pages'
+++
## What is hugo 
Hugo is a fast and flexible static site generator written in Go. It's used to create websites, blogs, and other web content by generating HTML pages from source content, typically Markdown. Hugo is known for its speed and ease of use, making it a popular choice for building static websites
### Key features and benefits of Hugo:
### Speed:
Hugo is renowned for its exceptionally fast build times, often building entire sites in milliseconds. 

### Flexibility:
It's highly configurable and can be adapted to various website types, from blogs and documentation to corporate sites and portfolios.

### Ease of use:
Hugo is designed to be user-friendly, with a clear command-line interface and a large library of customizable themes. 
### Static Site Generation:
Unlike dynamic websites that generate content on the fly, Hugo generates static HTML files, resulting in faster loading times and improved security. 
### Markdown Support:
Hugo primarily uses Markdown for writing content, which is a lightweight markup language that's easy to learn and use. 
### No Database Required:
Hugo sites can be built without relying on databases or complex server-side systems, making them simpler to manage and deploy. 
### Multilingual Support:
Hugo provides robust support for multilingual websites, allowing you to easily translate content into multiple languages. 
### Extensive Themes and Community:
A large community of users and developers contributes to a vast library of themes and resources, making it easy to find pre-built templates or customize Hugo to your specific needs. 
### Integration with CMSs:
Hugo can integrate with headless CMSs like Sanity and Hygraph to provide content management capabilities. 
### Install hugo 
```apt install hugo```
###  Create a New Hugo Site CMD
```hugo new site your-site-name```
### Initialize Git Repo
```git init```
### Add a Theme or submodule
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
### Add the theme to your config.toml
theme = "add your theme name">
theme  = "PaperMod"
### Create GitHub Repository
### Connect Local Repository to GitHub
git remote add origin https://github.com/username/username.github.io.git
### Configure hugo for GitHub pages : Edit your config.toml file
baseURL = "https://username.github.io/"

languageCode = 'en-us'

title = 'Anandhu home page'

theme = "PaperMod"

### Create a  Workflow for GitHub Actions

Create .github/workflows/hugo.yml

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
        with:
          submodules: true

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: '0.145.0'
          extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
          publish_branch: gh-pages
### Configure GitHub pages settings
Go to your repository on GitHub

Click Settings > "Pages"
### Commit and push
git add .

git commit -m "first commit"

git push  origin main

### Access Your Site

### my GitHub repo link
https://kisip.github.io/anandhu.me/

### workflow images

![Workflow Image 1](/images/hugo.png)

![Workflow Image 2](/images/hugo1.png)

![Workflow Image 3](/images/hugo2.png)
