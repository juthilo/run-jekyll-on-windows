在Windows上运行Jekyll
============================

不幸的是， 在Windows上运行 [Jekyll](http://jekyllrb.com) 并不像 Mac OS X or Linux 上那么简单, 这也是官方不提供支持，没有任何文档记录如何操作的原因了。

但是在Windows上运行Jekyll也并不是不可能. 事实上, 互联网上有许许多多的教程, 有些有用, 有些帮助不大. 大多数教程都写在博客中，那些文章经常过时或讲得不准确。

本教程打算提供给Windows用户如何成功运行Jekyll的完整的指导 -- 并且希望不仅能给出当前环境下的配置教程，而且在将来也能起指导作用。

开始前的一些Note
---------------------------------

* Except where otherwise noted, content in this repository is licensed under a Creative Commons Attribution
3.0 license. You can find a copy of the license in the [LICENSE file](LICENSE).
* Liability claims regarding damage caused by the use of any information provided, including any kind of
incorrect or sparse information, will be rejected. **USE THE INFORMATION PROVIDED ON THIS PAGE AT YOUR OWN RISK**.

* * *

## 概貌 ##

依据以下步骤安装，详细安装步骤在后文...

* ... Ruby. [jump to section](#install-ruby)
* ... the Ruby Dev Kit to be able to build native extensions. [jump to section](#install-the-ruby-devkit)
* ... the Jekyll gem. [jump to section](#install-the-jekyll-gem)
* ... Python to be able to use Pygments, a common syntax highlighter, with Jekyll. [jump to section](#install-python-environment)
* ... Python setuptools and pip to install the Python part of Pygments. [jump to section](#install-setup\_tools)
* ... the working version of the Pygments gem. [jump to section](#install-python-part-of-pygments)

最后, 就能使用文中最后提到的方法 [Run Jekyll](#run-jekyll) .

## 安装 Ruby ##

Jekyll是由Ruby写成的. 我们首先要安装它.

1. 下载 RubyInstaller from [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * Version 2.0.0 should work fine.
  * Make sure to download the right package depending on your system's architecture: x86 / x64 注意系统是32位或者64位
2. 运行安装包，按照指示下一步下一步
  * 唯一需要注意的是勾选 "Add Ruby executables to your PATH"
3. After you click on Install, you're all set with Ruby!

## 安装 Ruby DevKit ##

Some of Jekyll's dependencies need to be built as "native extensions". To do that, you'll need the Ruby DevKit.

1. 下载安装包 from [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * The DevKit's version number and target architecture (32/64 bit) need to match your Ruby installation.
2. 下载完成之后是一个自解压包.
  * Execute the file.
  * 改变解压目的路径，比如到 `C:\rubydevkit\`.
  * Extract the archive.
  * **Note**: 由于一些原因, 如果有很多运行的程序，解压可能失败.
3. 初始化 DevKit and 将它绑定到 Ruby 环境 (以下通过命令行).
  * 进入解压DevKit的文件夹.

            cd "C:\rubydevkit\"

  * 自动检测 Ruby 安装环境并且添加到配置文件.

            ruby dk.rb init

  * 安装 DevKit.

            ruby dk.rb install

## 安装 Jekyll gem ##

目前最新版本的Jekyll是 **v1.5.1, 兼容Windows环境**. 不要尝试安装Jekyll **v1.4.3, 已知不兼容Windows.** (See [jekyll/jekyll#1948](https://github.com/jekyll/jekyll/issues/1948) for more information.)

1. 安装最新版本 Jekyll ,通过命令行.

        gem install jekyll

2. 等着结束吧.

未来版本的 Jekyll 可能再一次不兼容Windows. 当新版本发布的时候，到这里查看一下兼容性.

* * *

现在在你Windows电脑上已经安装了 Jekyll . 如果你确定你不会用到 Pygments, 你可以跳过 [Run Jekyll](#run-jekyll) 部分. 否则, 继续读下去直到 Pygments 也能够运行.

* * *

## 安装 Python 环境 ##

如果你想要使用Jekyll默认依赖 Pygments, Windows上语法高亮, 你需要安装 Python, setuptools and pip.

### 安装 Python ###

1. Download the Python installer from [python.org](http://www.python.org/download/).
  * Python 3 不兼容 Jekyll. 使用 Python 2.7.5.
  * 再一次,下载符合操作系统版本的安装包
2. 执行安装. 按照默认操作即可.

### 安装 setuptools ###

1. Download the setuptools installer that matches your system and your Python installation from
   [here](http://www.lfd.uci.edu/~gohlke/pythonlibs/#setuptools).
2. Execute the installer.
  * If you used the default values when installing Python, you can do the same here. Otherwise, enter the correct
    path.

### 安装 pip ###

1. Download the pip installer that matches your system and your Python installation from
   [here](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pip).
2. Execute the installer.
  * If you used the default values when installing Python, you can do the same here. Otherwise, enter the correct
    path.

### 将 pip and Python 添加到 PATH 环境变量 ###

在你能够在命令行使用 pip 来安装 Pygments 之前, 你需要将 Python 添加到 PATH 环境变量.

1. Add `C:\path-to-your-python-installation\Scripts;` to the _beginning_ of your **user** PATH variable. The semicolon is
   important! Without it, you'll mess up your PATH. If you used all the default settings, the string to add should
   be `C:\Python27\Scripts;`. Of course, you can also put the semicolon before the new path and add it to the _end_
   of your **user** PATH variable: `;C:\Python27\Scripts`
2. Add `C:\path-to-your-python-installation\;` to the _beginning_ of your **system** PATH variable. The semicolon is
   important! Without it, you'll mess up your PATH. If you used all the default settings, the string to add should
   be `C:\Python27\;`. Of course, you can also put the semicolon before the new path and add it to the _end_
   of your **system** PATH variable: `;C:\Python27\`

## 安装 Python part of Pygments ##

打开命令行 and 运行以下命令:

    pip install Pygments

## 安装 working version of Ruby part of Pygments ##

Pygments.rb recently fixed a bug that caused Jekyll to fail when trying to compile sites that use Pygments. In order to use Jekyll with projects that use Pygments for code highlighting, make sure you have a working version of Pygments installed. Versions known to work include `0.5.0` (recommended) and `0.5.4` but not those in between.

1. 查看安装的 Pygments 版本.
  * Run `gem list` and look for `pygments.rb` in the output.
  * You can find the version you have installed next to the name in the list.

            ...
            pygments.rb (0.5.?)
            ...

  * 如果你的安装版本是 `0.5.0` or `0.5.4`, 你可以继续.
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

## 运行 Jekyll ##

依据你的站点, 编码问题可能导致出错. 为了避免这一点, 在导航到站点文件目录之前，将命令行编码改成 UTF-8, 然后再运行 Jekyll.

    chcp 65001
    cd "C:\my-site\"
    jekyll serve

You need to do this every time you open a new command prompt before running Jekyll.

你可以将如下设置添加到 `_config.yml` 文件, 如果有这个选项:

    encoding: UTF-8

**Note:** 这仅仅是改变了你站点的编码. 你依然需要使用 `chcp 65001` 命令来生成其他站点 (除非你同样添加了上面的那条配置).

### Let Jekyll watch ###

如果你想使用 Jekyll 自动生成的功能 (`jekyll serve --watch` / `jekyll serve -w`), 你需要 Ruby gem *wdm* 安装好.

你可以:

* 检查你的操作系统并且仅在你的站点有 Gemfile情况下,安装 gem. 将以下代码添加到 Gemfile:

        require 'rbconfig'
        gem 'wdm', '~> 0.1.0' if RbConfig::CONFIG['target_os'] =~ /mswin|mingw/i

* 手动安装 gem, 如果你的站点没有 Gemfile. 运行下面命令:

        gem install wdm
