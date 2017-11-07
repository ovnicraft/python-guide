.. _install-windows:

Instalando Python 2 en Windows
==============================

.. image:: https://farm5.staticflickr.com/4268/34435688560_4cc2a7bcbb_k_d.jpg

Primero, descarga la `última versión <https://www.python.org/ftp/python/2.7.14/python-2.7.14.msi>`_
de Python 2.7 del sitio oficial. Si deseas estar seguro que estas instalando una versión totalmente
actualizada, clic el link de  Descargas > Windows desde la página oficial
`Python.org web site <http://python.org>`_ .

La versión de Windows se entrega com un paquete MSI. Para instalarlo manualmente, sólo
da doble clic al archivo. El paquete de formato MSI permite a los administradores Windows
automatizar la instalación con sus herramientas estándar.

Por diseño, Python se instala en un directorio con el número de versión embebido,
p.ej. Python 2.7 se instalará en :file:`C:\\Python27\\`, así tu puedes tener
multiples versiones de Python
en el mimso sistema sin conflictos. De seguro, solo un interprete puede ejecutar
por defecto los archivos de tipo Python. Eso tampoco se hace automáticamente
modificar la :envvar:`PATH` variable de ambiente, así tu puedes tener siempre el control sobre
que copia de Python esta corriendo.

Escribir la ruta completa del interprete Python cada vez es tedioso,
así que agrega los directorios para tu versión por defecto de Python a :envvar:`PATH`.
Asumiendo que tu instalación de Python está en :file:`C:\\Python27\\`, agrega esto a tu
:envvar:`PATH`:

.. code-block:: console

    C:\Python27\;C:\Python27\Scripts\

Puedes ahcer rápidamente ejecutando lo siguiente en ``powershell``:

.. code-block:: console

    [Environment]::SetEnvironmentVariable("Path", "$env:Path;C:\Python27\;C:\Python27\Scripts\", "User")

Esta también es una opción durante el proceso de instalación.

El segundo (:file:`Scripts`) directorio recibe archivos de comando cuando
ciertos paquetes están instalados, así que es algo muy útil.
No necesitas instalar o configurar nada más para usar Python.
Dicho eso, voy a recomendar que instales las herramientas y librerías
descritas en la siguiente sección antes de empezar a constriur aplicaciones Python para
su uso en el mundo real. En particular, tu siempre debes instalar Setuptools, ya que
lo hace mucho más fácil para ti usar otras librerías Python de terceros.

Setuptools + Pip
----------------

La librería Python de terceros más crucial de toda es Setuptools, que
extiende las facilidades de empaquetado e instalación entregadas por distutils en
la librería estándar. Una vez que agregas Setuptools a tu sistema Python tu puedes
descargar e instalar cualquier software Python compatible con un simple
comando. También te permite capacidades de instalación en red a tu
propio software Python con muy poco trabajo.

Para obtener la última versión de Setuptools para Windows, corre el script Python
disponible aquí: `ez_setup.py <https://bootstrap.pypa.io/ez_setup.py>`_


Tu ahora tienes un nuevo comando disponible: **easy_install**. Es
considerado por muchos como obsoleto, así que instalaremos su reemplazo:
**pip**. Pip permite desinstalación de paquetes, y esta siendo activamente mantenido,
no como easy_install.

Para instalar pip, ejecuta el script de Python disponible aquí:
`get-pip.py <https://raw.github.com/pypa/pip/master/contrib/get-pip.py>`_


Ambientes Virtuales
-------------------

Un ambiente virtual es una herramienta para mantener lsa dependencias requeridas por diferentes proyectos
en lugares separados, creando ambientes Python virtuales para ellos. Esto resuelve el dilema de
"El Proyecto X depende de la versión 1.x pero, el Proyecto Y necesita 4.x", y mantiene
tu directorio site-packages global limpio y administrable.

Por ejemplo, puedes trabajar en un proyecto que requiere Django 1.10 mientras también
mantener un proyecto que require Django 1.8.

Para empezar a usarlo y ver más imformación: :ref:`Virtual Environments <virtualenvironments-ref>` documentación.


--------------------------------

Esta página es una mezcla de `otra guía <http://www.stuartellis.eu/articles/python-development-windows/>`_,
que esta disponible bajo la misma licencia.
