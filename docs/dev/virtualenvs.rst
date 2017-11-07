.. _virtualenvironments-ref:

Pipenv & Ambientes Virtuales
============================

.. image:: https://farm5.staticflickr.com/4290/35294660055_42c02b2316_k_d.jpg

Este tutorial te llevará a traves de la instalación y uso de paquetes Python.

Te va a mostrar como instalar y usar las herramientas necesarias y hacerte fuertes
recomendaciones en las mejores prácticas. Ten en cuenta que Python es usado para grandes
y diferentes propósitos, y precisamente cómo deseas manejar tus dependencias
puede cambiar basado en como decides publicar tu software. La guía
presentada está directamente aplicada al desarrollo y despliegue de
servicios de red (incluyendo aplicaciones web), pero también esta muy adecuada para
administrar ambientes de prueba y desarrollo para cualquier tipo de proyecto.

.. Note:: Esta guía está escrita para Python 3, aunque, estas instrucciones
    deberían trabajar bien en Python 2.7—si aún lo estas usando, por alguna razón.


Asegúrate que tienes Python & pip
---------------------------------

Antes de ir más lejos, asegurate que tienes Python y que está disponible
desde tu línea de comandos. Puedes revisar esto sólo ejecutando:

.. code-block:: bash

    $ python --version

Debes obtener algún resultado como ``3.6.2``. Si no tienes Python, por favor
instala la última versión desde `python.org`_ o refierete a la sección
`Instalando Python`_ de esta guía.

.. Note:: Si eres novato y tienes un error como este:

    .. code-block:: python

        >>> python
        Traceback (most recent call last):
          File "<stdin>", line 1, in <module>
        NameError: name 'python' is not defined

    Es porque este comando esta tratando de ser ejecutado en una *shell* (también llamada
    *terminal* o *consola*). Mira la sección Para Novatos
    `getting started tutorial`_ para una introducción de cómo usar tu shell
    del sistema operativo e interactuar con Python.

Además, necesitarás asegurarte que tienes :ref:`pip` disponible. Puedes
revisar esto ejecutando:

.. code-block:: bash

    $ pip --version

Si instalaste Python desde la fuente, con un instalador desde `python.org`_, o
vía `Homebrew`_ ya deberías tener pip. Si estas usando Linux e instalaste
usando tu manejador de paquetes del sistema operativo, talves tengas que `instalar pip <https://pip.pypa.io/en/stable/installing/>`_ por separado.

.. _getting started tutorial: https://opentechschool.github.io/python-beginners/en/getting_started.html#what-is-python-exactly
.. _python.org: https://python.org
.. _Homebrew: https://brew.sh
.. _Installing Python: http://docs.python-guide.org/en/latest/starting/installation/


Instalando Pipenv
-----------------

:ref:`Pipenv` es un manejador de dependencias para proyectos Python. Si estas familiarizado
con Node.js' `npm`_ o `bundler`_ de Ruby, es similiar en el espíritu de estas
herramientas. Mientras :ref:`pip` puede instalar paquetes Python, Pipenv es recomendado como
una herramienta de lato nivel que simplifica la gestión de dependencias como casos de uso
común.

Usa ``pip`` para instalar Pipenv:

.. code-block:: python

    $ pip install --user pipenv


.. Note:: This does a `user installation`_ to prevent breaking any system-wide
    packages. If ``pipenv`` isn't available in your shell after installation,
    you'll need to add the `user base`_'s binary directory to your ``PATH``.

    On Linux and macOS you can find the user base binary directory by running
    ``python -m site --user-base`` and adding ``bin`` to the end. For example,
    this will typically print ``~/.local`` (with ``~`` expanded to the
    absolute path to your home directory) so you'll need to add
    ``~/.local/bin`` to your ``PATH``. You can set your ``PATH`` permanently by
    `modifying ~/.profile`_.

    On Windows you can find the user base binary directory by running
    ``py -m site --user-site`` and replacing ``site-packages`` with
    ``Scripts``. For example, this could return
    ``C:\Users\Username\AppData\Roaming\Python36\site-packages`` so you would
    need to set your ``PATH`` to include
    ``C:\Users\Username\AppData\Roaming\Python36\Scripts``. You can set your
    user ``PATH`` permanently in the `Control Panel`_. You may need to log
    out for the ``PATH`` changes to take effect.

.. _npm: https://www.npmjs.com/
.. _bundler: http://bundler.io/
.. _user base: https://docs.python.org/3/library/site.html#site.USER_BASE
.. _user installation: https://pip.pypa.io/en/stable/user_guide/#user-installs
.. _modifying ~/.profile: https://stackoverflow.com/a/14638025
.. _Control Panel: https://msdn.microsoft.com/en-us/library/windows/desktop/bb776899(v=vs.85).aspx

