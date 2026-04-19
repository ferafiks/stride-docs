# Arrays

<span class="badge text-bg-primary">Beginner</span>
<span class="badge text-bg-success">Programmer</span>

An **array** is a **fixed** collection of elements of the same type.

Arrays exposed to the **Property grid** cannot have their size changed.

TODO: CHECK THESE
```csharp
public string[] array;
public string[] array = [];
```

## Example

```csharp
using Stride.Engine;

public class Example : StartupScript
{
    public string[] unassigedArray;
    public string[] emptyArray = [];
    public string[] array = new string[3];
}
```

TODO: IMAGE

## See also

* [Lists](lists.md)
