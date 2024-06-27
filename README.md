# K-State CS Hugo Framework

This is a [Hugo](https://gohugo.io/)-based web framework for K-State CS lecture content. It uses a lightly adapted version of the [Hugo Relearn Theme](https://mcshelby.github.io/hugo-theme-relearn/index.html) theme called [K-State CS Hugo Theme](https://ksucs-hugo.russfeld.me/)

#### Relevant Documentation

* [Hugo Documentation](https://gohugo.io/documentation/)
* [Hugo Relearn Theme](https://mcshelby.github.io/hugo-theme-relearn/index.html)
* [K-State CS Hugo Theme](https://ksucs-hugo.russfeld.me/)

## System Requirements

* [Git](https://github.com/git-guides/install-git)
* Go 1.22 or later from [Go Downloads](https://go.dev/doc/install)
* Hugo 0.128.0 or later from [Hugo Releases](https://github.com/gohugoio/hugo/releases)

## Cloning for the First Time

* Clone the repository using Git: `git clone <url>`
* Open the directory: `cd <directory>`
* Run the site using Hugo : `hugo serve`

Hugo should automatically download the relevant theme module. No additional configuration is needed.

## Updating the Theme

To update the theme to the latest version, run `hugo mod get -u`

## Updating the Hugo Version

To update the Hugo version, install a new version locally for testing and also update the version in `workflows/gh-pages.yml`

## Questions?

Contact [Russell Feldhausen](https://russfeld.me) - russfeld@ksu.edu