Instalando Paquetes para tu Proyecto
------------------------------------

Pipenv manages dependencies on a per-project basis. To install packages,
change into your project's directory (or just an empty directory for this
tutorial) and run:

.. code-block:: bash

    $ cd myproject
    $ pipenv install requests

Pipenv will install the excellent `Requests`_ library and create a ``Pipfile``
for you in your project's directory. The :ref:`Pipfile` is used to track which
dependencies your project needs in case you need to re-install them, such as
when you share your project with others. You should get output similar to this
(although the exact paths shown will vary):

.. code-block:: text

    Creating a Pipfile for this project...
    Creating a virtualenv for this project...
    Using base prefix '/usr/local/Cellar/python3/3.6.2/Frameworks/Python.framework/Versions/3.6'
    New python executable in ~/.local/share/virtualenvs/tmp-agwWamBd/bin/python3.6
    Also creating executable in ~/.local/share/virtualenvs/tmp-agwWamBd/bin/python
    Installing setuptools, pip, wheel...done.

    Virtualenv location: ~/.local/share/virtualenvs/tmp-agwWamBd
    Installing requests...
    Collecting requests
      Using cached requests-2.18.4-py2.py3-none-any.whl
    Collecting idna<2.7,>=2.5 (from requests)
      Using cached idna-2.6-py2.py3-none-any.whl
    Collecting urllib3<1.23,>=1.21.1 (from requests)
      Using cached urllib3-1.22-py2.py3-none-any.whl
    Collecting chardet<3.1.0,>=3.0.2 (from requests)
      Using cached chardet-3.0.4-py2.py3-none-any.whl
    Collecting certifi>=2017.4.17 (from requests)
      Using cached certifi-2017.7.27.1-py2.py3-none-any.whl
    Installing collected packages: idna, urllib3, chardet, certifi, requests
    Successfully installed certifi-2017.7.27.1 chardet-3.0.4 idna-2.6 requests-2.18.4 urllib3-1.22

    Adding requests to Pipfile's [packages]...
    P.S. You have excellent taste! ✨ 🍰 ✨

.. _Requests: https://python-requests.org


Usando Paquetes Instalados
--------------------------

Now that Requests is installed you can create a simple ``main.py`` file to
use it:

.. code-block:: python

    import requests

    response = requests.get('https://httpbin.org/ip')

    print('Your IP is {0}'.format(response.json()['origin']))

Then you can run this script using ``pipenv run``:

.. code-block:: bash

    $ pipenv run python main.py

You should get output similar to this:

.. code-block:: text

    Your IP is 8.8.8.8

Using ``$ pipenv run`` ensures that your installed packages are available to
your script. It's also possible to spawn a new shell that ensures all commands
have access to your installed packages with ``$ pipenv shell``.


Siguientes Pasos
----------------

Congratulations, you now know how to install and use Python packages! ✨ 🍰 ✨



Un nivel más bajo: virtualenv
=============================

`virtualenv <http://pypi.python.org/pypi/virtualenv>`_ is a tool to create
isolated Python environments. virtualenv creates a folder which contains all the
necessary executables to use the packages that a Python project would need.

It can be used standalone, in place of Pipenv.

Install virtualenv via pip:

.. code-block:: console

  $ pip install virtualenv

Test your installation

.. code-block:: console

   $ virtualenv --version


Uso Básico
~~~~~~~~~~

1. Create a virtual environment for a project:

.. code-block:: console

   $ cd my_project_folder
   $ virtualenv my_project

``virtualenv my_project`` will create a folder in the current directory which will
contain the Python executable files, and a copy of the ``pip`` library which you
can use to install other packages. The name of the virtual environment (in this
case, it was ``my_project``) can be anything; omitting the name will place the files
in the current directory instead.

This creates a copy of Python in whichever directory you ran the command in,
placing it in a folder named :file:`my_project`.

You can also use the Python interpreter of your choice (like
``python2.7``).

.. code-block:: console

   $ virtualenv -p /usr/bin/python2.7 my_project

or change the interpreter globally with an env variable in ``~/.bashrc``:

.. code-block:: console

   $ export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python2.7

2. To begin using the virtual environment, it needs to be activated:

.. code-block:: console

   $ source my_project/bin/activate

The name of the current virtual environment will now appear on the left of
the prompt (e.g. ``(my_project)Your-Computer:your_project UserName$)`` to let you know
that it's active. From now on, any package that you install using pip will be
placed in the ``my_project`` folder, isolated from the global Python installation.

