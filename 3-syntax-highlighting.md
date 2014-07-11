---
layout: page
title: Install a Syntax Highlighter
step: 3
---

## Overview

Whether you're using Markdown or HTML, Jekyll makes it easy for you to insert beautiful code blocks into your pages.

By default, Jekyll comes with pygments.rb, which is a syntax highlighter based on Python. To use it on Windows, you'll need to install Python and some extra tools.

A nice alternative is the Ruby-based Rouge, which is faster and easier to install, but doesn't support as many languages as Pygments.

Below, you'll find instructions for both syntax highlighters. Choose the one that best suits your needs. More information can be found on [the official Jekyll website](http://jekyllrb.com/docs/templates/#code-snippet-highlighting).

## Install Rouge

Quick and painless: Open your favorite command line tool and enter the following command.

```
gem install rouge
```

Then, in your `_config.yml`, set Rouge as your syntax highlighter:

```
highlighter: rouge
```

Done!

## Make Pygments work

If you want to use Pygments, which is a default Jekyll dependency, for syntax highlighting on Windows, you need to install Python, pip and finally the Python base of pygments.rb.

**Note:** After you complete the following steps, Jekyll might still output errors when building or serving sites. These shouldn't cause any real problems though, so you can safely ignore them.

### Install Python

The latest working version of Python at the time of writing is v2.7.8. Python 3 will not work.

Click the button below and download the v2.7 installer that matches your system's architecture (32bits / 64bits).

<a href="http://www.python.org/download/" class="button-external" target="_blank">Get Python</a>

Execute the downloaded file and go through the steps of the installation.

When you get to the screen below, make sure to click on the box next to *Add python.exe to Path* and select "Entire feature will be installed on local hard drive."

<img alt="Screenshot from the Python installation" src="../public/img/python-path.png" class="img-nice">

### Install pip

Pip is a tool for installing and managing Python packages, similar to Ruby Gems. You'll need it to install Pygments, the Python package that pygments.rb uses to highlight your code.

First, click on the button below and download `get-pip.py` via the link on that site.

<a href="https://pip.pypa.io/en/latest/installing.html" class="button-external" target="_blank">Get pip</a>

Next, open your favorite command line tool and navigate to the location of `get-pip.py` on your computer (e.g., `C:\pip\` or whatever folder you saved it into).

```
cd C:\pip
```

Then, run the following command to automagically download and install all required components.

```
python get-pip.py
```

### Install Python base of Pygments

From the command line, run the following command to install the Python base of Pygments.

```
pip install Pygments
```

### Set Pygments as your syntax highlighter

If it's not set already, add the following to your `_config.yml` to set Pygments as your syntax highlighter.

```
highlighter: pygments
```

## Summary

Jekyll will now use the highlighter you chose to make all your code blocks look super sleek. We're almost finished. Click the button below to find out how you can make Jekyll's super-useful watch option work on Windows. Or, if you'll never use that, [skip ahead to some final tips for smoothly running Jekyll on Windows]({{ site.baseurl }}5-running-jekyll).

<div class="pagination">
  <a class="pagination-item older" href="{{ site.baseurl }}2-jekyll-gem">&laquo; Install Jekyll Gem</a>
  <a class="pagination-item newer" href="{{ site.baseurl }}4-wdm-gem">Watch &raquo;</a>
</div>
