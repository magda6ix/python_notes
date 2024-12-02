Python Dictionaries
===================

A `Python dictionary`_ is a collection of values, stored using a key. Keys are unique and case sensitive.

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

Changing values in the dictionary
---------------------------------

To change the value associated with a key in a dictionary, assign a new value to the key, 
as shown below:

.. code-block:: python

    favourites = {
        'color': 'blue',
        'food': 'pizza',
        'animal': 'dog',
        'movie': 'Inception',
        'sport': 'basketball'
    }

    # change the favourite color
    favourites['color'] = 'green'

    # change the favourite movie
    favourites['movie'] = 'Blade Runner'


After performing these changes, the dictinary looks like this:

.. code-block:: python

    print(favourites)

Code output:

.. code-block::

    {
    'color': 'green',
    'food': 'pizza',
    'animal': 'dog',
    'movie': 'Blade Runner',
    'sport': 'basketball'
    }


Removing items from a dictionary:
---------------------------------

Removing items from a Python dictionary, can be done in several ways:

1. Using ``del``
2. Using the ``pop()`` method 
3. Using the ``popitem()`` method

Let's see how these options work on our dictionary:

.. code-block:: python

    favourites = {
        'color': 'blue',
        'food': 'pizza',
        'animal': 'dog',
        'movie': 'Inception',
        'sport': 'basketball'
    }

``del`` removes an item from the dictionary by specifying its key.

For example:

.. code-block:: python

    # remove 'food'
    del favourites['food']

    print(favourites)

Output:

.. code-block::

    {
        'color': 'blue',
        'animal': 'dog',
        'movie': 'Inception',
        'sport': 'basketball'
    }

The ``pop()`` method removes an item by key and returns this value.

For example:

.. code-block:: python

    # remove 'animal' using 'pop()'
    rem = favourites.pop('animal')

    print(favourites)
    print("Removed:", rem)

The code outputs:

.. code-block:: 

    {
        'color': 'blue',
        'movie': 'Inception',
        'sport': 'basketball'
    }
    removed: dog

The ``pop()`` method returns the removed value, so it can be stored 
and/or used later in the code, if needed.

The ``popitem()`` method removes and returns the last key - value pair in the dictionary.

For example:

.. code-block:: python

    # remove the last item using 'popitem()'
    last = favourites.popitem()

    print(favourites)
    print("removed:", last)

Output:

.. code-block::

    {
        'color': 'blue',
        'movie': 'Inception'
    }
    removed: ('sport', 'basketball')


Let's practice - Toolbox System
-------------------------------

In the example below, we simulate a simple toolbox system where the user can select different tasks to be performed. 
The program checks if the necessary tools are available in the toolbox to complete the task.

First, let's analyze the two dictionaries, below:

.. code-block:: python

    toolbox = {
        "scissors": 1,
        "tape": 1, 
        "glue": 2,
        "paper": 5,
        "marker": 3,
        "string": 10,
        "cardboard": 3,
        "stapler": 1,
        "rubber band": 10,
    }

    actions = {
        "Make a greeting card": [
            "scissors",
            "tape",
            "paper",
            "marker",
            "glitter"
        ],
        "Wrap a gift": [
            "scissors",
            "tape",
            "paper",
            "string",
        ],
        "Create a paper airplane": [
            "paper",
            "scissors",
        ],
        "Build a cardboard box": [
            "cardboard",
            "scissors",
            "tape",
        ],
        "Organize papers": [
            "stapler",
            "rubber band",
        ],
        "Tie a bundle of papers": [
            "string",
            "rubber band",
        ],
    }

We have a toolbox with several tools (scissors, tape, etc.), and a set of actions 
that require specific tools. 

Now, we need to make these dictionaries useful and create some code.


.. code-block:: python

    display_d = {}
    for index, key in enumerate(actions):
        display_d[str(index + 1)] = key

    while True:
        print("Please choose an action:")
        print("----------------------------")
        for key, value in display_d.items():
            print(f"{key} - {value}")

        choice = input(": ")

        if choice == "0":
            break
        elif choice in display_d:
            selected_action = display_d[choice]
            print(f"You have selected: {selected_action}")
            print("Checking availability...")

            required_tools = actions[selected_action]
            for tool in required_tools:
                if tool in toolbox:
                    print(f"\t {tool} - OK")
                else:
                    print(f"\t You don't have the necessary tool - {tool}")


Let's run the code and then analyze it step by step.
First, we get the following output:

.. code-block::

    Please choose an action:
    ----------------------------
    1 - Make a greeting card
    2 - Wrap a gift
    3 - Create a paper airplane
    4 - Build a cardboard box
    5 - Organize papers
    6 - Tie a bundle of papers
    : 

The program is waiting for our input. For example, if we want to build a cardboard box, 
we need to type in ``4``. The program will check the availability of the materials needed to perform this action.

.. code-block::

    Please choose an action:
    ----------------------------
    1 - Make a greeting card
    2 - Wrap a gift
    3 - Create a paper airplane
    4 - Build a cardboard box
    5 - Organize papers
    6 - Tie a bundle of papers
    : 4
    You have selected: Build a cardboard box
    Checking availability...
        cardboard - OK
        scissors - OK
        tape - OK

The code output states that the toolbox dictionary contains all the necessary elements
to build a cartboard box.

Because the code is wrapped into the ``while True`` loop, it will continue running 
indefinitely. You can try different options available in the list of actions.

Let's see what happens, if we don't have all the nexessary tools, by choosing ``1`` from the list:

.. code-block::

    You have selected: Make a greeting card
    Checking availability...
        scissors - OK
        tape - OK
        paper - OK
        marker - OK
        You don't have the necessary tool - glitter


The code output correctly displays the information that we don't have glitter. 


.. _`Python dictionary`: https://docs.python.org/3/tutorial/datastructures.html#dictionaries