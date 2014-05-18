How to Run Jekyll on Windows
============================

Sadly, getting [Jekyll](http://jekyllrb.com) to run on Windows is not as easy as it is on Mac OS X or Linux, which is also why it is not officially supported or documented.

Running Jekyll on Windows is not impossible though. In fact, there are a lot of tutorials out there, some more, some less helpful. Most of these are written as blog posts which is often why they become outdated and inaccurate over time.

This repository is intended to provide Windows users with instructions to successfully run Jekyll - not just at the time of its creation but hopefully also in the future, when common solutions become outdated once again.

A few notes before we get started
---------------------------------

* Except where otherwise noted, content in this repository is licensed under a Creative Commons Attribution
3.0 license. You can find a copy of the license in the [LICENSE file](LICENSE).
* Liability claims regarding damage caused by the use of any information provided, including any kind of
incorrect or sparse information, will be rejected. **USE THE INFORMATION PROVIDED ON THIS PAGE AT YOUR OWN RISK**.

* * *

## Overview ##

Below, you'll find instructions to install...

* ... Ruby. [jump to section](#install-ruby)
* ... the Ruby Dev Kit to be able to build native extensions. [jump to section](#install-the-ruby-devkit)
* ... the Jekyll gem. [jump to section](#install-the-jekyll-gem)
* ... Python to be able to use Pygments, a common syntax highlighter, with Jekyll. [jump to section](#install-python-environment)
* ... Python setuptools and pip to install the Python part of Pygments. [jump to section](#install-setup\_tools)
* ... the working version of the Pygments gem. [jump to section](#install-python-part-of-pygments)

Finally, you'll be able to [Run Jekyll](#run-jekyll) on Windows using one last trick.

## Install Ruby ##

Ruby is the language Jekyll is written in. We'll need to install it first to get started.

1. Download a RubyInstaller from [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * Version 2.0.0 should work fine.
  * Make sure to download the right package depending on your system's architecture: x86 / x64
2. Execute the installer which will guide you through the installation.
  * The only customization you need to make for our purposes is to check the box "Add Ruby executables to your
    PATH" on the last screen before the actual installation.
3. After you click on Install, you're all set with Ruby!

## Install the Ruby DevKit ##

Some of Jekyll's dependencies need to be built as "native extensions". To do that, you'll need the Ruby DevKit.

1. Download the package from [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * The DevKit's version number and target architecture (32/64 bit) need to match your Ruby installation.
2. What you have now is a self-extracting archive.
  * Execute the file.
  * Change the extraction destination to something like `C:\rubydevkit\`.
  * Extract the archive.
  * **Note**: For some reason, the extraction might fail if you have lots of other programs running.
3. Initialize the DevKit and bind it to your Ruby installation (via your preferred command line tool).
  * Navigate to the folder you extracted the DevKit into.

            cd "C:\rubydevkit\"

  * Auto-detect Ruby installations and add them to a configuration file.

            ruby dk.rb init

  * Install the DevKit.

            ruby dk.rb install

## Install the Jekyll gem ##

The latest version of Jekyll at the time of writing is **v1.5.1, which is compatible with Windows environments**. Do not attempt to install Jekyll **v1.4.3, which is known to be incompatible with Windows.** (See [jekyll/jekyll#1948](https://github.com/jekyll/jekyll/issues/1948) for more information.)

1. Install the latest version of Jekyll from the command line.

        gem install jekyll

2. Watch and enjoy.

Future versions of Jekyll might once again be incompatible with Windows. Check back here when a new version is released to see if it remains compatible.

* * *

You now have Jekyll installed on your Windows computer. If you are sure you'll never need to use Pygments,
you can skip to the [Run Jekyll](#run-jekyll) section. Otherwise, read on to get Pygments running as well.

* * *

## Install Python Environment ##

If you want to use Pygments, which is a default Jekyll dependency, for syntax highlighting on Windows, you need to
install Python, setuptools and pip.

### Install Python ###

1. Download the Python installer from [python.org](http://www.python.org/download/).
  * Python 3 is currently known not to work with Jekyll. Use Python 2.7.5.
  * Again, make sure to download the package intended for your system.
2. Execute the installer. All default values should be fine.

### Install setuptools ###

1. Download the setuptools installer that matches your system and your Python installation from
   [here](http://www.lfd.uci.edu/~gohlke/pythonlibs/#setuptools).
2. Execute the installer.
  * If you used the default values when installing Python, you can do the same here. Otherwise, enter the correct
    path.

### Install pip ###

1. Download the pip installer that matches your system and your Python installation from
   [here](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pip).
2. Execute the installer.
  * If you used the default values when installing Python, you can do the same here. Otherwise, enter the correct
    path.

### Add pip and Python to your PATH environment variable ###

Before you can use pip from the command line to install Pygments, you need to add your Python environment to your
PATH environment variables.

1. Add `C:\path-to-your-python-installation\Scripts;` to the _beginning_ of your **user** PATH variable. The semicolon is
   important! Without it, you'll mess up your PATH. If you used all the default settings, the string to add should
   be `C:\Python27\Scripts;`. Of course, you can also put the semicolon before the new path and add it to the _end_
   of your **user** PATH variable: `;C:\Python27\Scripts`
2. Add `C:\path-to-your-python-installation\;` to the _beginning_ of your **system** PATH variable. The semicolon is
   important! Without it, you'll mess up your PATH. If you used all the default settings, the string to add should
   be `C:\Python27\;`. Of course, you can also put the semicolon before the new path and add it to the _end_
   of your **system** PATH variable: `;C:\Python27\`

## Install Python part of Pygments ##

Open a new command line window and run the following command:

    pip install Pygments

## Install working version of Ruby part of Pygments ##

Pygments.rb recently fixed a bug that caused Jekyll to fail when trying to compile sites that use Pygments. In order to use Jekyll with projects that use Pygments for code highlighting, make sure you have a working version of Pygments installed. Versions known to work include `0.5.0` (recommended) and `0.5.4` but not those in between.

1. Find out which version of Pygments you have installed.
  * Run `gem list` and look for `pygments.rb` in the output.
  * You can find the version you have installed next to the name in the list.

            ...
            pygments.rb (0.5.?)
            ...

  * If your installed version is `0.5.0` or `0.5.4`, you're already good to go.
  * **Note:** Using version `0.5.4`, you might receive warnings when you run Jekyll but your site should be successfully generated.

            ...
                Generating... C:/Ruby200-x64/lib/ruby/gems/2.0.0/gems/posix-spawn-0.3.8/lib/posix/spawn.rb:162: warning: cannot close fd before spawn
                              done.
              Server address: http://0.0.0.0:9001
            Server running... press ctrl-c to stop.
            ...

2. If necessary (see above), uninstall any broken version of Pygments. Confirm that you want to break Jekyll's dependency (temporarily).

        gem uninstall pygments.rb --version "=0.5.2"
        ...
        Continue with Uninstall? [yN] y

3. Install a working version of Pygments.

        gem install pygments.rb --version "=0.5.0"

## Run Jekyll ##

Depending on your individual site, problems due to incompatible character encodings might arise. To avoid those, change your command line's encoding to UTF-8 before navigating to your site source folder and running the Jekyll command of your choice.

    chcp 65001
    cd "C:\my-site\"
    jekyll serve

You need to do this every time you open a new command prompt before running Jekyll.

You can alternatively add the following setting to your `_config.yml` file, if that is an option:

    encoding: UTF-8

**Note:** This will only change the encoding for one site. You'll need to continue to use the `chcp 65001` command for other sites (unless you add the setting to those, too).

### Let Jekyll watch ###

If you want to use Jekyll's auto-regeneration feature (`jekyll serve --watch` / `jekyll serve -w`), you need to have the Ruby gem *wdm* installed.

You can:

* Check the operating system and install the gem only if necessary (on Windows), if your site has a Gemfile. Add this to the Gemfile:

        require 'rbconfig'
        gem 'wdm', '~> 0.1.0' if RbConfig::CONFIG['target_os'] =~ /mswin|mingw/i

* Install the gem manually, if your site doesn't have a Gemfile. Run this command:

        gem install wdm
