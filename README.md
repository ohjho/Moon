# JHO Jekyll Theme [![Donate](https://img.shields.io/badge/paypal-donate-blue.svg)][1]

#### (If you like this theme or using it, please give a :star: for motivation.)

**[Moon](http://taylantatli.github.io/Moon)** is a minimal, one column jekyll theme.

## Getting Started
Clone or fork this repo and change the `url` and `puburl` in `_configa.yml`

### Prerequisites
You will need ruby and gem github-pages installed on your computer if you want to serve the Jekyll page locally.

I highly recommend using [rbenv][2]. Installation is easy if you already have [homebrew][3]:
```
$ brew install rbenv
```

### Ruby and rbenv
After you have rbenv `cd` to your Jekyll site's directory, and install a Ruby version. This theme was tested on 2.4.0:
```
# list available versions:
$ rbenv install -l

# install a ruby version (this might take a while):
$ rbenv install 2.4.0

# set the ruby version in the working directory:
$ rbenv local 2.4.0

# see which version is selected:
$ rbenv versions
```

### installing Gems
With rbenv **You don't need to SUDO**, but we need to install some gems:
```
# everything we need to github-pages, including jekyll
$ gem install github-pages

# we also need bundler
$ gem install bundler

# to install the required gems for this project specified in the gemfile
$ bundler install
```
you can checkout what [bundler][4] does.

if you are struck with some of these ruby, gems, bundler stuff, [this link][5] might be helpful.

### Serving Locally
```
$ bundle exec jekyll serve --watch    # the watch flag looks for real-time changes to files you edit
```
go to `localhost:4000` in your browser to see your site.

## Features
* Minimal, you can focus on your content
* Responsive
* Disqus integration
* Syntax highlighting
* Optional post image
* Social icons
* Page for sharing projects
* Optional background image
* Simple navigation menu
* MathJax support

## Preview

![screenshot of Moon](https://cloud.githubusercontent.com/assets/754514/14509720/61c61058-01d6-11e6-93ab-0918515ecd56.png)    
![screenshot of Moon](https://cloud.githubusercontent.com/assets/754514/14509716/61ac6c8e-01d6-11e6-879f-8308883de790.png)

See a [live version of Moon](http://taylantatli.github.io/Moon) hosted on GitHub.

## Getting Started

To learn how to install and use this theme check out the [Setup Guide](http://taylantatli.me/Moon/moon-theme/) for more information.

[1]: https://paypal.me/ohjho
[2]: https://github.com/rbenv/rbenv
[3]: https://brew.sh/
[4]: http://bundler.io/
[5]: http://idratherbewriting.com/documentation-theme-jekyll/mydoc_about_ruby_gems_etc.html
