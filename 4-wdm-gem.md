---
layout: page
title: Let Jekyll --watch
step: 4
---

## Install the wdm Gem

You can instruct Jekyll to have an eye out for changed files to automatically rebuild your site whenever you make changes in the source. On Windows, you need to install one extra tool, or rather Gem, to enable this functionality. Simply run the following command from the command line.

```
gem install wdm
```

## Require wdm in your Gemfile

Alternatively, if you use a Gemfile, you can check if Jekyll runs on Windows and only then install the wdm Gem.

```
require 'rbconfig'
gem 'wdm', '~> 0.1.0' if RbConfig::CONFIG['target_os'] =~ /mswin|mingw/i
```

## Summary

Take a deep breath! You've now installed everything you need to run Jekyll on Windows. There are a few minor things you should know to make sure that your sites build smoothly and without problems. Click the button below to proceed.

<div class="pagination">
  <a class="pagination-item older" href="{{ site.baseurl }}3-syntax-highlighting">&laquo; Beautiful Code</a>
  <a class="pagination-item newer" href="{{ site.baseurl }}5-running-jekyll">Run Jekyll &raquo;</a>
</div>
