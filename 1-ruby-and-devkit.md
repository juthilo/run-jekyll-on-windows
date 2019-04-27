---
layout: page
title: 安装 Ruby 和 Ruby DevKit
nav_title: Ruby
step: 1
---

Ruby 是 Jekyll 所用的编程语言。您将需要安装 Ruby 和相应的 Devkit，这是将 Jekyll 的一些依赖项构建为 "native extensions" 所必需的。Jekyll 有一些依赖项只提供原始源代码。为了使它们成为功能完整的可执行文件，您可能需要安装相应的 Devkit。

## 安装 Ruby 和 相应的 Devkit

首先，单击下面的按钮，下载与您的系统体系结构 (x86 / x64) 匹配的 Ruby 2.5.5 版安装程序。此安装程序来源于 RubyInstaller 并已整合相应的 Devkit。

<a href="https://github.com/oneclick/rubyinstaller2/releases/download/RubyInstaller-2.5.5-1/rubyinstaller-devkit-2.5.5-1-x64.exe" class="button-external" target="_blank">Ruby+Devkit 2.5.5-1 (x64)</a>

<a href="https://github.com/oneclick/rubyinstaller2/releases/download/RubyInstaller-2.5.5-1/rubyinstaller-devkit-2.5.5-1-x86.exe" class="button-external" target="_blank">Ruby+Devkit 2.5.5-1 (x86)</a>

执行安装程序并完成安装步骤。当您进入下面的页面时，请确保选中 "Add Ruby executables to your PATH" 复选框以及 "MSYS2 development toolchain" 复选框。

<img alt="Screenshot of the Ruby installation" src="../public/img/ruby-path.png" class="img-nice">

单击 Install，Ruby 将很快安装完毕。在安装完成页面，请不要直接退出安装程序。

<img alt="Screenshot of the MSYS2 installation" src="../public/img/ruby-msys2.png" class="img-nice">

请确保选中 "Run 'ridk install' to setup MSYS2" 复选框，并点击 Finish 完成安装。完成后将会弹出 RubyInstall2 的 CMD 窗口并提示输入数字选择安装组件，不输入数字并直接回车安装所有组件。

等待 RubyInstall2 完成安装，此步骤所需时间可能较长，请耐心等待全部配置完成

## 完成

完工！如果一切顺利的话，现在您的机器上已经安装了一个可以运行的 Ruby，您可以使用 Ruby Devkit 来构建功能完整的可执行文件。Ruby 提供了一种安装所谓的 *gems*&mdash;软件包 的方法，您可以从命令行使用这些软件包。Jekyll 就是其中之一。单击下面的按钮以了解如何安装它。

<div class="pagination">
  <a class="pagination-item older" href="{{ site.baseurl }}">&laquo; 介绍</a>
  <a class="pagination-item newer" href="{{ site.baseurl }}2-jekyll-gem">安装 Jekyll Gem &raquo;</a>
</div>
