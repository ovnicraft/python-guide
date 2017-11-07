:orphan: This article should not be added to a toctree for now

.. _install3-osx:

Instalando Python 3 en Mac OS X
===============================

.. image:: https://farm5.staticflickr.com/4276/34435689480_2e6f358510_k_d.jpg

La última versión de Mac OS X, Sierra, **viene con Python 2.7 por defecto.**

Tu no necesitas instalar o configurar nada más para usar Python 2. Estas
instrucciones documentan la instalación de Python 3.

La versión que viene con OS X está bien para aprendizaje, pero no es lo mejor
para desarrollo. La versión enviada con OS X puede estar desactualizada de la
`publicación oficial actual de Python <https://www.python.org/downloads/mac-osx/>`_,
que es considerada la versión estable para producción.

Hacerlo Bien
------------

Vamos a instalar una versión real de Python.

Antes de instalar Python, necesitarás instalar GCC. GCC puede obtenerse
descargandolo desde `XCode <http://developer.apple.com/xcode/>`_, las pequeñas
`Herramientas de línea de comandos <https://developer.apple.com/downloads/>`_ (debes tener una
cuenta Apple) o incluso el más pequeño paquete `Instalador-OSX-GCC <https://github.com/kennethreitz/osx-gcc-installer#readme>`_.

.. note::
    Si ya tienes instalado XCode, no necesitas instalar OSX-GCC.
    En combinación, el software puede causar problemas que son difíciles de
    diagnosticar.

.. note::
    Si realizas una instalación nueva de XCode, también necesitarás agregar
    las herramientas de línea de comandos ejecutando ``xcode-select --install`` en el terminal.

Mientras OS X viene con un gran número de utilidades UNIX, quienes están familiarizados
con sistemas Linux se darán cuenta que hay un componente que falta: un manejador de paquetes.
`Homebrew <http://brew.sh>`_ resuelve este problema.

Para `instalar Homebrew <http://brew.sh/#install>`_, abrir :file:`Terminal` o
tu emulador de terminal favorito para OSX y ejecutar

.. code-block:: console

    $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

El script explicará que cambios hará y te preguntará antes que la
instalación inicie.
Una vez que has instalado Homebrew, inserta el directorio de Homebrew al inicio
de tu variable de ambiente :envvar:`PATH`. Puedes hacer esto agregando la siguiente
línea al final de tu archivo :file:`~/.profile`

.. code-block:: console

    export PATH=/usr/local/bin:/usr/local/sbin:$PATH

Ahora, podemos instalar Python 3:

.. code-block:: console

    $ brew install python3

Esto tomará uno o dos minutos.


Pip
---

Homebrew instala ``pip3`` por ti.

``pip3`` es un alias para ``pip`` apuntando al Python 3 de Homebrew.

Trabajando con Python 3
-----------------------

A este punto, tiene Python 2.7 disponible, potencialmente
:ref:`la versión Homebrew de Python 2 <install-osx>` instalado, y la versión
Homebrew de Python 3 también.

.. code-block:: console

    $ python

lanzará el interprete de Python.

.. code-block:: console

    $ python2

lanzará el interprete homebrew de Python 2 (si hay alguno).

.. code-block:: console

    $ python3

lanzará el interprete homebrew de Python 3 instalado.

Si la versión Homebrew de Python 2 está instalada entonces ``pip2`` apuntará a Python 2.
Si la versión Homebrew de Python 3 está instalada entonces ``pip3`` apuntará a Python 3.


Pipenv & Ambientes Virtuales
----------------------------

El siguiente paso es instalar Pipenv, con esto puedes instalar dependencias y manejar ambientes virtuales.

Un ambiente virtual es una herramienta para mantener las dependencias requeridas por diferentes proyectos
en lugares separados, creando ambientes virtuales para esos proyectos. Resuelve el dilema de
"El Proyecto X depende de la versión 1.x pero, el Proyecto Y necesita 4.x", y mantiene
tu directorio global site-packages limpio y administrable.

Por ejemplo, puedes trabajar en un proyecto que requiere Django 1.10 mientras también
mantienes un proyecto que requiere Django 1.8.

Por lo que en adelante, la documentación para :ref:`Pipenv & Ambientes Virtuales <virtualenvironments-ref>`

--------------------------------

Esta página es un mezcla de `otra guía <http://www.stuartellis.eu/articles/python-development-windows/>`_,
que está disponible bajo la misma licencia.
