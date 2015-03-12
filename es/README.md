Cómo utilizar Jekyll en Windows
============================

Desgraciadamente, instalar y ejecutar [Jekyll](http://jekyllrb.com) bajo **Windows** no es una tarea tan sencilla como lo es ejecutarlo en *Mac OSX* o *Linux*.

No obstante, utilizar _Jekyll_ desde un equipo con Windows **no es imposible**. De hecho, puede encontrar multitud de tutoriales – algunos más útiles que otros - que ofrecen instrucciones de cómo instalar y utilizar Jekyll desde equipos Windows. La mayoría de ellos son entradas de blog que, frecuentemente, se encuentran desactualizados.

Por eso, este repositorio está pensado para proporcionar a los usuarios de Windows las instrucciones necesarias para instalar y ejecutar Jekyll correctamente. La información contenida aquí pretende estar actualizada, incluso cuando la propia evolución de la aplicación _Jekyll_ o de sus prerrequisitos provoque que no funcione el método de instalación que explicamos aquí.

Antes de empezar...
------------------------------
* A menos que se indique lo contrario, el contenido en este repositorio está licenciado bajo la licencia **Creative Commons Attribution 3.0**. Puede encontrar una copia de la licencia en el archivo [LICENSE](LICENSE) correspondiente.
* Cualquier reclamación de responsabilidad por daños causados por el uso de cualquier información proporcionada, incluyendo cualquier tipo de información incorrecta o incompleta, serán rechazadas.

 ** UTILICE LA INFORMACION PROPORCIONADA EN ESTA PÁGINA BAJO SU PROPIO RIESGO.**

* * *

Introducción
------------------
En este manual encontrará las instrucciones para instalar...

* ... **Ruby**. [saltar a sección](#instalación-de-ruby)
* ... El **kit de desarrollo** de Ruby (DevKit), necesario para desarrollar - y compilar - extensiones nativas. [saltar a sección](#instalación-del-devkit-de-ruby)
* ... la gema **Jekyll**. [saltar a sección](#instalación-de-la-gema-de-jekyll)
* ... **Python**, con el objetivo de utilizar _Pygments_, una extensión para dar formato a snippets de código desde _Jekyll_. [saltar a sección](#instalar-el-entorno-de-python)
* ... **setuptools** y **pip**, para instalar la parte de _Pygments_ correspondiente a _Python_. [saltar a sección](#instalación-de-setuptools)
* ... la gema de **Pygments**. [saltar a sección](#instalación-de-una-versión-funcional-de-la-parte-ruby-de-pygments)

Una vez termine este tutorial, será capaz de [ejecutar Jekyll](#ejecutar-jekyll) en sistemas Windows.

## Instalación de Ruby ##

En primer lugar, dado que _Jekyll_ está escrito en lenguaje **Ruby**, necesitará instalar el lenguaje y el entorno de ejecución de _**Ruby para Windows**_ para poder continuar.

1. Descargue el instalador de _Ruby_ desde [rubyinstaller.org](http://rubyinstaller.org/downloads/).
 * La versión 2.0.0 debería funcionar bien.
 * Asegúrese de descargar el paquete correcto dependiendo de la arquitectura de tu sistema operativo: **x86** / **x64**
2. Ejecute el instalador, el cual le guiará a través del proceso de instalación.
  * La única personalización que necesita realizar para nuestro propósito es marcar la opción
    _**"Add Ruby executables to your PATH"**_ en la última pantalla antes de completar la instalación.
3. Después de hacer clic en _**Install**_... ¡finalizará la configuración de Ruby!

## Instalación del Devkit de Ruby ##

Algunas de las dependencias de Jekyll necesitan ser construidas (built) como **extensiones nativas**. Para conseguirlo, es necesario el _**Development Kit**_ o _**DevKit**_ de Ruby.

1. Descargue el paquete de [rubyinstaller.org](http://rubyinstaller.org/downloads/).

  * La versión de Devkit y la arquitectura de su sistema operativo (**x86** / **x64**) deben coincidir con las de la instalación previa de Ruby.

2. La descarga consiste en un archivo auto-extraíble. Para continuar:

 * Ejecute el archivo.
 * Cambie el destino de la extracción a una ruta sencilla como _**C:\rubydevkit**_.
 * Descomprima el archivo.

 **Nota**: Es posible que la extracción falle si tiene muchos programas ejecutándose durante la instalación.

3. Inicialice el _DevKit_ y enlácelo a su instalación de _Ruby_ mediante su herramienta de línea de comandos preferida.
  * Navegue a la carpeta en la que extrajo _Devkit_.

            cd "C:\rubydevkit\"

  * El proceso de inicialización se encarga de detectar automáticamente las instalaciones existentes de Ruby en el equipo y agregarlas a un archivo de configuración. Para inicializar el DevKit, ejecute la siguiente instrucción:

            ruby dk.rb init

  ** Nota**: Edite el fichero `config.yml` generado por la instrucción anterior para comprobar si se ha configurado la ruta destino del entorno _Ruby_ instalado previamente. Si no existiera, siga las instrucciones disponibles en el fichero `config.yml` generado para incluir dicha ruta.

  * Para instalar el _DevKit_.

            ruby dk.rb install


## Instalación de la gema de Jekyll ##

La última versión de _Jekyll_ disponible en el momento de escribir la última versión de este documento es la versión `2.5.3`, versión que es compatible con entornos Windows.

No intente instalar versiones anteriores de Jekyll como la versión `1.4.3`, ya que es posible que sea incompatible con Windows.

Para más información, consulte [jekyll/jekyll#1948](https://github.com/jekyll/jekyll/issues/1948).

1. Instale la última versión de Jekyll desde la línea de comandos.

        gem install jekyll

2. Espere a que termine el proceso de actualización de gemas.

Debe tener en cuenta que es posible que en futuras versiones de Jekyll se generen nuevas incompatibilidades con Windows.

Vuelva a revisar este documento cuando se lance una nueva versión para ver si ésta sigue siendo compatible o no.

* * *

Desde este momento tiene instalado *Jekyll* en equipo Windows. Si está seguro de nunca necesitará usar _Pygments_, puede saltar a la sección [Ejecutar Jekyll](#ejecutar-jekyll). En caso contrario, continúe leyendo la siguiente sección para saber cómo configurar _Pygments_.

* * *

## Instalar el entorno de Python ##

Para utilizar **Pygments** (dependencia de Jekyll para el resaltado de sintaxis en Windows), necesita instalar **Python**, **setuptools** y **pip**.

### Instalación de Python ###
1. Descargue el instalador de Python desde [python.org](http://www.python.org/download/).
 * _Python **3**_ es incompatible con _Jekyll_. Use Python **2.7.8** en su lugar.
 * De nuevo, asegúrese de descargar el paquete destinado a su sistema (**x86** / **x64**).
2. Ejecute el instalador, manteniendo los valores por defecto del proceso de instalación.

### Instalación de setuptools ###

1. Descargue el instalador de **setuptools** que coincida con su sistema y su instalación de _Python_ desde [aquí](http://www.lfd.uci.edu/~gohlke/pythonlibs/#setuptools).
2. Ejecute el instalador.
 * Si usó los valores por defecto al instalar _Python_, puede hacer lo mismo aquí. En caso contrario, deberá indicar la ruta correcta donde se encuentre instalado _Python_.

### Instalación de pip ###

1. Descargue el instalador de **pip** que coincida con su sistema y su instalación de Python desde [aquí](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pip).
2. Ejecute el instalador.
 * Si usó los valores por defecto al instalar _Python_, puede hacer lo mismo aquí. En caso contrario, deberá indicar la ruta correcta donde se encuentre instalado _Python_.

### Agregar pip y Python a su variable de entorno PATH ###

Antes de poder utilizar _pip_ desde la línea de comandos para instalar _Pygments_, necesita agregar la ruta donde se instaló su entorno _Python_ a la variable de entorno **PATH**.

Para ello, tiene dos opciones.

1. Agregar `C:\path-to-your-python-installation\Scripts;` al inicio de su variable de **usuario** PATH.

2. Agregar `C:\path-to-your-python-installation\;` al inicio de su variable PATH de **sistema**.

***

** Atención:** ¡Los punto y coma son importantes!

** NOTA 1:** Si usó todos los valores por defecto durante la instalación, el nuevo valor a añadir será `C:\Python27\Scripts;`.

** NOTA 2:** Por supuesto, en ambos casos también puede poner el punto y coma antes y después del nuevo path y agregarlo al final de su variable PATH: `;C:\Python27\Scripts;`


## Instalación de Pygments en Python##

Abra una nueva ventana de la línea de comandos y ejecute el siguiente comando:

    pip install Pygments

## Instalación de Pygments para Ruby##

En su momento, en `pygments.rb` se corrigió un error que causaba que _Jekyll_ fallara cuando se intentaba compilar sitios que utilizaban _Pygments_. Para poder utilizar _Jekyll_ en proyectos que usen _Pygments_ para el resaltado de sintaxis, asegúrese de tener una versión válida de _Pygments_.
Algunas de las versiones conocidas que sí funcionan son la `0.5.0` (recomendada) y la `0.5.4`.

1. Averigüe qué versión de Pygments tiene instalada.

 * Ejecute 'gem list' y busque 'pygments.rb' en el resultado.
 * Para saber qué versión tiene instalada, ésta aparece tras el nombre de cada gema en el listado.

            ...
            pygments.rb (0.5.?)
            ...

  Si su instalación se corresponde con las versiones `0.5.0` o `0.5.4`, puede continuar.

 **Nota:** Al usar la versión `0.5.4`, podría recibir _warnings_ cuando ejecute _Jekyll_, pero la generación del sitio web _Jekyll_ debería ser correcto.


                ...
                Generating... C:/Ruby200-x64/lib/ruby/gems/2.0.0/gems/posix-spawn-0.3.8/lib/posix/spawn.rb:162: 
                       warning: cannot close fd before spawn done.
                Server address: http://0.0.0.0:9001
                Server running... press ctrl-c to stop.
                ...

2. Si fuese necesario (ver punto anterior), desinstale cualquier versión incompatible de _Pygments_. Para eliminar la dependencia incompatible con _Jekyll_, ejecute:

        gem uninstall pygments.rb --version "=0.5.2"
        ...
        Continue with Uninstall [yN] y

3. Instale una versión compatible de _Pygments_.

        gem install pygments.rb --version "=0.5.0"

## Ejecutar Jekyll ##

En función del sitio que quiera generar, es posible que surjan problemas por incompatibilidad con la codificación de caracteres. Para evitar estos problemas, cambie la codificación de su línea de comandos a `UTF-8` antes de navegar a la carpeta con el código fuente de su sitio y ejecute el comando _Jekyll_ correspondiente.

    chcp 64001
    cd "C:\my-site"
    jekyll serve

Es necesario realizar esta acción cada vez que abra una ventana de comandos y antes de ejecutar cualquier opción de _Jekyll_.

No obstante, existe la alternativa - si fuese opción en su caso - de agregar la siguiente configuración a su archivo `_config.yml`:

    encoding: UTF-8

**Nota:** Esta configuración sólo cambia la codificación para el sitio web concreto al que pertenece el fichero. Necesitará usar el comando `chcp 64001` en otros sitios web (a menos que también agregue esta configuración en cada uno de ellos).

## Dejemos que Jekyll observe... ##

Si quiere usar la característica de auto-regeneración de _Jekyll_ (`jekyll serve --watch` / `jekyll serve -w`), necesita tener también instalada la gema **wdm** de _Ruby_.

Para ello, existen dos opciones:

1. Añadiendo el siguiente fragmento de configuración al fichero `Gemfile` de si sitio web:

        require 'rbconfig'
        gem 'wdm', '~> 0.1.0' if RbConfig::CONFIG['target_os'] =~ /mswin|mingw/i

2. Instale la gema manualmente, si su sitio no tiene un arhivo `Gemfile`. Para ello, ejecute este comando:

        gem install wdm