Install packages as usual, for example:

.. code-block:: console

    $ pip install requests

3. If you are done working in the virtual environment for the moment, you can
   deactivate it:

.. code-block:: console

   $ deactivate

This puts you back to the system's default Python interpreter with all its
installed libraries.

To delete a virtual environment, just delete its folder. (In this case,
it would be ``rm -rf my_project``.)

After a while, though, you might end up with a lot of virtual environments
littered across your system, and its possible you'll forget their names or
where they were placed.

Otras Notas
~~~~~~~~~~~

Running ``virtualenv`` with the option ``--no-site-packages`` will not
include the packages that are installed globally. This can be useful
for keeping the package list clean in case it needs to be accessed later.
[This is the default behavior for ``virtualenv`` 1.7 and later.]

In order to keep your environment consistent, it's a good idea to "freeze"
the current state of the environment packages. To do this, run

.. code-block:: console

    $ pip freeze > requirements.txt

This will create a :file:`requirements.txt` file, which contains a simple
list of all the packages in the current environment, and their respective
versions. You can see the list of installed packages without the requirements
format using "pip list". Later it will be easier for a different developer
(or you, if you need to re-create the environment) to install the same packages
using the same versions:

.. code-block:: console

    $ pip install -r requirements.txt

This can help ensure consistency across installations, across deployments,
and across developers.

Lastly, remember to exclude the virtual environment folder from source
control by adding it to the ignore list.

.. _virtualenvwrapper-ref:

virtualenvwrapper
-----------------

`virtualenvwrapper <https://virtualenvwrapper.readthedocs.io/en/latest/index.html>`_
provides a set of commands which makes working with virtual environments much
more pleasant. It also places all your virtual environments in one place.

To install (make sure **virtualenv** is already installed):

.. code-block:: console

  $ pip install virtualenvwrapper
  $ export WORKON_HOME=~/Envs
  $ source /usr/local/bin/virtualenvwrapper.sh

(`Full virtualenvwrapper install instructions <https://virtualenvwrapper.readthedocs.io/en/latest/install.html>`_.)

For Windows, you can use the `virtualenvwrapper-win <https://github.com/davidmarble/virtualenvwrapper-win/>`_.

To install (make sure **virtualenv** is already installed):

.. code-block:: console

  $ pip install virtualenvwrapper-win

In Windows, the default path for WORKON_HOME is %USERPROFILE%\Envs

Uso Básico
~~~~~~~~~~

1. Create a virtual environment:

.. code-block:: console

   $ mkvirtualenv my_project

This creates the :file:`my_project` folder inside :file:`~/Envs`.

2. Work on a virtual environment:

.. code-block:: console

   $ workon my_project

Alternatively, you can make a project, which creates the virtual environment,
and also a project directory inside ``$PROJECT_HOME``, which is ``cd`` -ed into
when you ``workon myproject``.

.. code-block:: console

   $ mkproject myproject

**virtualenvwrapper** provides tab-completion on environment names. It really
helps when you have a lot of environments and have trouble remembering their
names.

``workon`` also deactivates whatever environment you are currently in, so you
can quickly switch between environments.

3. Deactivating is still the same:

.. code-block:: console

   $ deactivate

4. To delete:

.. code-block:: console

   $ rmvirtualenv venv

Otros comandos útiles
~~~~~~~~~~~~~~~~~~~~~

``lsvirtualenv``
  List all of the environments.

``cdvirtualenv``
  Navigate into the directory of the currently activated virtual environment,
  so you can browse its :file:`site-packages`, for example.

``cdsitepackages``
  Like the above, but directly into :file:`site-packages` directory.

``lssitepackages``
  Shows contents of :file:`site-packages` directory.

`Full list of virtualenvwrapper commands <https://virtualenvwrapper.readthedocs.io/en/latest/command_ref.html>`_.

virtualenv-burrito
------------------

With `virtualenv-burrito <https://github.com/brainsik/virtualenv-burrito>`_, you
can have a working virtualenv + virtualenvwrapper environment in a single command.

autoenv
-------
When you ``cd`` into a directory containing a :file:`.env`, `autoenv <https://github.com/kennethreitz/autoenv>`_
automagically activates the environment.

Install it on Mac OS X using ``brew``:

.. code-block:: console

   $ brew install autoenv

And on Linux:

.. code-block:: console

   $ git clone git://github.com/kennethreitz/autoenv.git ~/.autoenv
   $ echo 'source ~/.autoenv/activate.sh' >> ~/.bashrc
