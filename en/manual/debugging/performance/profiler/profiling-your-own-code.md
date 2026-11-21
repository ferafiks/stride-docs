# Profiling your own code

By default, every system and script is profiled individually, meaning that **you don't need to do any additional setup** to differentiate poorly optimized code.

TODO: TAKE SCREENSHOT

However, if you feel that script profiling should be **further split into smaller chunks,** this guide is for you.

## Manually profiling code

First, you have to define a **profiling key**. This is a unique identifier that will be associated with your code's profiling data.

```csharp
// Keys can have parents, every script and system has one defined somewhere
public ProfilingKey GameplayInitialization { get; } = new ProfilingKey(ProfilingKey, "GameplayInitialization");

// Alternatively, create a key without a parent
public static readonly ProfilingKey ParentlessOperation { get; } = new ProfilingKey("ParentlessOperation");
```

Then you can start profiling your code by calling `Profiler.Begin` in a `using` block.

```csharp
using (var profile = Profiler.Begin(GameplayInitialization))
{
    // Execute my own code here
}
```

You profile should now start showing up with the rest of the profiling data.

## Sending mark events

Mark events allow you to **highlight critical moments** in the code you are profiling. Think of it as [logging](../../code/logging.md) for profile data.

You can send a mark event by calling [`Mark`](xref:Stride.Core.Diagnostics.ProfilingState.Mark) or [`Mark(string)`](xref:Stride.Core.Diagnostics.ProfilingState.Mark(System.String,System.Nullable{Stride.Core.Diagnostics.ProfilingCustomValue},System.Nullable{Stride.Core.Diagnostics.ProfilingCustomValue},System.Nullable{Stride.Core.Diagnostics.ProfilingCustomValue},System.Nullable{Stride.Core.Diagnostics.ProfilingCustomValue})) if you wish to provide an optional message.

```csharp
using (var profile = Profiler.Begin(MyKey))
{
    if (someCondition)
    {
        profile.Mark("Started the performance-heavy method");
        PerformanceHeavyMethod();
    }
}
```

Mark events can also pass **up to 4 additional values** that can either be a `double`, `float`, `int` or `long`.

```csharp
int iterationAmount = 10;

...

profile.Mark("Executing method for set amount of iterations", iterationAmount);
for (int i = 0; i < iterationAmount; i++)
    PerformanceHeavyMethod();
```

> [!TIP]
> Additional parameters in mark events are useful for providing values that could have an impact on performance.
