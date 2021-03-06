.. _`external plugins`:
.. _`extplugins`:
.. _`using plugins`:

Installing and Using plugins
============================

This section talks about installing and using third party plugins.
For writing your own plugins, please refer to :ref:`writing-plugins`.

Installing a third party plugin can be easily done with ``pip``::

    pip install pytest-NAME
    pip uninstall pytest-NAME

If a plugin is installed, ``pytest`` automatically finds and integrates it,
there is no need to activate it.  We have a :doc:`page listing
all 3rd party plugins and their status against the latest py.test version
<plugins_index/index>` and here is a little annotated list
for some popular plugins:

.. _`django`: https://www.djangoproject.com/

* `pytest-django <http://pypi.python.org/pypi/pytest-django>`_: write tests
  for `django`_ apps, using pytest integration.

* `pytest-twisted <http://pypi.python.org/pypi/pytest-twisted>`_: write tests
  for `twisted <http://twistedmatrix.com>`_ apps, starting a reactor and
  processing deferreds from test functions.

* `pytest-capturelog <http://pypi.python.org/pypi/pytest-capturelog>`_:
  to capture and assert about messages from the logging module

* `pytest-cov <http://pypi.python.org/pypi/pytest-cov>`_:
  coverage reporting, compatible with distributed testing

* `pytest-xdist <http://pypi.python.org/pypi/pytest-xdist>`_:
  to distribute tests to CPUs and remote hosts, to run in boxed
  mode which allows to survive segmentation faults, to run in
  looponfailing mode, automatically re-running failing tests
  on file changes, see also :ref:`xdist`

* `pytest-instafail <http://pypi.python.org/pypi/pytest-instafail>`_:
  to report failures while the test run is happening.

* `pytest-bdd <http://pypi.python.org/pypi/pytest-bdd>`_ and
  `pytest-konira <http://pypi.python.org/pypi/pytest-konira>`_
  to write tests using behaviour-driven testing.

* `pytest-timeout <http://pypi.python.org/pypi/pytest-timeout>`_:
  to timeout tests based on function marks or global definitions.

* `pytest-cache <http://pypi.python.org/pypi/pytest-cache>`_:
  to interactively re-run failing tests and help other plugins to
  store test run information across invocations.

* `pytest-pep8 <http://pypi.python.org/pypi/pytest-pep8>`_:
  a ``--pep8`` option to enable PEP8 compliance checking.

* `oejskit <http://pypi.python.org/pypi/oejskit>`_:
  a plugin to run javascript unittests in life browsers

To see a complete list of all plugins with their latest testing
status against different py.test and Python versions, please visit
`plugincompat <http://plugincompat.herokuapp.com/>`_.

You may also discover more plugins through a `pytest- pypi.python.org search`_.

.. _`available installable plugins`:
.. _`pytest- pypi.python.org search`: http://pypi.python.org/pypi?%3Aaction=search&term=pytest-&submit=search


Requiring/Loading plugins in a test module or conftest file
-----------------------------------------------------------

You can require plugins in a test module or a conftest file like this::

    pytest_plugins = "myapp.testsupport.myplugin",

When the test module or conftest plugin is loaded the specified plugins
will be loaded as well.

    pytest_plugins = "myapp.testsupport.myplugin"

which will import the specified module as a ``pytest`` plugin.

.. _`findpluginname`:

Finding out which plugins are active
------------------------------------

If you want to find out which plugins are active in your
environment you can type::

    py.test --traceconfig

and will get an extended test header which shows activated plugins
and their names. It will also print local plugins aka
:ref:`conftest.py <conftest>` files when they are loaded.

.. _`cmdunregister`:

Deactivating / unregistering a plugin by name
---------------------------------------------

You can prevent plugins from loading or unregister them::

    py.test -p no:NAME

This means that any subsequent try to activate/load the named
plugin will it already existing.  See :ref:`findpluginname` for
how to obtain the name of a plugin.

.. _`builtin plugins`:

Pytest default plugin reference
-------------------------------


You can find the source code for the following plugins
in the `pytest repository <https://github.com/pytest-dev/pytest>`_.

.. autosummary::

    _pytest.assertion
    _pytest.capture
    _pytest.config
    _pytest.doctest
    _pytest.genscript
    _pytest.helpconfig
    _pytest.junitxml
    _pytest.mark
    _pytest.monkeypatch
    _pytest.nose
    _pytest.pastebin
    _pytest.pdb
    _pytest.pytester
    _pytest.python
    _pytest.recwarn
    _pytest.resultlog
    _pytest.runner
    _pytest.main
    _pytest.skipping
    _pytest.terminal
    _pytest.tmpdir
    _pytest.unittest

