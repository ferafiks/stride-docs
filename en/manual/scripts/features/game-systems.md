# Game systems

Stride allows you to run code game-wide by creating a **game system**.

**Game systems** run outside of the scene and aren't attached to entities.

An example of this would be the **input system** which keeps handling device input independently from the scene setup.

## Create a game system

```csharp
public class MyGameSystem : MyGameSystem
{
    public MyGameSystem(IServiceRegistry registry) : base(registry)
    {
        
    }
}
```
