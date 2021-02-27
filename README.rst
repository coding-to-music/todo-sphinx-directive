Using a python directive (simple python program) to do or say anything, such as ToDo lists
===============================================================================================

Following these instructions:
https://www.sphinx-doc.org/en/master/development/tutorials/todo.html

Steps:

Here is what needs to be done:: 

    mkdir todo-sphinx-directive
    cd todo-sphinx-directive
    sphinx-quickstart
    mkdir source/_ext
    Create an _ext folder in source

    apt-get install python3-venv
    sudo apt-get install python3-venv
    python -m venv ver3.7

Create a new Python file in the _ext folder called todo.py

modify conf.py :: 

    import os
    import sys

    sys.path.append(os.path.abspath("./_ext"))

    extensions = ['helloworld']

You can now use the extension in a file. For example:

Some intro text here...

use the following directive anywhere and it will get expanded by the python program

.. code-block:: 
:directive:

    `::todolist::`

Some more text here...
The sample above would generate:

Some intro text here...::

    <list of todo's go here>

Some more text here...

edit the file index.rst, which uses the directive, and view the generated index.html:: 

    make html
    cd build/html
    python3 -m http.server
    http://0.0.0.0:8000/

Unlimited Scale and Free Web Hosting with GitHub Pages and Cloudflare
https://www.toptal.com/github/unlimited-scale-web-hosting-github-pages-cloudflare

https://medium.com/@shobhitrathi10/github-io-getting-started-e0d643dac850


the format of your github.io page will be 

username.github.io/RepositoryName


This bug report shows how to publish on github.io 
https://github.com/sphinx-doc/sphinx/issues/3382

suhailvs commented on Jul 30, 2018
update of @wxianxin ::

    Create an empty .nojekyll file in the root folder to turn off Jekyll.
    Create an index.html file in the root folder with contents:
    <meta http-equiv="refresh" content="0; url=./_build/html/index.html" />
    Run make html then add, commit and push the repo.
    In the GitHub Pages box in the project Settings page, choose to use master branch.
    Visit https://<username>.github.io/<repo>

The page should be viewable at https://coding-to-music.github.io/todo-sphinx-directive/
