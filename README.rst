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
