# Unit tests

Unit tests are commonly used in software development to ensure that all code works correctly and doesn't break in the future.

A tests is a simple method that runs a given method using certain parameters and checks if its output matches the value that was checked to be correct.

## Practical example

The method `MyClass.Add` returns the sum of two `int` values. We know that the sum of 2 and 2 is equal to 4, so we create the following test:

```csharp
[Fact]
public void TestAdd()
{
    // Run the method using 2 and 2
    var result = MyClass.Add(2, 2);

    // Check if the result is equal to 4
    Assert.IsTrue(result == 4);
}
```

Now if the `MyClass.Add` method suddenly starts returning 5 for these values, an exception will be thrown and the test will fail. This lets you quickly check if your changes cause any breakage before you encounter a single bug.

## Using tests in your project

Stride doesn't provide a built-in testing solution for your games. Instead, you can use any external test framework available on NuGet, just as you would with any .NET project.

For the rest of this page, we will be using [xUnit](https://xunit.net/?tabs=cs), which is the same test framework that Stride uses for engine code.

## Setup

### [Command line](#tab/command-line)

1. Install the xunit templates.

    ```bash
    dotnet new install xunit.v3.templates
    ```

2. Create a new tests project package in your project.

    ```bash
    dotnet new xunit3 --name NameOfGame.Tests
    ```

3. Add the newly created project package to the solution.

    ```bash
    dotnet sln add NameOfGame.Tests
    ```

4. Add a reference to your game's main project package in the test project package.

    ```bash
    dotnet add NameOfGame.Tests reference NameOfGame.Game
    ```

---

## Creating tests

Tests are created by adding the `[Fact]` attribute to methods.

```csharp
public class MyClassTests
{
    [Fact]
    public void MyMethodTest()
    {
        // Run the test here
    }
}
```

To verify the output, use methods from the [`Assert`](https://api.xunit.net/v3/3.0.1/Xunit.Assert.html) class.

```csharp
[Fact]
public void MyMethodTest()
{
    var result = MyClass.MyMethod("MyString", 1);
    
    // This method will throw an exception if the result is
    // not equal to 71, failing the test
    Assert.IsTrue(result == 71);
}
```

> [!TIP]
> You can use [pattern matching](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/patterns/pattern-matching) for testing methods that return complex structs or classes.
>
> ```csharp
> Assert.IsTrue(result is MyCustomStruct { Property1 = 3, Property4 = false });
> ```

### Running the game for tests

Testing outputs of specific methods is great for simpler tests. If you want to check code that relies on runtime features (e.g. physics), you will have to run the game inside the test.

```csharp
private static void RunGameTest(Func<Game, Scene, Task> asyncFunction)
{
    using var game = new Game();
    
    // Fixed time step to reduce framerate discrepancies
    game.IsFixedTimeStep = true;
    game.IsDrawDesynchronized = false;
    game.TargetElapsedTime = TimeSpan.FromTicks(10000000 / 60); // 60hz, 60fps
    
    game.Script.AddTask(async () =>
    {
        await asyncFunction(game, game.SceneSystem.SceneInstance.RootScene);
        game.Exit();
    });
    game.Run();
}
```

This method will launch a new instance of the game, execute code from the asyncFunction and then exit.

Here's an example of how to use this:

```csharp
[Fact]
public void ExampleTest()
{
    RunGameTest(async (game, scene) =>
    {
        var entity = new Entity("Player")
        {
            new RemoveEntityAfterTimeScript()
            {
                TimeToWait = TimeSpan.FromSeconds(3)
            }
        };
        entity.Scene = scene;

        await Task.Delay(TimeSpan.FromSeconds(3.1));
        Assert.IsTrue(entity.Scene == null);
    });
}
```

## Running tests

### [Command line](#tab/command-line)

You can run all tests by running the following command:

```bash
dotnet test
```

If any tests fail, you'll be able to quickly see them and diagnose the issue that's preventing them from passing.

---
