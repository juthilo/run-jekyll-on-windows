在Windows上运行Jekyll
============================

不幸的是， 在Windows上运行 [Jekyll](http://jekyllrb.com) 并不像 Mac OS X or Linux 上那么简单, 这也是官方不提供支持，没有任何文档记录如何操作的原因了。

但是在Windows上运行Jekyll也并不是不可能. 事实上, 互联网上有许许多多的教程, 有些有用, 有些帮助不大. 大多数教程都写在博客中，那些文章经常过时或讲得不准确。

本教程打算提供给Windows用户如何成功运行Jekyll的完整的指导 -- 并且希望不仅能给出当前环境下的配置教程，而且在将来也能起指导作用。

开始前的一些说明
---------------------------------

* 除非特殊说明, 这个repository中内容使用Creative Commons Attribution 3.0 license协议. 你可以在这里找到一份协议拷贝 [LICENSE file](LICENSE).
* 免责申明，使用本页面信息，包括可能错误的或者不完整的信息，导致的错误，风险自担**本页面信息造成的任何伤害风险自担**.

* * *

## 概貌 ##

依据以下步骤安装，详细安装步骤在后文...

* ... Ruby. [jump to section](#安装-ruby)
* ... the Ruby Dev Kit to be able to build native extensions. [jump to section](#安装-ruby-devkit)
* ... the Jekyll gem. [jump to section](#安装-jekyll-gem)
* ... Python to be able to use Pygments, a common syntax highlighter, with Jekyll. [jump to section](#安装python环境)
* ... Python setuptools and pip to install the Python part of Pygments. [jump to section](#安装-setup\_tools)
* ... the working version of the Pygments gem. [jump to section](#安装-python-part-of-pygments)

最后, 就能使用文中最后提到的方法 [Run Jekyll](#run-jekyll) .

## 安装 Ruby ##

Jekyll是由Ruby写成的. 我们首先要安装它.

1. 下载 RubyInstaller from [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * 2.0.0版本可以运行.
  * 注意系统是32位或者64位
2. 运行安装包，按照指示下一步下一步
  * 唯一需要注意的是勾选 "Add Ruby executables to your PATH"
3. 在点击“Install”之后, Ruby一切都安装好了!

## 安装 Ruby DevKit ##

有一些Jekyll的dependencies需要编译为"native extensions". 为了实现那样，你需要安装Ruby DevKit.

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

## 安装Python环境 ##

如果你想要使用Jekyll默认依赖 Pygments, Windows上语法高亮, 你需要安装 Python, setuptools and pip.

### 安装 Python ###

1. 下载 Python 安装包 [python.org](http://www.python.org/download/).
  * Python 3 不兼容 Jekyll. 使用 Python 2.7.5.
  * 再一次,下载符合操作系统版本的安装包
2. 执行安装. 按照默认操作即可.

### 安装 setup\_tools ###

1. 下载符合系统版本和Python版本的 setuptools 安装包 from [here](http://www.lfd.uci.edu/~gohlke/pythonlibs/#setuptools).
2. 执行安装包.
  * 如果你在安装Python时使用默认安装, 这里同样默认. 否则你需要键入正确的路径.

### 安装 pip ###

1. 下载符合系统版本和Python版本的 pip 安装包 from [here](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pip).
2. 执行安装包.
  * 如果你在安装Python时使用默认安装, 这里同样默认. 否则你需要键入正确的路径.

### 将 pip and Python 添加到 PATH 环境变量 ###

在你能够在命令行使用 pip 来安装 Pygments 之前, 你需要将 Python 添加到 PATH 环境变量.

1. 将 `C:\path-to-your-python-installation\Scripts;` 添加到 **user** PATH 变量的开始. 分号很重要! 如果没有分号,你会把Path搞混乱. 如果你上述步骤都是默认, 需要添加的路径应该是 `C:\Python27\Scripts;`. 当然, 你也可以将分号放到新加路径的前面并把添加的路径放到 **user** PATH 变量的后面: `;C:\Python27\Scripts`
2. 将 `C:\path-to-your-python-installation\;` 添加到 **system** PATH 变量的开始. 分号很重要! 如果没有分号,你会把Path搞混乱. 如果你上述步骤都是默认, 需要添加的路径应该是 `C:\Python27\;`. 当然, 你也可以将分号放到新加路径的前面并把添加的路径放到 **system** PATH 变量的后面: `;C:\Python27\`

## 安装 Python part of Pygments ##

打开命令行 and 运行以下命令:

    pip install Pygments

## 安装 working version of Ruby part of Pygments ##

Pygments.rb 最近修复了一个bug, 这个bug会导致 Jekyll 在使用Pygments编译生成站点的时候发生错误. 为了在Jekyll中使用Pygments 达到高亮效果, 确保你有一个能工作的Pygments. 可工作的版本包括 `0.5.0` (推荐) 和 `0.5.4` 但是不包括其中的.

1. 查看安装的 Pygments 版本.
  * 运行 `gem list` 并查看输出中的 `pygments.rb`.
  * 你可以在输出列表中查看你所安装的版本.

            ...
            pygments.rb (0.5.?)
            ...

  * 如果你的安装版本是 `0.5.0` or `0.5.4`, 你可以继续.
  * **说明:** 使用 `0.5.4` 版本, 当你运行Jekyll的时候，你会收到警告，但是你的站点应该能够生成成功.

            ...
                Generating... C:/Ruby200-x64/lib/ruby/gems/2.0.0/gems/posix-spawn-0.3.8/lib/posix/spawn.rb:162: warning: cannot close fd before spawn
                              done.
              Server address: http://0.0.0.0:9001
            Server running... press ctrl-c to stop.
            ...

2. 如果需要 (see above), 卸载任何有问题的 Pygments. Confirm that you want to break Jekyll's dependency (temporarily).

        gem uninstall pygments.rb --version "=0.5.2"
        ...
        Continue with Uninstall? [yN] y

3. 安装可工作的 Pygments.

        gem install pygments.rb --version "=0.5.0"

## 运行 Jekyll ##

依据你的站点, 编码问题可能导致出错. 为了避免这一点, 在导航到站点文件目录之前，将命令行编码改成 UTF-8, 然后再运行 Jekyll.

    chcp 65001
    cd "C:\my-site\"
    jekyll serve

在运行Jekyll之前,你都需要运行一下以上代码.

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
