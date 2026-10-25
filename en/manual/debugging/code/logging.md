# Logging

Many games and applications use **logs** to display messages describing what is happening and what went wrong.

TODO: IMAGE OF AN EXAMPLE

Stride uses its own logging system, which can also be utilized by your own code.

## How to log

To log a message, you can use one of the methods available in the [`Log`](xref:Stride.Engine.ScriptComponent.Log) property.

There are multiple types of log messages:

| Type | Description |
| :-- | :-- |
| [Debug](xref:Stride.Core.Diagnostics.Logger.Debug*) | Used for debugging during development that might not be easily comprehensible (e.g. random variable or a message that a method was called). |
| [Verbose](xref:Stride.Core.Diagnostics.Logger.Verbose*) | Contains an excessive amount of information, only useful when diagnosing complicated problems in a released game. |
| [Info](xref:Stride.Core.Diagnostics.Logger.Info*) | Notifies that something usual has happened (e.g. the player has been spawned). |
| [Warning](xref:Stride.Core.Diagnostics.Logger.Warning*) | Warns that something went wrong, but the game can still mostly worked (e.g. failed to play a sound effect). |
| [Error](xref:Stride.Core.Diagnostics.Logger.Error*) | Notifies that something went wrong and the game might not work properly (e.g. failed to load the next level). |
| [Fatal](xref:Stride.Core.Diagnostics.Logger.Fatal*) | Notifies that a critical error has occurred and the game needs to shut down. |

Here's an example:

```csharp
Log.Info($"Loaded level {CurrentLevelScene.Name}.");
```

## Viewing logs

Logs aren't visible to a user, unless the game is run from the terminal.

TODO: IMAGE

On Windows, if the game is running in the debug configuration, the terminal is automatically opened when a message is logged.

> [!NOTE]
> Certain types of logs are disabled by default.

## Activate or deactivate log types

In Stride, it's possible to deactivate logs by type. By default, log visibility looks like this:

| | Debug | Verbose | Info | Warning | Error | Fatal |
| :-- | :-: | :-: | :-: | :-: | :-: | :-: |
| Activated (is visible) | No | No | No | Yes | Yes | Yes |

You can specify which logs are activated using [`ActivateLog(fromLevel, toLevel)`](xref:Stride.Core.Diagnostics.Logger.ActivateLog(Stride.Core.Diagnostics.LogMessageType,Stride.Core.Diagnostics.LogMessageType,System.Boolean)) or toggle them individually with [`ActivateLog(type, enabledFlag)`](xref:Stride.Core.Diagnostics.Logger.ActivateLog(Stride.Core.Diagnostics.LogMessageType,System.Boolean)).

```csharp
// Activate all logs except verbose
Log.ActivateLog(LogMessageType.Debug, LogMessageType.Fatal);
Log.ActivateLog(LogMessageType.Verbose, false);
```

> [!NOTE]
> * [`ActivateLog(fromLevel, toLevel)`](xref:Stride.Core.Diagnostics.Logger.ActivateLog(Stride.Core.Diagnostics.LogMessageType,Stride.Core.Diagnostics.LogMessageType,System.Boolean)) - enables or disables log types in the specified range **while setting the opposite value to the ones outside of it**.
> * [`ActivateLog(type, enabledFlag)`](xref:Stride.Core.Diagnostics.Logger.ActivateLog(Stride.Core.Diagnostics.LogMessageType,System.Boolean)) - enables or disables a specific log types. **Does not affect other types**.
