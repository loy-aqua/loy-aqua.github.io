---
title: "Use Bootstrap Gem 4.5.0 on RoR"
categories: misc
---

The operations carried out below are based on the Bootstrap’s readme file.

Add bootstrap and its depends to your Gemfile:

> gem 'bootstrap', '~> 4.5.0'
> gem 'jquery-rails'

Ensure that sprockets-rails is at least v2.3.2.

bundle install and restart your server to make the files available through the pipeline.
```shell
$ mv app_assets_stylesheets_application.css app_assets_stylesheets_application.scss
```

 Custom bootstrap variables must be set or imported **before** bootstrap.
> @import "bootstrap";

Add Bootstrap dependencies and Bootstrap to your application.js:

> import 'bootstrap'
> require("@rails/ujs").start()
> ......
> ......
> = require jquery3
> = require popper
> = require bootstrap-sprockets

While bootstrap-sprockets provides individual Bootstrap components for ease of debugging, you may alternatively require the concatenated bootstrap for faster compilation.

If something went wrong, try this first 
```shell
$ rails assets:precompile
```
