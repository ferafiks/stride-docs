# Debug text

<span class="badge text-bg-primary">Beginner</span>
<span class="badge text-bg-success">Programmer</span>

Stride allows you to easily display text on the screen using [DebugText](xref:Stride.Engine.ScriptComponent.DebugText). This is useful when you want to check a rapidly changing value or display a message when a problem occurs.

## Printing text

To print text on the screen, use the [`DebugText.Print`](xref:Stride.Profiling.DebugTextSystem.Print*) method in the `Update` function of your script.

```csharp
public override void Update()
{
    DebugText.Print("My debug text", new Int(50, 50));
}
```

The method requires you to specify a message and the screen pixel coordinates at which to display the text.

TODO: IMAGE

## Toggling visibility

Debug text is automatically hidden depending on your build configuration:
* **Debug:** 🟩 debug text is visible by default.
* **Release:** 🟥 debug text is hidden by default.

To manually toggle debug text, change the value of [`DebugText.Visible`](xref:Stride.Games.GameSystemBase.Visible).

```csharp
DebugText.Visible = false;
```

## Color

You can customize the text color by providing a `color` parameter in the [`DebugText.Print`](xref:Stride.Profiling.DebugTextSystem.Print*) method.

```csharp
// The following will print red debug text
DebugText.Print("Something went wrong!", new Int2(50, 50), color: new Color4(1f, 0f, 0f));
```

## Time

[`DebugText.Print`](xref:Stride.Profiling.DebugTextSystem.Print*) has an optional time parameter, which specifies for how long a message should be displayed. This is useful if you want to print something without needing to use the update loop.

```csharp
public override void Update()
{
    if (Input.IsKeyPressed(Keys.Space))
    {
        DebugText.Print("You have pressed space.", new Int2(50, 50), timeOnScreen: TimeSpan.FromSeconds(4.0));
    }
}
```

## Example script

The following script checks that the texture `MyTexture` is loaded. If it isn't loaded, the game displays a message "MyTexture not loaded".

```cs
using Stride.Core.Mathematics;
using Stride.Engine;
using Stride.Graphics;

namespace MyGame;

public class Example : SyncScript
{
    private Texture myTexture;

    public override void Start()
    {
        // Initialization of the script.
        myTexture = Content.Load<Texture>("MyTexture");
    }

    public override void Update()
    {
        if (myTexture == null)
            DebugText.Print("MyTexture not loaded", new Int2(x: 50, y: 50));
    }
}
```
