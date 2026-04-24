# Services

When creating games in Stride, it is recommended to avoid using the [singleton pattern](https://en.wikipedia.org/wiki/Singleton_pattern) (creating a static object to hold data). However, quite often it's useful to have an easy way of referencing a class.

This is where **services** come in. By registering a class as a service, it becomes easily accessible in the entire project via [`ServiceRegistry`](xref:Stride.Core.IServiceRegistry).

```csharp
public override void Start()
{
    // Note: this example is redundant
    // It's much simpler to access this service with DebugText
    var debugTextService = Services.GetService<DebugTextSystem>();
    debugTextService.Visible = true;
}
```

## What can be a service?

**Every class** can be a service. However, it's **recommended** to inherit the [`IService`](xref:Stride.Core.IService) interface.

```csharp
public class MyService : IService
{
    public static MyService NewInstance(IServiceRegistry services)
    {
        // Create the service instance
        return new();
    }
}
```

## Manually registering a service

You can register a class in services, by using [`Services.AddService`](xref:Stride.Core.IServiceRegistry.AddService*).

```csharp
Services.AddService(new MyService());
```

> [!WARNING]
> It's only possible to register **a single instance**. Trying to register more will result in an error. You can prevent this by first checking if another instance is already registered.
> 
> ```csharp
> if (Services.GetService<MyService>() == null)
>     Services.AddService(new MyService());
> ```

## Getting a service

You can get a service by using [`Services.GetService`](xref:Stride.Core.IServiceRegistry.GetService*).

```csharp
public class Example : StartupScript
{
    public override void Start()
    {
        var service = Services.GetService<MyService>();
        // Do something with the service
    }
}
```

## Auto-creating a service

When registering a service manually you run the risk of another script **trying to access it, before it's registered**.

This can be prevented by using [`Services.GetOrCreate`](xref:Stride.Core.IServiceRegistry.GetOrCreate*) - if the service isn't already registered, a new instance of it will be created.

```csharp
public class Example : StartupScript
{
    public override void Start()
    {
        var service = Services.GetOrCreate<MyService>();
        // Do something with the service
    }
}
```

> [!NOTE]
> The service needs to inherit [`IService`](xref:Stride.Core.IService).
