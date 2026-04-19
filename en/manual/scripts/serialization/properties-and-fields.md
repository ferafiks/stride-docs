# Properties and fields

<span class="badge text-bg-primary">Beginner</span>
<span class="badge text-bg-success">Programmer</span>

In C#, a **field** is something that can hold a value of some type, which can be changed by code.

```csharp
public string myField = "Some value";
```

A **property** on the other hand is similar to a field, but provides more control over how values are read and assigned.

```csharp
// The most basic form of a property
public string MyProperty { get; set; } = "Some value";

// A more complex property
public string MyOtherProperty
{
    get => field.Trim();
    private set
    {
        // Only change the field value, if the new value
        // isn't made out of only spaces
        if (!string.IsNullOrWhiteSpace(value))
            field = value;
    }
}
```

Properties and fields can be exposed in the **Property grid** panel for modifying in that specific script instance.

**For example:** You can have multiple instances of a `Player` script in a scene and assign a different value for the `Name` property for each of them.

TODO: VISUALIZATION

## How to expose fields

Fields marked as `public` will be automatically exposed. Others might require the [`DataMember`](xref:Stride.Core.DataMemberAttribute) attribute, or a different access modifier.

| Access modifier | Exposed |
| :-- | :-- |
| `public` | 🟩 Automatically exposed. |
| `internal` | 🟨 Not exposed, unless an [`DataMember`](xref:Stride.Core.DataMemberAttribute) is added. |
| `private` | 🟥 Cannot be exposed. |

```csharp
// Fields that will be exposed
public string publicField;
[DataMember] internal string internalField;

// Fields that won't be exposed
internal string internalField;
private string privateField;
```

## How to expose properties

Properties can have **different access modifiers** for their **getters** and **setters**, but the general rule is that <u>the getter needs to be exposed</u>.

Aside from that, the rules are the same as the ones for fields.

| Access modifier | Exposed |
| :-- | :-- |
| `public` | 🟩 Automatically exposed. |
| `internal` | 🟨 Not exposed, unless an [`DataMember`](xref:Stride.Core.DataMemberAttribute) is added. |
| `private` | 🟥 Cannot be exposed. |

```csharp
// Properties that will be exposed
public string PublicProperty { get; set; }
[DataMember] internal string InternalProperty { get; set; }
[DataMember] public string PublicProperty { get; internal set; }

// Properties that won't be exposed
private string PrivateProperty { get; set; }
internal string InternalProperty { get; set; }
public string PublicProperty { get; private set; }
public string PublicProperty { get; internal set; }
```

## Read only

Fields marked as `readonly` and properties that only have a getter can be exposed to the **Property grid**, but can't be modified.

```csharp
// Read only members
public string ReadOnlyProperty => "Some value";
public readonly string readOnlyField = "Some value";
```

> [!NOTE]
> Although read only properties cannot be modified, the object assigned to them can be. This means that for example: when [another class](non-script-classes-and-structs.md) is assigned to the read only field, that classes properties and fields can be modified.
> 
> TODO: Test this
> TODO: Image
> TODO: Code
> 
> For more information on exposing classes and structs to the property field, check out [this page](non-script-classes-and-structs.md).

## See also

* [Non-script classes and structs](non-script-classes-and-structs.md)
