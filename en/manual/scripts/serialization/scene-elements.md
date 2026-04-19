# Scene elements

<span class="badge text-bg-primary">Beginner</span>
<span class="badge text-bg-success">Programmer</span>

Frequently, scripts needs to reference other components or entities that are in the same scene. In Stride, this is quite simple to do.

To reference other components in the scene, simply create a property or field on your script with that component's type.

```csharp
using Stride.Engine;

public class Example : StartupScript
{
    public CameraComponent Camera { get; set; }
    public Entity OtherEntity { get; set; }
}
```

Unlike typical classes, components are serialized as a reference. In the **Property grid** they will appear as a field where you can assign an instance of them from any entity in the same scene.

TODO: IMAGE

## See also

* [Non-script classes and structs](non-script-classes-and-structs.md)
