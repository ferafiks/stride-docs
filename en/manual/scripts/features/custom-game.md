# Custom game

In Stride, it's possible to override the [`Game`](xref:Stride.Engine.Game) class to customize how the game is created.

## Reasons for doing this

1. Registering a custom game system
2. Changing the default window properties
3. Changing how the game works

## Creating a custom game class

1. Create a new class that inherits [`Game`](xref:Stride.Engine.Game).
    
    ```csharp
    public class CustomGame : Game
    {
        
    }
    ```

2. Edit the [entry point](#TODO) of all of your project's platforms to use the new class.
    
    ```csharp
    using Stride.Engine;
    
    // Replace Game with CustomGame
    using var game = new CustomGame();
    game.Run();
    ```

Now you can override one of these methods to execute your own code:
