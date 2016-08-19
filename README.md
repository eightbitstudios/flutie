# Flutie

[![Build Status](https://travis-ci.org/thoughtbot/flutie.svg?branch=master)](https://travis-ci.org/thoughtbot/flutie)

Flutie provides some utility view helpers for use with Rails applications.

There are helpers for setting a page title and for generating body classes.

## Installation & Upgrading

Flutie is a Railtie.
We support the versions of Ruby and Rails
listed in [.travis.yml](.travis.yml).

It should be run as a gem and included in your `Gemfile`:

    gem "flutie"

## Helpers

Flutie provides helper methods for use within Rails application layouts and views.

### Page Title

The `page_title` method can be used like:

    <title><%= page_title %></title>

By default, it will produce results like:

    <title>Appname : page title</title>

* "App name" comes from the module name of the rails application created by your app, i.e. `Appname::Application` will produce "Appname"
* "page" comes from trying `content_for(:page_title)` and assumes you are using `content_for` with `:page_title` symbol on your pages.
* The separator defaults to " : "

These can be overridden by passing an options hash including `:app_name`, `:page_title_symbol` and `:separator` hash keys, ie:

    content_for(:site_page_title, 'My title of my page')
    page_title(:app_name => 'My app name', :page_title_symbol => :site_page_title, :separator => " | ")
    => "My app name | My title of my page"

### Body Class

The `body_class` method can be used like:

    <body class="<%= body_class %>">

This will produce a string including the controller name and controller-action name.  For example, The WidgetsController#show action would produce:

    <body class="widgets widgets__show">

Anything which has been added via `content_for(:extra_body_classes)` will be added to the end, for example:

    content_for(:extra_body_classes, 'special--class')
    <body class="<%= body_class %>">
    <body class="widgets widgets__show special--class">

## How to contribute

Please see the [CONTRIBUTING](CONTRIBUTING.md) file for details.

## Credits

![thoughtbot](http://thoughtbot.com/images/tm/logo.png)

Flutie is maintained and funded by [thoughtbot, inc](http://thoughtbot.com/community).

Thank you to all [the contributors](https://github.com/thoughtbot/flutie/contributors)!

The names and logos for thoughtbot are trademarks of thoughtbot, inc.

## License

Flutie is Copyright © 2010-2015 thoughtbot, inc.
It is free software,
and may be redistributed under
the terms specified in the [LICENSE](LICENSE) file.
