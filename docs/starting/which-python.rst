Eligiendo un Interprete Python (3 vs. 2)
========================================

.. image:: https://farm5.staticflickr.com/4265/34484834733_5b80f65ab1_k_d.jpg

.. _which-python:

El estado de Python (3 & 2)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cuando vamos a elegir un interprete de Python, una pregunta esta siempre presente:
"Debo elegir Python 2 o Python 3"? La respuesta no esta tan obvia como uno
podría pensar.


La esencia básica de las cosas es la siguiente:

1. La mayoría de aplicación en producción de hoy usan Python 2.7.
2. Python 3 está listo para despliegues en producción de aplicaciones de hoy en día.
3. Python 2.7 sólo recibirá actualizaciones de seguridad necesarias hasta el 2020 [#pep373_eol]_.
4. La marca "Python" encapsúla ambos Python 3 y Python 2.

Recommendaciones
~~~~~~~~~~~~~~~~


.. note:: El uso de **Python 3** es *altamente* preferido sobre Python 2. Considera actualizar tus aplicaciones e infraestructura si *aún* te encuentras usando Python 2 en producción ahora. Si estás usando Python 3, felicitaciones — ya eres una persona con excelente gusto.
  —*Kenneth Reitz*

Voy a ser franco:

- Usa Python 3 para nuevas aplicaciones Python.
- Si estás aprendiendo Python por primera vez, familiarizarte con Python 2.7 será muy
  útil, pero no más útil que aprender Python 3.
- Aprende ambos. Ambos son "Python".
- Software que ya esta creado a menudo depende de Python 2.7.
- Si estas escribiendo una nueva librería open source de Python, lo mejor es escribirla para ambos Python 2 y 3
  simultáneamente. Sólo soportar Python 3 para una nueva librería que deseas que sea ampliamente adoptada es una
  desición política y alejará a muchos usuarios. Esto no es un problema — lentamente, durante los próximos tres años, estos casos serán menos.

Asi que.... 3?
~~~~~~~~~~~~~~

Si esta eligiendo un interprete de Python para usar, Te
recomiendo usar el Python 3.x más nuevo, ya que cada versión trae nuevos y
mejorados módulos de la librería estandar, seguridad y correcciones de errores.

Dado esto, sólo usa Python 2 si tienes una fuerte razón para, tal como
código base pre existente, una librería exclusiva de Python 2, simplicidad/familiaridad,
o, de seguro, tu absolutamente lo amas y estás inspirado por Python 2. No hay daño en eso.

Revisa `Puedo usar Python 3? <https://caniusepython3.com/>`_ para ver si el software
del que dependes bloqueará tu adopción de Python 3.

`Otras lecturas <http://wiki.python.org/moin/Python2orPython3>`_

Es posible `escribir código que funcionará en Python 2.6, 2.7, y Python 3
<https://docs.python.org/3/howto/pyporting.html>`_. Estos
rangos de trivial a difícil dependerá del tipo de software que estás
escribiendo; si eres principiante hay cosas más importantes por las que preocuparse.

Implementaciones
~~~~~~~~~~~~~~~~

Cuando la gente habla de *Python* ellos a menudo no sólo se refieren al lenguaje sino
a la implementación CPython. *Python* es actualmente una especificación para un lenguaje
que puede ser implementado en diferentes maneras.

CPython
-------

`CPython <http://www.python.org>`_ es la referencia de la implmementación de Python,
escrita en C. Este compila código Python a bytecode intermedio que luego es interpretado
por la máquina virtual. CPython provee el nivel más alto de
compatibilidad con paquetes Python y módulos de extensión C.

Si estas escribiendo código abierto Python y deseas alcanzar una amplia audiencia posible,
apuntar a CPython es lo mejor. Para usar paquetes que recaen en extensiones C
para funcionar, CPython es tu única implementación como opción.

Todas las versiones de Python son implementadas en C porque CPython es la
implementación de referencia.

PyPy
----

`PyPy <http://pypy.org/>`_ es un interprete de Python implementado en un subgrupo restringido
de tipo estático del lenguaje de Python llamado RPython. El interprete cuenta
con un compilador *just-in-time* y soporta múltiples *back-ends* (C, CLI, JVM).

PyPy apunta a la máxima compatibilidad con la referencia de implementación CPython
mientras mejora su rendimiento.

Si estas buscando incrementar el rendimiento de tu código Python, vale la pena darle
una oportunidad a PyPy. En un conjunto de puntos de referencia, es actualmente `más de 5
veces más rápido que CPython <http://speed.pypy.org/>`_.

PyPy soporta Python 2.7. PyPy3 [#pypy_ver]_, liberado como beta, apunta a Python 3.

Jython
------

`Jython <http://www.jython.org/>`_ es una implementación de Python que compila
código Python a Java bytecode que es ejecutado por la JVM (Java Virtual Machine).
Adicionalmente, esta habilitado para importar y usar cualquier clase de Java como
un módulo de Python.

Si necesitas interactuar con código Java o tienes otras razones para escribir
código Python para la JVM, Jython es tu mejor opción.

Jython actualmente soporta hasta Python 2.7. [#jython_ver]_

IronPython
----------

`IronPython <http://ironpython.net/>`_  es una implementación de Python para el
framework .NET. Puede ser usada por ambas librerías Python y .NET framework,
y también puede exponer código Pytohn para otros lenguajes en el framwork .NET.

`Python Tools para Visual Studio <http://ironpython.net/tools/>`_ integra
IronPython directamente en el ambiente de desarrollo Visual Studio,convirtiéndolo
en una elección ideal para desarrolladores Windows.

IronPython soporta Python 2.7. [#iron_ver]_

PythonNet
---------

`Python for .NET <http://pythonnet.github.io/>`_ es un paquete que
provee una integración sin puntos rotos de una instalación de Python
con una instalación de .NET Common Language Runtime (CLR).  Es un enfoque
inverso al tomado por IronPython (ver antes), lo que es es más
complementario que competitivo.

Junto con Mono, pythonnet activa soporte nativo de instalaciones de Python
en sistemas operativos no-Windows, tales como OS X y
Linux, para operar con el framework .NET.  Puede ser ejecutado junto con
IronPython sin conflicto.

Pythonnet soporta desde Python 2.6 hasta Python 3.5. [#pythonnet_ver1]_ [#pythonnet_ver2]_

.. [#pypy_ver] http://pypy.org/compat.html

.. [#jython_ver] https://hg.python.org/jython/file/412a8f9445f7/NEWS

.. [#iron_ver] http://ironpython.codeplex.com/releases/view/81726

.. [#pythonnet_ver1] https://travis-ci.org/pythonnet/pythonnet

.. [#pythonnet_ver2] https://ci.appveyor.com/project/TonyRoberts/pythonnet-480xs

.. [#pep373_eol] https://www.python.org/dev/peps/pep-0373/#id2
