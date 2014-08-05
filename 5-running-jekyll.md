---
layout: page
title: Run Jekyll without errors
step: 5
---

## No BOM allowed

If there are `BOM` header characters in your UTF-8-encoded files, Jekyll will break. Make sure there are none.

## Set your encoding to UTF-8

Depending on the version of Ruby and/or Jekyll you're using, your site's content, and maybe other factors, you may need to make sure Jekyll will read your site's source as UTF-8.

If you followed this guide step by step or if your versions match the ones in this guide, you shouldn't need to use any of the following fixes.

### Set `encoding` option

Since Jekyll v1.3.0, you can specify the encoding in your `_config.yml`:

```
encoding: utf-8
```

### Change console encoding

Alternatively, you can change your command line tool's encoding to UTF-8 by running the following command every time you open a new console window.

```
chcp 65001
```

## The End

```
jekyll build
jekyll build --watch
jekyll build -w
jekyll serve
jekyll serve --watch
jekyll serve -w
```

You can now run all of the above commands on your Windows machine. Congratulations! You have successfully set up Jekyll on Windows.

Found something that wasn't quite clear? Is something in this guide outdated? Did I forget something? Please [look if somebody else noticed it already](https://github.com/juthilo/run-jekyll-on-windows/issues?state=open) or [file a new issue on GitHub](https://github.com/juthilo/run-jekyll-on-windows/issues/new) if that's not the case. Thanks!

If you need help with using Jekyll in general, please visit the official Jekyll website by clicking the button below.

<div class="pagination">
  <a class="pagination-item older" href="{{ site.baseurl }}4-wdm-gem">&laquo; Watch</a>
  <a class="pagination-item newer" href="http://jekyllrb.com" target="_blank">Jekyll Docs</a>
</div>
