IATI Validator Docs
===================

Deployed to https://docs.validator.iatistandard.org/en/latest/

Docs should build automatically upon pull request.
  
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
  
  # Install submodules
  git submodule init
  git submodule update
  
  # Create a venv
  python3 -m venv .ve    
  
  # Enter the venv, needs to be run for every new shell
  source .ve/bin/activate
  
  # Install requirements
  pip install --upgrade pip setuptools
  pip install -r requirements.txt
  
  # Build the docs
  cd docs
  make dirhtml


Built docs are in `docs/_build/dirhtml`.


Viewing the docs:

.. code-block:: bash

  cd _build/dirhtml
  python -m http.server

Then go to http://localhost:8000/ in a browser.
