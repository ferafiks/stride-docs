# Non-script classes and structs

<span class="badge text-bg-primary">Beginner</span>
<span class="badge text-bg-success">Programmer</span>

In Stride, it is possible to serialize a standard class or struct by using the [`[DataContract]`](xref:Stride.Core.DataContractAttribute) attribute.

```csharp
// This class is not a script
[DataContract]
public class MyClass
{
    public string MyProperty { get; set; }
    
    [DataMember]
    internal int MyNumber { get; set; }
}
```
