Eligiendo un Interprete
=======================

.. _which-python:

El estado de Python (2 vs 3)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cuando vamos a elegir un interprete de Python, una pregunta esta siempre presente:
"Debo elegir Python 2 o Python 3"? La respuesta no esta tan obvia como uno
podría pensar.


La esencia básica de las cosas es la siguiente:

1. Python 2.7 ha sido un estandar por un *largo* tiempo.
2. Python 3 introduce mayores cambios al lenguaje, que muchos desarrolladores no están felices con eso.
3. Python 2.7 recibirá actualizaciones de seguridad necesarias hasta 2020 [#pep373_eol]_.
4. Python 3 está continuamente evolucionando, como Python 2 lo hizo en años pasados.

Así, puedes ver porque no es una desición fácil.


Recommendaciones
~~~~~~~~~~~~~~~~

Voy a ser franco:


**Usa Python 3 si...**

- No te importa.
- Te encanta Python 3.
- Eres indiferente a 2 vs 3.
- No sabes cual utilizar
- Te gusta el cambio

**Usa Python 2 si...**

- Te encanta Python 2 y estas triste por el futuro de Python 3.
- Los requisitos de estabilidad de tu software podrían mejorarse con un lenguaje y ejecución que nunca cambia.
- El software que dependes los usará.


Asi que.... 3?
~~~~~~~~~

Si estas eligiendo un interprete de Python para usar, y no eres obstinado, entonces
te recomiendo usar la versión más nueva de Python 3.x, ya que cada versión trae nuevos y
mejorados módulos de la biblioteca estandar, correcciones de seguridad y errores. Progreso es progreso.

Dado tal, sólo use Python 2 si tienes una fuerte razón para hacerlo, tal como una
librería exclusiva de Python 2 que no tiene una adecuada alternativa en Python 3,
o si (como yo) ama absolutmente y está inspirado en Python 2.

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

En conjunto con Mono, PythonNet permite de forma nativa instalaciones de Python
en sistemas operativos no-Windows, tales como OS X y
Linux, para operar con .NET framework.  Puede correr
con IronPython sin conflicto.

PythonNet soporta desde Python 2.3 hasta Python 2.7. [#pythonnet_ver]_

.. [#pypy_ver] http://pypy.org/compat.html

.. [#jython_ver] https://hg.python.org/jython/file/412a8f9445f7/NEWS

.. [#iron_ver] http://ironpython.codeplex.com/releases/view/81726

.. [#pythonnet_ver] http://pythonnet.github.io/readme.html

.. [#pep373_eol] https://www.python.org/dev/peps/pep-0373/#id2
