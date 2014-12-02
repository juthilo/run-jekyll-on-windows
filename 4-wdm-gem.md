---
layout: page
title: Let Jekyll --watch
step: 4
---

Jekyll has a built-in auto-regeneration feature that watches your source folder for changes and then re-builds your site. Starting with Jekyll v2.4.0, the `jekyll serve` command has this enabled by default and you can use run `jekyll build --watch` to manually enable it there.

## Install the wdm Gem

On Windows, you need to install one extra tool, or rather Gem, to enable this functionality. Simply run the following command from the command line.

~~~
gem install wdm
~~~

## Require wdm in your Gemfile

Alternatively, if you use a Gemfile, you can check if Jekyll runs on Windows and only then install the wdm Gem.

~~~
gem 'wdm', '~> 0.1.0' if Gem.win_platform?
~~~

## Install working version of listen Gem

Jekyll uses the listen Gem as a dependency for auto-regeneration. Some versions of listen do not work on Windows. [jekyll/jekyll-help#64](https://github.com/jekyll/jekyll-help/issues/64) has some information on versions that worked on Windows in the past. Please refer to the [Versions table](/#versions) to learn which versions of listen have been tested as part of this guide.

## May still not work

- If you try to run `jekyll build --watch` or `jekyll serve` and the output directory already exists, Jekyll sometimes fails to build the site. If you encounter this problem, you can work around it by adding `--force_polling` to the end of your Jekyll command. See the discussion in [twbs/bootstrap#14746](https://github.com/twbs/bootstrap/pull/14746) and [jekyll/jekyll#2926](https://github.com/jekyll/jekyll/issues/2926) for more information.

- Jekyll's auto-regeneration feature sometimes does not work at all. [jekyll/jekyll#2529](https://github.com/jekyll/jekyll/issues/2529) suggests it fails on 32-bit systems and there is no known workaround. As of Jekyll v2.4.0, if your system is affected by this problem, you need to manually disable the auto-regeneration feature when you want to serve a site using Jekyll by running `jekyll serve --no-watch`.

## Summary

Take a deep breath! You've now installed everything you need to run Jekyll on Windows. There are a few minor things you should know to make sure that your sites build smoothly and without problems. Click the button below to proceed.

<div class="pagination">
  <a class="pagination-item older" href="{{ site.baseurl }}3-syntax-highlighting">&laquo; Beautiful Code</a>
  <a class="pagination-item newer" href="{{ site.baseurl }}5-running-jekyll">Run Jekyll &raquo;</a>
</div>
