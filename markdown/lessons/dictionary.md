
---
title: ""
date:
draft: false
order:
lesson: true
descriptor: ""
---

# Dictionary in Python 3
---
Dictionary (Associative Array, map, symbol table) is a data type that stores a collection of (key, value) pairs, such that each possible key appears at most once in the collection.

**Common Operations:**
- Adding a pair
- Removing a pair
- Modify an existing pair
- Lookup of a value associated with a particular key

_Aside:_ This concept is an introduction to concepts similar to: hash table and search trees

## Defining a Dictionary in Python 3
```
Dictionaries also use {} like sets; however, their individual item format is very different.

Each item in a dictionary be a pair of key: value.
```


```python
# Dictionary Example
sammy = {
    'username': 'sammy', 
    'online': True, 
    'followers': 42
}

# There are 3 items: each with their unique addresses and value
# Accessing
print('Sammy dict:', sammy)
print('Username:', sammy['username'])
print('Online Status:', sammy['online'])
print('Follower Count:', sammy['followers'])
```

    Sammy dict: {'username': 'sammy', 'online': True, 'followers': 42}
    Username: sammy
    Online Status: True
    Follower Count: 42


### Dictionary Properties

Each item in a dictionary is a key, value pair.

#### Keys
Keys are unique address for a dictionary value's location

**Key Properties:**
- Must be immutable (strings, numbers, tuples, frozenset)
- Unique; therefore, two same key values cannot exist in a single dictionary
    - NEWEST CREATED ITEM with a duplicate KEY superceeds the previous declaration
 
#### Values
Values of a dictionary within a key can be any data type.

#### Updating a Dictionary
- We can modify existing values by referencing the key
- We can add new values to a dictionary by creating a new key
- We can overwrite a value at an existing key by referencing and recreating the value for it


```python
# Update Example

sammy = {
    'username': 'sammy', 
    'online': True, 
    'followers': 42
}

sammy['followers'] += 10 # We are adding 10 to the value located at key: 'followers'
sammy['verified'] = True # We added a new value at a new key: 'verified'
sammy['username'] = 'SammySammy'

print('Sammy Dict:', sammy)
```

    Sammy Dict: {'username': 'SammySammy', 'online': True, 'followers': 52, 'verified': True}


#### Deletion with Dictionary
- We can delete a key hence deleting the value connected to the key
- We can empty out the entire dictionary
- We can delete the dictionary (uncommonly used)


```python
# Deletion Example

sammy = {
    'username': 'sammy', 
    'online': True, 
    'followers': 42
}

del sammy['followers'] # del is a keyword used to help us to execute a removal
print('followers key deleted:', sammy)

sammy.clear() # {} is considered an empty dict
print('emptying out a dictionary', sammy)
print('--\n\n')

del sammy
print('Deleting sammy, should create an error when referenced again', sammy)

```

    followers key deleted: {'username': 'sammy', 'online': True}
    emptying out a dictionary {}
    --
    
    



    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-11-d3cbe81f2de2> in <module>
         15 
         16 del sammy
    ---> 17 print('Deleting sammy, should create an error when referenced again', sammy)
    

    NameError: name 'sammy' is not defined


#### Membership

We can use the **in** and **not in** operators to check if a key exists in a dictionary


```python
# Membership Example

sammy = {
    'username': 'sammy', 
    'online': True, 
    'followers': 42
}

print('Checking for key username:', 'username' in sammy)
print('Checking if followers is not a key:', 'followers' not in sammy)
```

    Checking for key username: True
    Checking if followers is not a key: False


#### Built-in Functions' Interactions w/ Dictionaries


```python
# Built-in Function Interactions

sammy = {
    'username': 'sammy', 
    'online': True, 
    'followers': 42
}

print('Size of sammy dict:', len(sammy))
print('Largest Key:', max(sammy))
print('Smallest Key:', min(sammy))
print('Dict to string:', str(sammy))
print('Dict to list:', list(sammy))
```

    Size of sammy dict: 3
    Largest Key: username
    Smallest Key: followers
    Dict to string: {'username': 'sammy', 'online': True, 'followers': 42}
    Dict to list: ['username', 'online', 'followers']


#### Duplicate a Dictionary and Copy Keys Only


