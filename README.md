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

### Ruby version

Error:
```
An error occurred while installing commonmarker (0.17.13), and Bundler cannot continue.

In Gemfile:
  github-pages was resolved to 204, which depends on
    jekyll-commonmark-ghpages was resolved to 0.1.6, which depends on
      jekyll-commonmark was resolved to 1.3.1, which depends on
        commonmarker
```

[Solution](https://mkang32.github.io/2020/12/14/ruby-big-sur.html)

1. Check Ruby version
	```
	$ ruby -v
	ruby 2.6.3p62 (2019-04-16 revision 67580) [universal.x86_64-darwin20]
	```

2. Install Ruby Version Manager (rvm)
	```
	$ curl -sSL https://raw.githubusercontent.com/rvm/rvm/master/binscripts/rvm-installer | bash -s stable
	```

3. Install 2.7.2 version using rvm
	```
	$ rvm install "ruby-2.7.2"
	```

4. Check Ruby version again
	```
	$ ruby -v
	ruby 2.7.2p137 (2020-10-01 revision 5445e04352) [x86_64-darwin20]
	```

5. Bundle install
	```
	$ bundle install
	```

6. Run bundle
	```
	$ bundle exec jekyll serve
	```


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
