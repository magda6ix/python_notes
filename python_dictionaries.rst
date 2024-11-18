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


Iterating over a dictionary
---------------------------

When iterating over a dictionary, you can loop through the keys directly. 
For example:

.. code-block:: python

    favourites = {
        'color': 'blue',
        'food': 'pizza',
        'animal': 'dog',
        'movie': 'Inception',
        'sport': 'basketball'
    }

    for k in favourites:
        print(k)

The output will display the keys:

.. code-block::

    color
    food
    animal
    movie
    sport


To get both the key and the value, you have two options:

1: Using the key to index the value

You can iterate through the keys and access the value using indexing. For example:

.. code-block:: python

    for key in favourites:
        print(key, favourites[key], sep=", ")

This will output:

.. code-block::

    color, blue
    food, pizza
    animal, dog
    movie, Inception
    sport, basketball

**Note**: The ``sep`` parameter specifies the separator between the printed values.

2: Using ``items()`` for Key-Value Pairs

A more efficient way to iterate over both keys and values is to use the ``items()`` method. 
This returns each key-value pair as a tuple. 
In the example below, the tuple is unpacked directly in the loop:

.. code-block:: python

    for key, value in favourites.items():
        print(key, value)

This will output:

.. code-block::

    color blue
    food pizza
    animal dog
    movie Inception
    sport basketball

The ``items()`` method returns an iterator over the dictionary's key-value pairs. 
Each iteration gives you both the key and the corresponding value.
