IATI Validator Docs
===================

Deployed to https://docs.validator.iatistandard.org/en/latest/

Docs build automatically upon pull request.
  
Features of the docs
--------------------

Uses https://github.com/OpenDataServices/sphinx-base, but without markdown or json support.
See the `examples <https://sphinx-base.readthedocs.io/en/latest/examples/>`__ and `kitchen sink <https://sphinx-base.readthedocs.io/en/latest/kitchen-sink/>`__ sections for some directives you can use.

Extra features:
  
* Wrapping text in tables, to avoid having horizontal scrollbars
* Extra directives you can use, thanks to our extensions, see the docs of those for more information:
  - https://sphinxcontrib-opendataservices.readthedocs.io/en/latest/

Build the docs locally
----------------------
  
Assuming a unix based system:

.. code-block:: bash
  
  # Make sure you have python3 venv, e.g. for Ubuntu
  # If you're not sure, try creating a venv, and see if it errors
  sudo apt-get install python3-venv
  
  # Create a venv
  python3 -m venv .ve    
  
  # Enter the venv, needs to be run for every new shell
  source .ve/bin/activate
  
  # Install requirements
  pip install -r requirements.txt
  
  # Build the docs
  cd docs
  make dirhtml


Built docs are in ``docs/_build/dirhtml``


Viewing the docs:

.. code-block:: bash

  cd _build/dirhtml
  python -m http.server

Then go to http://localhost:8000/ in a browser.


Translations
------------

The translation workflow is:

* Extract strings into English-language .pot files
* Send the files for translation
* When translated .po files are received, check them in to the repo and rebuild the docs

On ReadTheDocs, there is a separate project for each language, each based on this repo. The projects for non-English languages are configured, on the English project, as translations. 

Extract strings
^^^^^^^^^^^^^^^

Install requirements as above.

Extract English source strings:

.. code-block:: bash

   cd docs
   make gettext
   # .pot files are in _build/locale




Send files for translation
^^^^^^^^^^^^^^^^^^^^^^^^^^

Via email

Check translated files into the repo
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Put the files in ``docs/locale/fr/LC_MESSAGES/`` (substituting fr for the appropriate language code as required)


Build
^^^^^

Build a translated docs site locally:

.. code-block:: bash

   cd docs
   make -e SPHINXOPTS="-D language='fr'" dirhtml


(substituting fr for the appropriate language code as required)

Built docs are in ``docs/_build/dirhtml``.

Build remotely:

All projects will build on a change to the repo, so a PR to the repo will trigger all languages to build. 