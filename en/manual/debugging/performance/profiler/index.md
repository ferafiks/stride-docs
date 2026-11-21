# Profiler

Stride internally keeps track how long certain rendering and processing operations take. You can utilize this data in order to diagnose which part of your game is hindering its performance.

> [!NOTE]
> Currently, there is no way of viewing this data using Game Studio. You'll have to use the game profiler script or create your own.

## How it works

There are 3 important terms to keep in mind:

* **Profiler** - collects profiling data from profiles for the entire game
* **Profile** - collects data for a block of code
* **Key** - a unique identifier for the profile

## Viewing profiling data

Currently the easiest way of viewing profiling data is to use the [game profiler script](game-profiler-script.md).

If you wish to display the data on your own (e.g. using the UI system), you can look at the source code of the [`GameProfilingSystem`](xref:Stride.Profiling.GameProfilingSystem) to see how to read data from the [`Profiler`](xref:Stride.Core.Diagnostics.Profiler).

## Proiling pieces of your code

By default, **every system and script is profiled separately** from each other, meaning that **you don't have to setup anything** in order to differentiate scripts from each other.

However if your code is **large enough to warrant further separation,** you can follow [this guide](profiling-your-own-code.md).