```python
# Duplicate a Dictionary

sammy = {
    'username': 'sammy', 
    'online': True, 
    'followers': 42
}

sammy_copy1 = sammy.copy()
sammy_copy2 = sammy

sammy['verified'] = True

print('sammy_copy1:', sammy_copy1)
print('sammy_copy2:', sammy_copy2)
print('--')

# Duplicate keys only

tammy = tammy.fromkeys(sammy) # Notice that all key's values are None ... aka empty

print('tammy dict:', tammy)
```

    sammy_copy1: {'username': 'sammy', 'online': True, 'followers': 42}
    sammy_copy2: {'username': 'sammy', 'online': True, 'followers': 42, 'verified': True}
    --
    tammy dict: {'username': None, 'online': None, 'followers': None, 'verified': None}


## Dictionary Methods

To help power this awesome data structure, it has good set of methods for us to use.

_Let A and B be a dictionary_
- A.keys() --> Returns a sequence of keys/addresses in A
- A.values() --> Returns a sequence of item values in A
- A.items() --> Returns a sequence of key,item pairs in A
- A.get(address) --> Returns the item value at address
- A.update(B) --> Extends A with the dictionary of key,value pairs of B



```python
# Dictionary Method Examples

sammy = {
    'username': 'sammy', 
    'online': True, 
    'followers': 42
}

sammy_hidden = {
    'pwd' : 'qwerty',
    'location' : 'Toronto, Ontario'
}

# printing all the keys of a dict
print('Sammy Dict Keys:', sammy.keys()) # notice how it prints

sammy_keys = list(sammy.keys()) # we can listify the .keys() returned
print('List of sammy_keys', sammy_keys) 
print('--')

# printing all the values of a dict
print('Sammy Dict Values:', sammy.values())
print('Sammy Dict Values as a list:', list(sammy.values()))
print('--')

# printing key, value pair of a dict
print('Sammy Dict key, value pairs:', sammy.items())
print('Sammy Dict key, value pairs as a list:', list(sammy.items()))
print('--')

# getting a value from a dict
print('Sammy followers value:', sammy.get('followers'))
print('Same as:', sammy['followers'])
print('--')

# updating / extending a dictionary
sammy.update(sammy_hidden)

print('Sammy extended with its hidden values:', sammy)
```

    Sammy Dict Keys: dict_keys(['username', 'online', 'followers'])
    List of sammy_keys ['username', 'online', 'followers']
    --
    Sammy Dict Values: dict_values(['sammy', True, 42])
    Sammy Dict Values as a list: ['sammy', True, 42]
    --
    Sammy Dict key, value pairs: dict_items([('username', 'sammy'), ('online', True), ('followers', 42)])
    Sammy Dict key, value pairs as a list: [('username', 'sammy'), ('online', True), ('followers', 42)]
    --
    Sammy followers value: 42
    Same as: 42
    --
    Sammy extended with its hidden values: {'username': 'sammy', 'online': True, 'followers': 42, 'pwd': 'qwerty', 'location': 'Toronto, Ontario'}


## Iterating a Dictionary
- We will be taking advantage of three iteration methods
    1. iterating the keys
    2. iterating the values
    3. iterating the key, value pairs by unpacking



```python
# Iteration Example 1: Keys
sammy = {
    'username': 'sammy', 
    'online': True, 
    'followers': 42
}

for k in sammy.keys():
    print('Current key:', k)
print('--\n')

# Iteration Example 2: Values

for v in sammy.values():
    print('Current value:', v)
print('--\n')

# Iteration Example 3: Key, Value Pair

for k, v in sammy.items():
    print('Current Key:', k)
    print('Current Value:', v)
    print()

```

    Current key: username
    Current key: online
    Current key: followers
    --
    
    Current value: sammy
    Current value: True
    Current value: 42
    --
    
    Current Key: username
    Current Value: sammy
    
    Current Key: online
    Current Value: True
    
    Current Key: followers
    Current Value: 42
    


## dict() Constrcutor Dictionary Comprehension

We can turn other data types to dictionaries.

Also similar to lists, tuples, and sets, dictionaries also support comprehension.

**Note:**
- We must specify where the keys are and where the values.


```python
# dict() Example

example_data = [
    ('one', 3),
    ('two', 3),
    ('three', 5)
]

data_dict = dict(example_data)
print('data_dict:', data_dict)
print('--')

# Dictionary Comprehension
# Goal: Take string numerals and assign them with their integer square
# - keys : string numerals
# - values: integer squares

example_data2 = ['1', '2', '3', '4', '5']

data2_dict = {x : int(x)**2 for x in example_data2}

print('data2_dict:', data2_dict)
```

    data_dict: {'one': 3, 'two': 3, 'three': 5}
    --
    data2_dict: {'1': 1, '2': 4, '3': 9, '4': 16, '5': 25}

