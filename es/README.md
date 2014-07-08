How to Run Jekyll on Windows
============================

Desgraciadamente, ejecutar [Jekyll](http://jekyllrb.com) en windows no es tan facil como lo es ejecutarlo en Mac OS X o Linux, la cual tambien es la razón de no estar soportado o documentado oficialmente.

Pienso que ejecutar Jekyll en Windows no es imposible. De hecho, hay un montón de tutoriales ahí afuera, algunos de más ayuda que otros. La mayoría de estos están escritos como "entradas de blog", por lo cual es frecuente que se sean inexactos o se encuentren desactualizados con el tiempo.

Este repositorio, está pensado para proporcionar a los usuarios de Windows, instrucciones para ejecutar Jekyll correctamente - no solo al momento de su creación sino espero también en el futuro, cuando las soluciones comunes se desactualizan otra vez.

Algunas notas antes de empezar
------------------------------
* Excepto que se indique lo contrario, el contenido en este repositorio está licenciado bajo la licencia Creative Commons Attribution 3.0. Puedes encontrar una copia de la licencia en el archivo [LICENSE](LICENSE).
* Las reclamaciones de responsabilidad por daños causados ​​por el uso de cualquier información proporcionada, incluyendo cualquier tipo de información incorrecta o escasa, será rechazada. ** USAR LA INFORMACION PROPORCIONADA EN ESTA PÁGINA BAJO SU PROPIO RIESGO.

* * *

## Generalidades ##
Abajo encontrarás las instrucciones para instalar...

* ... Ruby. [saltar a sección](#instalación-de-ruby)
* ... El kit de desarrollo (DevKit), para ser capaces de desarrollar extensiones nativas. [saltar a sección](#instalación-del-devkit-de-ruby)
* ... La gema de Jekyll. [saltar a sección](#instalación-de-la-gema-de-jekyll)
* ... Python, para ser capaces de utilizar Pygments, un resaltador de sintáxis, con Jekyll. [saltar a sección](#instalar-el-entorno-de-python)
* ... setuptools y pip, para instalar la parte de Pygments correspondiente a Python. [saltar a sección](#instalación-de-setuptools)
* ... Una versión funcional de la gema de Pygments. [saltar a sección](#instalación-de-una-versión-funcional-de-la-parte-ruby-de-pygments)

Finalmente, serás capaz de [Ejecutar Jekyll](#ejecutar-jekyll) en windows usando un último truco.

## Instalación de Ruby ##

Ruby es el lenguaje en el que Jekyll está escrito. Necesitaremos instalarlo primero para poder empezar.

1. Descarga el Instalador de Ruby de [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * La versión 2.0.0 debería funcionar bien.
  * Asegurate de descargar el paquete correcto dependiendo de la arquitectura de tu sistema operativo: x86 / x64
2. Ejecuta el instalador, el cual te guiará a través del proceso de instalación.
  * La única personalización que necesitas realizar para nuestros propósitos es "checkear" la opción
    "Add Ruby executables to your PATH" en la última pantalla antes de de instalación.
3. Despues de hacer click en "Install", finalizamos la configuración de ruby!

## Instalación del Devkit de Ruby ##

Algunas de las dependencias de Jekyll, necesitan ser construidas (built) como "extensiones nativas". Para hacer esto, necesitas el Devkit de Ruby.

1. Descarga el paquete de [rubyinstaller.org](http://rubyinstaller.org/downloads/).
  * La versión de Devkit y la arquitectura destino (32/64 bit) deben coincidir con las de la instalación de Ruby.
2. Lo que tienes ahora es un archivo auto-extraible.
  * Ejecuta el archivo.
  * Cambia el destino de la extracción a algo como 'C:\rubydevkit'.
  * Extrae el archivo.
  * **Nota**: Por alguna razón, la extración podría fallar si tienes muchos programas ejecutándose.
3. Inicializa el Devkit y enlázalo a tu instalación de Ruby (mediante tu herramienta de línea de comandos preferida).
  * Navega a la carpeta en la que extrajiste Devkit.

          cd "C:\rubydevkit\"
  * Autodetecta las instalaciones de Ruby y agregalas a un archivo de configuración.

          ruby dk.rb init

  * Instala el DevKit.

          ruby dk.rb install


## Instalación de la gema de Jekyll ##

La última version de Jekyll al momento de escribir esto es : **v1.5.1, la cual es compatible con entornos Windows**. No intentes instalar Jekyll **v1.4.3, la cual es conocida por ser incompatible con Windows.** (Ver [jekyll/jekyll#1948](https://github.com/jekyll/jekyll/issues/1948) para más información.)

1. Instala la última versión de Jekyll desde la línea de comandos.

        gem install jeyll

2. Observa y disfruta.

Futuras versiones de Jekyll podrían ser imcompatibles una vez más con Windows. Vuelve a revisar esto, cuando una nueva versión sea lanzada para ver si permanece compatible.


* * *

Ahora tienes instalado Jekyll en tu instalación de Windows. Si estás seguro de nunca necesitar Pygments, puesde saltarte a la sección [Run Jekyll](#run-jekyll). De otra forma, lee sobre ejecutar Pygments.

* * *

## Instalar el entorno de Python ##

Si quieres utilizar Pygments, la cual es una dependencia de Jekyll para el resaltado de sintaxis en Windows, necesitas instalar Python, setuptools y pip.

### Instalación de Python ###

1. Descarga el instalador de Python de [python.org](http://www.python.org/download/).
  * Python 3 es actualmente conocido por no funcionar con Jekyll. Usa Python 2.7.5.
  * Otra vez, asegurate de descargar el paquete destinado a tu sistema.
2. Ejecuta el instalador. Todos los valores por defecto deberían estar bien.

### Instalación de setuptools ###

1. Descargar el instalador de setuptools que coincida con tu sistema y tu instalación de python desde [acá](http://www.lfd.uci.edu/~gohlke/pythonlibs/#setuptools).
2. Ejecuta el instalador.
  * Si usaste los valores por defecto al instalar Python, puedes hacer lo mismo aquí. De otra forma, ingresa el path correcto.


### Instalación de pip ###

1. Descarga el instalador de pip que coincida con tu sistema y tu instalación de python desde [acá](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pip).
2. Ejecuta el instalador.
  * Si usaste los valores por defecto al instalar Python, puedes hacer lo mismo aquí. De otra forma, ingresa el path correcto.

### Agregar pip y Python a tu variable de entorno PATH ###

Antes de poder utilizar pip desde la línea de comandos para instalar Pygments, necesitas agregar tu entorno Python a la variable de entorno PATH.

1. Agrega `C:\path-to-your-python-installation\Scripts;` al inicio de tu variable de **usuario** PATH. El punto y coma es importante! Sin él, te pederás en tu PATH. Si usaste todos los valores por defecto, la cadena por agregar debería ser `C:\Python27\Scripts;`. Por supuesto tambien puedes poner el punto y coma antes del nuevo path y agregarlo al final de tu variable PATH de **usuario** : `;C:\Python27\Scripts`
2. Agrega `C:\path-to-your-python-installation\;` al inicio de tu variable de **sistema** PATH. El punto y coma es importante! Sin él, te perderás en tu PATH. Si usaste todos los valores por defecto, la cadena por agregar debería ser `C:\Python27\;`. Por supuesto, tambien puedes poner el punto y coma antes del nuevo path y agregarlo al final de tu variable PATH del **sistema** : `;C:\Python27\`

## Instalación de la parte Python de Pygments ##

Abre una nueva ventana de la línea de comandos y ejecuta el siguiente comando:
    
    pip install Pygments


## Instalación de una versión funcional de la parte Ruby de Pygments ##

Recientemente pygments.rb corrigió un error que causaba que Jekyll fallara cuando se intentaba compilar sitios que utilizaban Pygments. Para poder utilizar Jekyll en proyectos que usen Pygments para el resaltado de sintáxis, asegurate de tener una versión funcionando de Pygments. Las versiones conocidas por funcionar son '0.5.0' (recomendada) y '0.5.4' pero no aquellas entre estas.

1. Averigua que versión de Pygments tienes instalada.
  * Ejecuta 'gem list' y busca 'pygments.rb' en el resultado.
  * Puedes encontrar la versión que tienes instalada, a continuación del nombre en la lista.

          ...
          pygments.rb (0.5.?)
          ...
  * Si tu instalación es '0.5.0' o '0.5.4', estás listo para continuar.
  * **Nota:** Al usar la versión '0.5.4', podrías recibir warnings cuando ejecutes Jekyll, pero tu sitio debería ser correctamente generado.

            ...
                Generating... C:/Ruby200-x64/lib/ruby/gems/2.0.0/gems/posix-spawn-0.3.8/lib/posix/spawn.rb:162: warning: cannot close fd before spawn
                              done.
              Server address: http://0.0.0.0:9001
            Server running... press ctrl-c to stop.
            ...
2. Si es necesario (ver arriba), desinstala cualquier versión rota de Pygments. Confirma que quieres eliminar la dependencia de Jekyll (temporalmente).

        gem uninstall pygments.rb --version "=0.5.2"
        ...
        Continue with Uninstall [yN] y

3. Instala una versión funcionar de Pygments.
        gem install pygments.rb --version "=0.5.0"

## Ejecutar Jekyll ##

Dependiendo de su sitio, podrían surgir problemas debido a la incompatiblidad de codificación de caracteres. Para evitarlos, cambia la codificación de tu línea de comandos a UTF-8 antes de navegar a la carpeta fuente de tu sitio y ejecutar el comando Jekyll de tu elección.

    chcp 64001
    cd "C:\my-site"
    jekyll serve

Necesitas hacer esto cada vez que abras una nueva ventana de comandos, antes de ejecutar Jekyll.

Alternativamente, si es una opción, puedes agregar la siguiente configuración a tu archivo '_config.yml':

    encoding: UTF-8

**Note:** Esto solo cambia la codificación para un sitio. Necesitarás usar continuamente el comando 'chcp 64001' para otros sitios ( a menos de que también agregues esta configuración).

## Dejemos que Jekyll Observe ##

Si quieres usar la característica de auto-regeneración de Jekyll ('jekyll serve --watch' / 'jekyll serve -w'), necesitas tener instalada la gema *wdm*.

Puedes:

* Verificar el sistema operativo e instalar la gema solo si es necesaria (en Windows), si tu sitio tiene un archivo Gemfile. Agrega esto al Gemfile:

        require 'rbconfig'
        gem 'wdm', '~> 0.1.0' if RbConfig::CONFIG['target_os'] =~ /mswin|mingw/i

* Instala la gema manualmente, si tu sitio no tiene un arhivo Gemfile. Ejecuta este comando:

        gem install wdm
