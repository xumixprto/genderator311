genderator
==========
.. image:: https://img.shields.io/travis/davidmogar/genderator.svg
   :target: https://travis-ci.org/davidmogar/genderator
.. image:: https://img.shields.io/coveralls/davidmogar/genderator.svg
   :target: https://coveralls.io/r/davidmogar/genderator
.. image:: https://img.shields.io/pypi/v/genderator.svg
   :target: https://pypi.python.org/pypi/genderator
.. image:: https://img.shields.io/badge/license-MIT-blue.svg
   :target: https://github.com/davidmogar/genderator/blob/master/LICENSE
.. image:: https://img.shields.io/badge/gitter-join%20chat-brightgreen.svg
   :target: https://gitter.im/davidmogar/genderator?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge

Genderator is a Python library to process Spanish names (from Spain) to guess their
gender.

For this to work, the libray uses the next datasets from `Instituto
Nacional de Estadística <http://www.ine.es>`_:

-  **name\_surname\_ratio**: List of words that could be both, a name or
   a surname, and shows the probability to be a surname.
-  **names\_ine**: List of registered names on Spain, with the
   probability for each one to be a male or a female name.
-  **surnames\_ine**: List of registeres surnames on Spain.

Installation
------------

The easiest way to install the latest version is by using pip to pull it
from `PyPI <https://pypi.python.org/pypi/genderator311>`_:

::

    pip install genderator311

You may also use Git to clone the repository from Github and install it
manually:

::

    git clone https://github.com/xumixprto/genderator311.git
    cd genderator
    python setup.py install

Python 3.11+ are supported.

Usage
-----

The next code shows a sample usage of this library:

.. code:: python

    import genderator

    guesser = genderator.Parser()
    answer = guesser.guess_gender('David Moreno García')
    if answer:
        print(answer)
    else:
        print('Name doesn\'t match')

Output
------

.. code::

    OrderedDict([
        ('names', ['david']),
        ('surnames', ['moreno', 'garcia']),
        ('real_name', 'david'),
        ('gender', 'Male'),
        ('confidence', 1.0)
    ])

Options
-------

Genderator's parser can receive some arguments to control its behaviour. Those arguments are:

- **force_combinations=Boolean**: Force combinations during classification.
- **force_split=Boolean**: Force name split if no surnames are detected.
- **normalize=Boolean**: Enable or disable normalization.
- **normalizer_options=Dictionary**: Normalizer options to be applied.

Normalizer options are a dictionary to control what normalization rules are applied to each name. Possible options are:

- **hyphens**: Boolean option to enable or disable hyphens removal.
- **symbols**: Boolean option to enable or disable symbols removal.
- **whitespaces**: Boolean option to enable or disable extra whitespaces removal.
