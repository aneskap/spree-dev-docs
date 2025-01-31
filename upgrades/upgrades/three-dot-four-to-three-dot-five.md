---
title: Upgrading Spree from 3.4 to 3.5
section: upgrades
order: 5
description: 'This guide covers upgrading a 3.4 Spree store, to a 3.5 store.'
---

# 3.4 to 3.5

### Update Gemfile

```ruby
gem 'spree', '~> 3.5.0'
gem 'spree_auth_devise', '~> 3.3'
gem 'spree_gateway', '~> 3.3'
```

### Run `bundle update`

### Install missing migrations

```bash
rails spree:install:migrations
rails spree_auth:install:migrations
rails spree_gateway:install:migrations
```

### Run migrations

```bash
rails db:migrate
```

### Install Spree Analytics Trackers extension

If you were previously using Analytics Trackers feature you need to install it as an extension as it was [extracted from the core](https://github.com/spree/spree/pull/8408).

1. Add [Spree Analytics Trackers](https://github.com/spree-contrib/spree_analytics_trackers) to your `Gemfile`:

```ruby
gem 'spree_analytics_trackers', github: 'spree-contrib/spree_analytics_trackers'
```

1. Install the gem using Bundler:

```bash
bundle install
```

1. Copy and run migrations:

```bash
bundle exec rails g spree_analytics_trackers:install
```

You're good to go!

## Read the release notes

For information about changes contained within this release, please read the [3.5.0 Release Notes](http://guides.spreecommerce.org/release_notes/spree_3_5_0.html).

## Verify that everything is OK

Run you test suite, click around in your store and make sure it's performing as normal. Fix any deprecation warnings you see.

