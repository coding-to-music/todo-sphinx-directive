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

    sudo apt-get install python3-venv
    python -m venv ver3.7

    python -m site

    connorstom@penguin:~/aprojects/todo-sphinx-directive$ python -m site
    sys.path = [
        '/home/connorstom/aprojects/todo-sphinx-directive',
        '/usr/lib/python37.zip',
        '/usr/lib/python3.7',
        '/usr/lib/python3.7/lib-dynload',
        '/home/connorstom/.local/lib/python3.7/site-packages',
        '/usr/local/lib/python3.7/dist-packages',
        '/usr/lib/python3/dist-packages',
    ]
    USER_BASE: '/home/connorstom/.local' (exists)
    USER_SITE: '/home/connorstom/.local/lib/python3.7/site-packages' (exists)
    ENABLE_USER_SITE: True

Here are some commands and the response ::

    connorstom@penguin:~/.local/bin$ echo $PATH
    /home/connorstom/.local/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
    connorstom@penguin:~/.local/bin$ /usr/bin/python --version
    Python 2.7.16
    connorstom@penguin:~/.local/bin$ whereis python
    python: /usr/bin/python3.7 /usr/bin/python3.7m /usr/bin/python3.7-config /usr/bin/python3.7m-config /usr/bin/python2.7 /usr/bin/python /usr/bin/python2.7-config /usr/lib/python3.7 /usr/lib/python2.7 /etc/python3.7 /etc/python2.7 /etc/python /usr/local/bin/python3.9 /usr/local/bin/python3.9-config /usr/local/lib/python3.7 /usr/local/lib/python3.9 /usr/local/lib/python2.7 /usr/include/python3.7m /usr/include/python3.7 /usr/include/python2.7 /usr/share/python /usr/share/man/man1/python.1.gz
    connorstom@penguin:~/.local/bin$ which python
    /usr/bin/python
    connorstom@penguin:~/.local/bin$ type -a python
    python is aliased to `python3'
    python is /usr/bin/python
    connorstom@penguin:~/.local/bin$ python -m site
    sys.path = [
        '/home/connorstom/.local/bin',
        '/usr/lib/python37.zip',
        '/usr/lib/python3.7',
        '/usr/lib/python3.7/lib-dynload',
        '/home/connorstom/.local/lib/python3.7/site-packages',
        '/usr/local/lib/python3.7/dist-packages',
        '/usr/lib/python3/dist-packages',
    ]
    USER_BASE: '/home/connorstom/.local' (exists)
    USER_SITE: '/home/connorstom/.local/lib/python3.7/site-packages' (exists)
    ENABLE_USER_SITE: True

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
