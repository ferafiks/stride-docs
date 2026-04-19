# Dictionaries

<span class="badge text-bg-primary">Beginner</span>
<span class="badge text-bg-success">Programmer</span>

Dictionaries are a collection of keys points to their values.

TODO: CHECK THESE
```csharp
// Dictionaries in general
public Dictionary<string, int> example;
public Dictionary<string, int> example = new();
public Dictionary<string, int> numberFromNames =
[
    ["one"] = 1,
    ["two"] = 2,
    ["three"] = 3,
];
```

```csharp
public Dictionary<string, int> numberFromNames =
[
    ["one"] = 1,
    ["two"] = 2,
    ["three"] = 3,
];

int number = numberFromNames["two"];
// The value of number is equal to 2
```

## See also

* [Arrays](arrays.md)
* [Lists](lists.md)
