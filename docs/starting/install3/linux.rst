.. _install3-linux:

Instalando Python 3 en Linux
============================

.. image:: https://farm5.staticflickr.com/4276/34435689480_2e6f358510_k_d.jpg

Este documento describe como instalar Python 3.6 en máquinas Ubuntu Linux.

Para ver que versión de Python 3 tienes instalada, abre una terminal y ejecuta

.. code-block:: console

    $ python3 --version

Si estás usando Ubuntu 16.10 o uno más nuevo, entonces puedes fácilmente instalar Python 3.6 con los siguientes comandos::

    $ sudo apt-get update
    $ sudo apt-get install python3.6

Si estás usando otra versión de Ubuntu (p.ej. el último release LTS), recomendamos usar el `deadsnakes PPA <https://launchpad.net/~fkrull/+archive/ubuntu/deadsnakes>`_ para instalar Python 3.6::

    $ sudo add-apt-repository ppa:fkrull/deadsnakes
    $ sudo apt-get update
    $ sudo apt-get install python3.6

Si estáß usando otra distribución de Linux, hay posibilidades que ya tengas Python 3
pre-instalado también. Si no, usa el manejador de paquetes de tu dsitribución.
Por ejemplo en Fedora, deberás usar `dnf`:

.. code-block:: console

    $ sudo dnf install python3

Mira si la versión del paquete de ``python3`` no es lo suficientemente actual
para ti, habrá modos de instalar versiones más recientes también,
dependiendo de tu distribución. Por ejemplo instalando el paquete ``python36`` en
Fedora 25 para tener Python 3.6. Si eres un usuario Fedora, talvez quieras
leer sobre `multiple Python versions available in Fedora`_.

.. _múltiples versiones de Python disponibles en Fedora: https://developer.fedoraproject.org/tech/languages/python/multiple-pythons.html


Trabajando con Python 3
-----------------------

En este punto, puedes tener Python 2.7 disponible también.

.. code-block:: console

    $ python

Esto lanzará el interprete de Python 2.

.. code-block:: console

    $ python3

Esto lanzará el interprete de Python 3.

Setuptools & Pip
----------------

Los dos paquetes de terceros de Python más cruciales son `setuptools <https://pypi.python.org/pypi/setuptools>`_ y `pip <https://pip.pypa.io/en/stable/>`_.

Una vez instalado, puedes descargar, instalar y desinstalar cualquier software de Python compatible
con sólo un comando. También agrega capacidad para instalación sobre red
para tu softwware Python con muy poco trabajo.

Python 2.7.9 y posteriores (en la serie python2), y Python 3.4 y posteriores incluido
pip por defecto.

Para ver si pip está instalado, abre una terminal y ejecuta

.. code-block:: console

    $ command -v pip

Para instalar pip, `sigue la guía oficial de instalación de pip <https://pip.pypa.io/en/latest/installing/>`_ - esto instalará automáticamente la última versión de setuptools.

Ten en cuenta que en algunas distribuciones Linux incluida Ubuntu y Fedora el comando ``pip``
funciona con Python 2, mientras que el comando ``pip3`` funciona para Python 3.

.. code-block:: console

    $ command -v pip3

Sin embargo, cuando usas ambientes virtuales (descritos a continuación), no necesitas
preocuparte sobre eso.


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
