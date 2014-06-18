Como Rodar o Jekyll no Windows
============================

Infelizmente, fazer o [Jekyll](http://jekyllrb.com) rodar no Windows não é tão fácil como é no Mac OS X ou Linux, e é também por isso que não é oficialmente suportado ou documentado.

Correndo Jekyll no Windows não é impossível. Na verdade, há um monte de tutoriais por ai, alguns mais úteis que outros. A maioria destes são escritos como posts de blogs e muitas vezes é por isso que eles tornam-se obsoletos e imprecisos ao longo do tempo.

Este repositório destina-se a fornecer aos usuários do Windows com instruções, como executar com êxito o Jekyll - e não apenas no momento de sua criação, mas espero que também no futuro, quando as soluções comuns tornarem-se obsoletas.

Algumas notas antes de começarmos
---------------------------------

* Exceto quando indicado, o conteúdo deste repositório está licenciado sob uma Creative Commons Attribution 
Licença 3.0. Você pode encontrar uma cópia da licença no link [LICENSE file](LICENSE).
* Quaisquer reclamações de responsabilidade relativas a danos causados ​​pelo uso de qualquer informação fornecida, incluindo qualquer tipo de 
informações incorretas ou esparsa, será rejeitado. ** Use as informações fornecidas NESTA PÁGINA POR SUA CONTA E RISCO. **
* * *

## visão global ##

Abaixo, você encontrará instruções para instalação...

* ... Ruby. [ir para a seção](#install-ruby)
* ... O Dev Kit do Ruby para ser capaz de construir extensões nativas. [ir para a seção](#install-the-ruby-devkit)
* ... O gem do Jekyll. [ir para a seção](#install-the-jekyll-gem)
* ... Python para ser capaz de usar Pygments, um marcador de sintaxe comuns, com Jekyll. [ir para a seção](#install-python-environment)
* ... Setuptools do Python e pip para instalar a parte de Python Pygments. [ir para a seção](#install-setup\_tools)
* ... a versão de funcional do Pygments gem. [ir para a seção](#install-python-part-of-pygments)

Finalmente, serás capaz de [Rodar o Jekyll](#run-jekyll) no Windows usando um último truque.

## Instalar Ruby ##
Jekyll foi escrito na linguagem Ruby, portanto Vamos precisar instalá-lo em primeiro lugar para começar.

1. Baixar o RubyInstaller no link [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * Versão 2.0.0 deve funcionar bem.
  * Certifique-se de baixar o pacote certo dependendo da arquitetura do seu sistema: x86 / x64
2. Execute o programa de instalação, que irá guiá-lo através da instalação. 
   * A única personalização que você precisa fazer para os nossos propósitos é verificar a caixa "Add executáveis ​​do Ruby para o seu
    PATH "na última tela antes da instalação real.
3.Após clicar em "Install", está tudo pronto com Ruby!

## Instalar o DevKit do Ruby ##

Algumas das dependências do Jekyll precisam ser construídas como "extensões nativas". Para fazer isso, você vai precisar do DevKit do Ruby.

1. Baixe o pacote de [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * Número da versão do DevKit e arquitetura alvo (32/64 bit) precisa corresponder à sua instalação Ruby.
2. O que você tem agora é um arquivo auto-extraível.
  * Execute o ficheiro.
  * Altere o destino de extração para algo como `C:\rubydevkit\`.
  * Extraia o arquivo.
  * **Nota**: Por alguma razão, a extração pode falhar se você tiver lotes de outros programas em execução. 
3. Inicializar o DevKit e vinculá-lo a sua instalação do Ruby (via sua ferramenta de linha de comando de preferência). 
   * Navegue até a pasta que você extraiu o DevKit em.

            cd "C:\rubydevkit\"

  * Auto-detectar instalações do Ruby e adicioná-los para um arquivo de configuração.

            ruby dk.rb init

  * Instale o DevKit.

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
