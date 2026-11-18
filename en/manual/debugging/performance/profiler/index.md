# Profiler

Stride internally keeps track how long certain rendering and processing operations take. You can utilize this data in order to diagnose which part of your game is hindering its performance.

> [!NOTE]
> Currently, there is no way of viewing this data using Game Studio. You'll have to use the game profiler script.

## How it works

There are 3 important terms to keep in mind:

* **Profiler** - collects profiling data from profiles for the entire game
* **Profile** - collects data for a block of code
* **Key** - a unique identifier for the profile



## Proiling pieces of your code

By default, **systems and scripts are profiled separately,** making it easier to diagnose issues without having to setup anything.

However, if you want to profile smaller chunks of your code, you will have to do a bit of setup.

1. Define a profiling key. This is a unique identifier that will be associated with your code's profiling data.

    ```csharp
    // Keys can have parents, every script and system has one defined somewhere
    public ProfilingKey GameplayInitialization { get; } = new ProfilingKey(this.ProfilingKey, "GameplayInitialization");
    
    // Alternatively, create a key without a parent
    public ProfilingKey ParentlessOperation { get; } = new ProfilingKey("ParentlessOperation");
    ```

2. Call `Profiler.Begin` in a `using` block to profile your code.

    ```csharp
    using (var profile = Profiler.Begin(GameplayInitialization))
    {
        // Execute my own code here
    }
    ```

## Reading profile data

## Reading profile data in-code

Profiling data is collected by the [`Profiler`](xref:Stride.Core.Diagnostics.Profiler) class.

The game profiler script only takes care of setup and controls — drawing information on the screen is handled by the game profiling system itself.

You can always display the information from the game profiler by yourself to, for example, integrate it with the UI system.
