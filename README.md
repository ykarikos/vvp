# Vanhassa Vara Parempi web site

This is the source for [Vanhassa Vara Parempi](http://www.vanhassavaraparempi.fi/) that is hosted in [GitHub Pages](https://pages.github.com/).

## How to add a new year

* Add the new year and festival title to `_config.yml`
* Refer to the new year in `index.md`
* Copy `<year-1>/index.md` to `<year>/` and `s/<year-1>/<year>/`
* Add a new year to archive-list in `_includes/navi.html`

## Running locally

Check instructions at https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/

```
$ sudo gem install bundler
$ bundle install
$ bundle exec jekyll serve
```
## Installation problems

### Nokogiri

Error:
```
An error occurred while installing nokogiri (1.6.8), and Bundler cannot continue.
```

[Solution](http://stackoverflow.com/a/34653921) on OSX:

```
$ xcode-select --install
$ gem install nokogiri -- --use-system-libraries --with-xml2-include=/usr/include/libxml2 --with-xml2-lib=/usr/lib/
$ bundle config build.nokogiri --use-system-libraries --with-xml2-include=/usr/include/libxml2/
```

Note the nokogiri version and update the `Gemfile` to point to that specific version:
```
gem 'nokogiri', '~> 1.10.3'
```

After this, run
```
bundle update
bundle install
bundle exec jekyll serve
```

### Activesupport

Error:
```
Gem::InstallError: activesupport requires Ruby version >= 2.2.2.
```

[Solution](https://github.com/github/pages-gem/issues/181) on Linux:

```
gem install activesupport
apt-get install -y zlib1g-dev ruby-execjs
gem install github-pages
```
