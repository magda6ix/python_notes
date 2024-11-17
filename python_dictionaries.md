# Python Dictionaries

A dictionary is a collection of values, that are stored using a key.
Keys are unique and case sensitive.

Here's an example dictionary:

```python
favourites = {
    'color': 'blue',
    'food': 'pizza',
    'animal': 'dog',
    'movie': 'Inception',
    'sport': 'basketball'
}
```

### Indexing Method

To get the specific value, we need to use a corresponding key, for example:

```python
favourite_food = favourites['food']
print(favourite_food)

favourite_sport = favourites['sport']
print(favourite_sport)
```

The following code will output:

```
pizza
basketball
```

The method of accessing the values associated with specific keys is called `indexing`. 

### get() Method

The *indexing* method is faster, but if the key doesn't exist, the code crashes with a `KeyError`. In that case, it's better to use `get()` (if the key doesn't exist, it returns `None`). 

Here's an example:

