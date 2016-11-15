Eligiendo un Interprete
=======================

.. _which-python:

El estado de Python (3 & 2)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cuando vamos a elegir un interprete de Python, una pregunta esta siempre presente:
"Debo elegir Python 2 o Python 3"? La respuesta no esta tan obvia como uno
podría pensar.


La esencia básica de las cosas es la siguiente:

1. Most production applications today use Python 2.7.
2. Python 3 is ready for the production deployment of applications today.
3. Python 2.7 will only receive necessary security updates until 2020 [#pep373_eol]_.
4. The brand name "Python" encapsulates both Python 3 and Python 2.

Recommendaciones
~~~~~~~~~~~~~~~~

Voy a ser franco:

- Use Python 3 for new Python applications.
- If you're learning Python for the first time, familiarizing yourself with Python 2.7 will be very
  useful, but not more useful than learning Python 3.
- Learn both. They are both "Python".
- Software that is already built often depends on Python 2.7.
- If you are writing a new open source Python library, it's best to write it for both Python 2 and 3
  simultaneously. Only supporting Python 3 for a new library you want to be widely adopted is a
  political statement and will alienate many of your users. This is not a problem — slowly, over the next three years, this will become less the case.

Asi que.... 3?
~~~~~~~~~

If you're choosing a Python interpreter to use, I
recommend you use the newest Python 3.x, since every version brings new and
improved standard library modules, security and bug fixes.

Given such, only use Python 2 if you have a strong reason to, such as a
pre-existing code-base, a Python 2 exclusive library, simplicity/familiarity,
or, of course, you absolutely love and are inspired by Python 2. No harm in that.

Revisa `Puedo usar Python 3? <https://caniusepython3.com/>`_ para ver si el software
del que dependes bloqueará tu adopción de Python 3.

`Otras lecturas <http://wiki.python.org/moin/Python2orPython3>`_

Es posible It is possible  `escribir código que funcionará en Python 2.6, 2.7, y Python 3
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
