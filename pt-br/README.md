Como executar Jekyll no Windows
============================

Infelizmente, para o [Jekyll](http://jekyllrb.com) executar no Windows não é tão fácil como é no Mac OS X ou Linux, e por isso seu suporte não é oficial ou documentados.

Executar o Jekyll no Windows não é impossível. Na verdade, há um monte de tutoriais lá fora, alguns mais, outros menos úteis. A maioria destes são escritos como posts de blogs que muitas vezes se tornam obsoletos e imprecisos ao longo do tempo.

Este repositório destina-se a fornecer aos usuários do Windows, instruções para executar com sucesso o Jekyll - e não apenas no momento de sua criação, mas espero que também no futuro, quando as soluções se tornarem obsoletas novamente.

Algumas notas antes de iniciar
---------------------------------

* Exceto quando indicado, o conteúdo deste repositório está licenciado com Licença Creative Commons Atribuição
3.0. Você pode encontrar uma cópia da licença na [arquivo de licença](LICENSE-PT-BR). 
* Quaisquer reclamações de responsabilidade relativas a danos causados **pelo uso de qualquer informação fornecida, incluindo qualquer tipo de 
informações incorretas ou esparsa, será rejeitado. ** Use as informações fornecidas NESTA PÁGINA POR SUA CONTA E RISCO**.

* * *

## Visão geral ##

Abaixo, você encontrará instruções para instalar...

* ... Ruby. [ir a seção](#instalar-ruby)
* ... o Kit Dev para Ruby para ser capaz de construir extensões nativas. [ir a seção](#instalar-o-ruby-devkit)
* ... o gem Jekyll. [ir a seção](#instalar-o-gem-jekyll)
* ... Python para ser capaz de usar o Pygments, um marcador de sintaxe, com Jekyll. [ir a seção](#instalar-python)
* ... Python setuptools e pip para instalar a parte do Python do Pygments. [ir a seção](#install-setup\_tools)
* ... a versão de trabalho do gem Pygments. [ir a seção](#instalar-python-parte-do-pygments)
*** Para a criação deste tutorial em português (Brasileiro) foi utilizado o sistema operacional Windows 8.1 - x64.

Finalmente, você vai ser capaz de [Executar o Jekyll](#executar-jekyll) no Windows usando um último truque.

## Instalar Ruby ##

Ruby é a linguagem que o Jekyll é escrito. Bem, você precisa instalar ele para começar.

1. Faça o download do instalador do Ruby (RubyInstaller) em [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * A versão 2.0.0 deve funcionar bem.
  * Tenha certeza que está fazendo o download do pacote correto, dependedo da arquitetura do seu sistema: x86 / x64
2. Execute o instalador, que irá guia-lo durante o processo de instalação.
  * A única personalização que você deve fazer para o nosso propósito é marcar a caixa "Add Ruby executables to your
    PATH" na tela onde é solicitado o caminho da instalação (Ex.: C:\Ruby).
3. Após clicar em Install, tudo estará pronto para o Ruby!

## Instalar o Ruby DevKit ##

Algumas das dependências do Jekyll precisam ser construídas como "extensões nativas". Para fazer isso, você vai precisar do Rubi DevKit.

1. Faça o download do pacote em [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * A versão e a arquitetura (32/64 bits) do DevKit's precisa ser correspondente a da instalação do Ruby.
2. O que você tem agora é um arquivo auto-extraível.
  * Execute o arquivo.
  * Altere o caminho destino de extração para algo como `C:\rubydevkit\`.
  * Extraia o arquivo.
  * **Nota**: Por alguma razão, a extração pode falhar se você tiver vários outros programas em execução.
3. Inicializar o DevKit e vinculá-lo a sua instalação do Ruby (via sua ferramenta de linha de comando de preferência).
  * Navegue até a pasta que você extraiu o DevKit.

            cd "C:\rubydevkit\"

  * Auto-detectar instalações do Ruby e adicioná-las a um arquivo de configuração.

            ruby dk.rb init

  * Instale o DevKit.

            ruby dk.rb install

## Instalar o gem Jekyll ##

A última versão do Jekyll no momento da escrita deste tutorial é **v2.0.3, que é compatível com ambientes Windows.
** Não tente instalar Jekyll **v1.4.3, que é conhecido por ser incompatível com o Windows.
** (Para mais informações veja em [jekyll/jekyll#1948](https://github.com/jekyll/jekyll/issues/1948))

1. Instale a última versão do Jekyll através da linha de comando.

        gem install jekyll

2. Assista e aproveite.

Futuras versões do Jekyll podem voltar a ser incompatíveis com o Windows. Volte aqui quando uma nova versão é lançada para ver se ele continua a ser compatível.

* * *

Agora, você tem o Jekyll instalado no seu computador com Windows. Se você tem certeza de que nunca vai precisar usar Pygments, 
você pode pular para a seção [Executar o Jekyll](#run-jekyll). Caso contrário, continue a ler para utilizar o Pygments.

* * *

## Instalar o ambiente Python

Se você quiser usar Pygments, que é uma dependência padrão do Jekyll, para destaques de sintaxe no Windows, você precisa 
instalar Python, setuptools e pip.

### Instalar o Python ###

1. Faça o download do instalador do Python em [python.org](http://www.python.org/download/).
  * Atualmente sabe-se que o Python versão 3 não funciona com o Jekyll. Use o Python versão 2.7.7.
  * Novamente, tenha certeza que o pacote baixado seja o mesmo que o seu sistema (x86/x64)
2. Execute o instalador. Todos os valores padrão estão certos.

### Instalar o setuptools ###

1. Baixe o instalador do setuptools que corresponde ao seu sistema e sua instalação do Python
   [here](http://www.lfd.uci.edu/~gohlke/pythonlibs/#setuptools).
2. Execute o instalador.
  * Se você usou os valores padrão durante a instalação do Python, você pode fazer o mesmo aqui. Caso contrário, digite o caminho
  correto.

### Instalar o pip ###

1. Baixe o instalador do pip que corresponde ao seu sistema e sua instalação do Python
   [here](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pip).
2. Execute o instalador.
  * Se você usou os valores padrão durante a instalação do Python, você pode fazer o mesmo aqui. Caso contrário, digite o caminho
  correto.

### Adicionar pip e Python para a sua variável de ambiente PATH ###

Antes de poder utilizar o pip a partir da linha de comando para instalar o Pygments, você precisa adicionar o Python às suas 
variáveis de ambiente, PATH.

1. Adicione `C:\path-to-your-python-installation\Scripts;` no _início_ do seu PATH em **Variáveis de de Usuário**. A ponto-e-vírgula (;)
   é importante! Sem ela, você irá estragar o PATH. Se você usou todas as configurações padrão, a string que deverá adicionar 
   é `C:\Python27\Scripts;`. Claro, você também pode colocar o ponto-e-vírgula antes do novo caminho e adicioná-lo ao _final_
   do seu PATH em **Variáveis de Usuário**: `;C:\Python27\Scripts`
2. Adicione `C:\path-to-your-python-installation\;` no _início_ do seu PATH em **Variáveis do Sistema**. O ponto-e-vírgula (;)
   é importante! Sem ele, você irá estragar o PATH. Se você usou todas as configurações padrão, a strint que deverá adicionar
   é `C:\Python27\;`. Claro, você também pode colocar o ponto-e-v[irgula antes do novo caminho e adicioná-lo ao _final_
   do seu PATH em **Variáveis de Sistema**: `;C:\Python27\`

## Instalar Python parte do Pygments ##

Abra uma nova janela de linha de comando e execute o comando:

    pip install Pygments

## Instalar a versão de trabalho do Ruby parte Pygments ##

Pygments.rb recentemente foi reparado um bug que causou falha ao Jekyll quando tentava-se compilar sites que usam o Pygments. Para utilizar Jekyll com projetos que utilizam Pygments para destaque de código, certifique-se que você tem uma versão de trabalho do Pygments instalado. As versões conhecidas para trabalhar incluem `0.5.0` (recomendado) e `0.5.4` mas não as que estão entre estas versões.

1. Saiba qual a versão do Pygments você tem instalada.
  * Execute `gem list` e procure por `pygments.rb` no que é exibido.
  * Você pode encontrar a versão que tem instalada ao lado do nome na lista.

            ...
            pygments.rb (0.5.?)
            ...

  * Se você tem instalda a versão `0.5.0` ou `0.5.4`, você está pronto para continuar.
  * **Nota:** Usando a versão `0.5.4`, você poderá receber avisos quando você executar Jekyll, mas o seu site deve ser gerado com sucesso.

            ...
                Generating... C:/Ruby200-x64/lib/ruby/gems/2.0.0/gems/posix-spawn-0.3.8/lib/posix/spawn.rb:162: warning: cannot close fd before spawn
                              done.
              Server address: http://0.0.0.0:9001
            Server running... press ctrl-c to stop.
            ...

2. Se necessário (veja acima), desinstale qualquer versão quebrada do Pygments. Confirme se você quer quebrar a dependência de Jekyll (temporariamente).

        gem uninstall pygments.rb --version "=0.5.2"
        ...
        Continue with Uninstall? [yN] y

3. Instale uma versão para trabalho do Pygments.

        gem install pygments.rb --version "=0.5.0"

## Execute o Jekyll ##

Dependendo do seu site individualmente, problemas devido à codificação de caracteres incompatíveis podem surgir. Para evitar esses, mude a codificação de sua linha de comando para UTF-8 antes de navegar para a sua pasta de origem local e executar o comando Jekyll de sua escolha.

    chcp 65001
    cd "C:\my-site\"
    jekyll serve

Você precisa fazer isso toda vez que você abrir uma nova linha de comando antes de executar Jekyll.

Você pode, alternativamente, adicionar a seguinte configuração para o seu arquivo `_config.yml`, se isso é uma opção:

    encoding: UTF-8

**Nota:** Isso só vai mudar a codificação para um site. Você vai precisar de continuar a usar o comando `chcp 65001` para outros sites (a menos que você adicione a definição para eles também).

### Use o Jekyll watch ###

Se você quiser usar o recurso de auto-regeneração do Jekyll's auto-regeneração (`jekyll serve --watch` / `jekyll serve -w`), você precisa ter o gem Ruby  *wdm* instalado.

Você pode:

* Verifique o sistema operacional e instale a gem somente se necessário (no Windows), se o seu site tem um Gemfile. Adicione isso ao Gemfile:

        require 'rbconfig'
        gem 'wdm', '~> 0.1.0' if RbConfig::CONFIG['target_os'] =~ /mswin|mingw/i

* Instale o gem manualmente, se o seu site não tem um Gemfile. Execute o comando:

        gem install wdm
