.. _install3-windows:

Instalando Python 3 en Windows
==============================

.. image:: https://farm5.staticflickr.com/4276/34435689480_2e6f358510_k_d.jpg

Primero, descarga la `última versión <https://www.python.org/ftp/python/3.6.3/python-3.6.3.exe>`_
de Python 3.6 desde el sitio oficial. Si deseas estar seguro que esas instalando una versión
totalmente actualizada, clic en en link de Downloads > Windows de la página inicial de
`sitio web de Python.org <http://python.org>`_ .

Por diseño, Python instala en un directorio con la versión embebida
p.ej. la versión de Python 3.6 se instalará en :file:`C:\\Python36\\`, así que puedes tener
múltiples versiones de Python en el
mismo sistema sin conflictos. De seguro, sólo un interprete puede ser
la aplicación por defecto para los archivos de tipo Python. Esto no modifica automáticamente
la variable de ambiente :envvar:`PATH`, así que siempre tienes el control sobre
que copia de Python correr.

Escribir la ruta completa para el interprete de Python interpreter puede convertirse
en algo tedioso, así que agregar los directorios de tu versión por defecto de Python a la variable :envvar:`PATH`.
Asumiendo que tu instalación de Python está en :file:`C:\\Python36\\`, agrega esto a tu
:envvar:`PATH`:

.. code-block:: console

    C:\Python36\;C:\Python36\Scripts\

Tu puedes hacerlo facilmente ejecutando lo siguiente en ``powershell``:

.. code-block:: console

    [Environment]::SetEnvironmentVariable("Path", "$env:Path;C:\Python36\;C:\Python36\Scripts\", "User")

Esto también es una opción durante el proceso de instalación.

El segundo (:file:`Scripts`) directorio recibe archivos de comandos cuando algunos
paquetes son instalados, es muy útil agregarlo.
Tu no necesitas instalar o configurar nada mas para usar Python. Dicho
eso, Te recomiendo que instales las herramientas y librerías
descritas en la siguiente sección antes de empezar a construir aplicaciones Python
para uso en el mundo real. En particular, siempre debes instalar Setuptools, ya que
hace mucho más fácil usar librerías Python de terceros.

Trabajando con  Python 3
------------------------

En este punto, también debes tener instalado Python 2.7.

.. code-block:: console

    $ python

Esto ejecutará el interprete de Python 2.

.. code-block:: console

    $ python3

Esto ejecutará el interprete de Python 3.


Setuptools + Pip
----------------

El software Python de terceros más crucial de todos es Setuptools, que
extiende las facilidaes de empaquetado e instalación entregadas por disutils en
la librería estandar. Una vez que agregas Setuptools a tu sistema Python puedes
descargar e instalar cualquier software Python compatible con solo un
comando. También te permite agregar capacidades de instalación en red a
tu software Pytohn con muy poco trabajo.

Para obtener la última versión de Setuptools para Windows, ejecuta el script de Python
disponible aquí: `ez_setup.py <https://bootstrap.pypa.io/ez_setup.py>`_


Ahora tendrás un nuevo comando disponible: **easy_install**. Es
considerado por muchos obsoleto, asi que vamos a instalar su reemplazo:
**pip**. Pip te permite desinstalar paquetes, y es activamente mantenido,
no como easy_install.

Para instalar pip, ejecuta el script de Python disponible aquí:
`get-pip.py <https://raw.github.com/pypa/pip/master/contrib/get-pip.py>`_


Pipenv & Ambientes Virtuales
----------------------------

El siguiente paso es instalar Pipenv, así puedes instalar dependencias y gestionar ambientes virtuales.

Un ambiente virtual, es una herramienta para mantener las dependencias requeridas por diferentes proyectos
en lugares separados, creando un ambiente virtual de Python para cada uno. Resuelve el dilema de
"el Projecto X depende de la versión 1.x pero, el Proyecto Y necesita 4.x", y mantiene
tu directorio de site-packages limpio y administrable.

Por ejemplo, puedes trabajar en un proyecto que requiere Django 1.10 mientras también
mantienes un proyecto que requiere Django 1.8.

Entonces, adelante! a la documentación de :ref:`Pipenv & Ambientes Virtuales <virtualenvironments-ref>`

--------------------------------

Esta página es una mezcla de la versión `another guide <http://www.stuartellis.eu/articles/python-development-windows/>`_,
que está disponible bajo la misma licencia.
