***********************
EulerPy
***********************

EulerPy is a command line tool designed to streamline the process of solving
Project Euler problems using Python. The package focuses on two main tasks:
firstly, to create Python "template" files with a docstring containing the
text of a Project Euler problem for ease-of-reference, and secondly, to check
whether a problem has been solved correctly.


============
Installation
============

EulerPy can be installed (and updated) from PyPI using `pip`_:

.. code-block:: bash

    $ pip install --upgrade EulerPy


Conversely, it can be uninstalled using `pip`_ as well.

.. code-block:: bash

    $ pip uninstall EulerPy


=====
Usage
=====

First, you'll want to ``cd`` to the directory where your Project Euler files
are being stored.

.. code-block:: bash

    $ mkdir ~/project-euler
    $ cd ~/project-euler


At this point, you'll probably want to run the ``euler`` command, which will
prompt to create ``001.swift``, a file containing the text to Project Euler problem
#1 as its docstring.

.. code-block:: bash

    $ euler
    No Project Euler files found in the current directory.
    Generate file for problem 1? [Y/n]: Y
    Successfully created "001.swift".

    $ cat 001.swift
    /*
    Project Euler Problem 1
    =======================

    If we list all the natural numbers below 10 that are multiples of 3 or 5,
    we get 3, 5, 6 and 9. The sum of these multiples is 23.

    Find the sum of all the multiples of 3 or 5 below 1000.
    */

At this point, you can open up your editor of choice and code up a solution
to the problem, making sure to ``print()`` the output. Once you feel that
you've solved the problem, run the ``euler`` command again to verify your
solution is correct. If the answer is correct, the solution will be printed
in green and the script will ask to generate the next problem file. If
incorrect, the solution will be printed in red instead. Additionally, the
time elapsed during the solution-checking process will also be printed.

.. code-block:: bash

    $ euler
    Checking "001.swift" against solution: [no output] # (output in red)

    $ echo "println(42)" >> 001.swift
    $ euler
    Checking "001.swift" against solution: 42 # (output in green)
    Generate file for problem 2? [Y/n]: Y
    Successfully created "002.swift".


EulerPy also comes with five options that act as commands. (The ``--help``
option can be used to display a summary of all of the options.)


``--cheat / -c``
----------------

The ``--cheat`` option will print the answer to a problem after prompting
the user to ensure that they want to see it. If no problem argument is given,
it will print the answer to the problem that they are currently working on.

.. code-block:: bash

    $ euler --cheat
    View answer to problem 2? [y/N]: Y
    The answer to problem 2 is <redacted>.

    $ euler --cheat 100
    View answer to problem 100? [y/N]: Y
    The answer to problem 100 is <redacted>.


``--generate / -g``
-------------------

The ``--generate`` option will create a Python file for the given problem
number. If no problem number is given, it will overwrite the most recent
problem with a file containing only the problem docstring (after prompting
the user).

.. code-block:: bash

    $ euler --generate
    Generate file for problem 2? [Y/n]: Y
    "002.swift" already exists. Overwrite? [y/N]:
    Successfully created "002.swift".

    $ euler --generate 5
    Generate file for problem 5? [Y/n]: n
    Aborted!

``euler <problem>`` is equivalent to ``euler --generate <problem>`` if the file
**does not** exist.

.. code-block:: bash

    $ cat 005.swift
    cat: 005.swift: No such file or directory

    $ euler 5
    Generate file for problem 5? [Y/n]: n
    Aborted!


``--preview / -p``
------------------

The ``--preview`` option will print the text of a given problem to the terminal;
if no problem number is given, it will print the next problem instead.

.. code-block:: bash

    $ euler --preview
    Project Euler Problem 3
    The prime factors of 13195 are 5, 7, 13 and 29.

    What is the largest prime factor of the number 600851475143?

    $ euler --preview 5
    Project Euler Problem 5
    2520 is the smallest number that can be divided by each of the numbers
    from 1 to 10 without any remainder.

    What is the smallest number that is evenly divisible by all of the numbers
    from 1 to 20?


``--skip / -s``
---------------

The ``--skip`` option will prompt the user to "skip" to the next problem.

.. code-block:: bash

    $ euler --skip
    Current problem is problem 2.
    Generate file for problem 3? [y/N]: Y
    Successfully created "003.swift".


``--verify / -v``
-----------------

The ``--verify`` option will check whether a given problem file outputs the
correct solution to the problem. If no problem number is given, it will
check the current problem.

.. code-block:: bash

    $ euler --verify
    Checking "003.swift" against solution: [no output] # (output in red)

    $ euler --verify 1
    Checking "001.swift" against solution: <redacted> # (output in green)

``euler <problem>`` is equivalent to ``euler --verify <problem>`` if the file
**does** exist.

.. code-block:: bash

    $ cat 001.swift
    """
    Project Euler Problem 1
    =======================
    ...


    """

    $ euler 1
    Checking "001.swift" against solution: <redacted>


============
Contributing
============

See `CONTRIBUTING.rst`_.


=============
Miscellaneous
=============

The text for the problems in `problems.txt`_ were derived from Kyle Keen's
`Local Euler`_ project, and the solutions in `solutions.txt`_ were derived
from the `projecteuler-solutions wiki`_.

See `this blog post`_ for insight into the development process.

EulerPy uses `click`_ as a dependency for its CLI functionality.


=======
License
=======

EulerPy is licensed under the `MIT License`_.
