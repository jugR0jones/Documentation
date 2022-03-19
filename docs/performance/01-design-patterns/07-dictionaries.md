---
id: 07-dictionaries
title: Dictionaries
tags:
  - Unity
  - Design
  - Patterns
  - Performance
  - Dictionaries
  - Collections
---

## When To Use Dictionaries

Dictionaries are useful for storing unordered data using a key. Each key is mapped to a value. The retrieval of values using its key is close to O(1) because the underlying implementation is a hash table.

If data needs to be ordered, a standard Dictionary may not be suitable.

In order to access data in a Dictionary, the key needs to be looked up, and the corresponding entry retrieved. This takes a small amount of effort. If you are dealing with a small amount of data, then using a simple array will be quicker.

## Hashing Keys

Each key in the dictionary must be unique, and it cannot be null. A hash is generated from the key. If the hash is not unique, then there can be collisions, collisions result in slower performance.

The key is required to implement the IEqualityComparer&lt;T&gt; generic interface.

### Use Object.GetInstanceID()

Object.GetInstanceID() returns the Unity instance Id for the Unity Object. This is guaranteed to be unique. It is expensive to generate this value, so it should be cached in the script.

This approach can be up to 2x faster than using the object itself as a key.

## Methods To Use

### TryGetValue

TryGetValue() should be used when retrieving data. If the key does not exist, then the function return false and avoids the generation of a exception.

### ContainsKey

ContainsKey() should be used to see if the dictionary contains a Key. This method simply checks if the key is in the Dictionary.