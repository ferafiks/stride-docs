# Stride events

<span class="badge text-bg-primary">Intermediate</span>
<span class="badge text-bg-success">Programmer</span>

> [!NOTE]
> Stride events are not recommended anymore, see [Best Practice](../best-practice.md)

Stride provides it's own event system for communicating between scripts. This communication works one-way: **brodcasters** to **receivers**.

An example usage would be broadcasting an event when the player dies, so that the end screen could know that it should show up.

Events can also **send additional data**, like information about the game's state.

> [!NOTE]
> Events are handled entirely in scripts. You can't configure them in Game Studio.

## Create and broadcast an event

Broadcasters in the Stride API are of type [EventKey](xref:Stride.Engine.Events.EventKey) or [EventKey&lt;T>](xref:Stride.Engine.Events.EventKey`1). They use the method [Broadcast](xref:Stride.Engine.Events.EventKey#Stride_Engine_Events_EventKey_Broadcast) or [Broadcast(T)](xref:Stride.Engine.Events.EventKey`1#Stride_Engine_Events_EventKey_1_Broadcast__0_) to broadcast events to receivers.

For example, this code creates two "Game Over" events. One with a non-generic and the other with a generic version of EventKey:

```cs
public static class GlobalEvents
{
    public static EventKey GameOverEventKey = new EventKey("Global", "Game Over");
    public static EventKey<string> GameOverWithDataEventKey = new EventKey<string>("Global", "Game Over With Data");

    public static void SendGameOverEvent()
    {
        GameOverEventKey.Broadcast();
        GameOverWithDataEventKey.Broadcast("Player 1");
    }
}
```

## Create a receiver

Receivers in the Stride API are of type [EventReceiver](xref:Stride.Engine.Events.EventReceiver) or [EventReceiver&lt;T>](xref:Stride.Engine.Events.EventReceiver`1).

To receive the "Game Over" events described above, use:

```cs
var gameOverListener = new EventReceiver(GlobalEvents.GameOverEventKey);
var gameIsOver = gameOverListener.TryReceive();

var gameOverListenerWithData = new EventReceiver<string>(GlobalEvents.GameOverWithDataEventKey);
if(gameOverListenerWithData.TryReceive(out string data))
{
	//data == "Player 1"
}

//Or in Async
await gameOverListener.ReceiveAsync();
string asyncData = await gameOverListenerWithData.ReceiveAsync();
//asyncData == "Player 1"
```

## See also

* [Best Practice](../best-practice.md)
* [Types of script](../types-of-script/index.md)
* [Create a script](../create-a-script.md)
