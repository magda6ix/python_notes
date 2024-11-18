Python Dictionaries
===================

A dictionary is a collection of values, stored using a key. Keys are unique and case sensitive.

Here's an example dictionary:

.. code-block:: python

    favourites = {
        'color': 'blue',
        'food': 'pizza',
        'animal': 'dog',
        'movie': 'Inception',
        'sport': 'basketball'
    }

Indexing Method
---------------

To get the specific value, we need to use the corresponding key. For example:

.. code-block:: python

    favourite_food = favourites['food']
    print(favourite_food)

    favourite_sport = favourites['sport']
    print(favourite_sport)

The following code will output:

.. code-block::

    pizza
    basketball

The method of accessing the values associated with specific keys is called *indexing*.

get() Method
------------

The *indexing* method is faster, but if the key doesn't exist, the code crashes with a ``KeyError``. 
In that case, it's better to use the ``get()`` method, which will return ``None`` if the key doesn't exist.

Here's an example:

.. code-block:: python

    favourite_drink = favourites.get('drink')
    print(favourite_drink)

This will output:

.. code-block::

    None

