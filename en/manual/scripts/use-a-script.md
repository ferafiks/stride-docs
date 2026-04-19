# Use a script

<span class="badge text-bg-primary">Beginner</span>
<span class="badge text-bg-success">Programmer</span>

To use a script, add it to an entity as a component. You can do this in **Game Studio** or in code. Stride runs scripts when the entity they are attached to loads.

An entity can contain multiple scripts.

A single script can be added to multiple entities, in which case every entity will have a separate instance of this script. This means that **every entity with an attached script won't share it's values with each other**.

## Add a script in Game Studio

To add a script to an entity, select it in the **entity tree** and in the **Property grid** panel, click the **Add component** button.

This will open a popup where you can search for and selec the script you want to add.

TODO: IMAGE

> [!NOTE]
> By default, your own scripts will appear in the dropdown under the **Scripts** category. This can be changed by using the `ComponentCategoryAttribute` attribute.
> 
> ```csharp
> [ComponentCategory("Player")]
> public class PlayerController : StartupScript
> {
>     
> }
> ```

> [!NOTE]
> You can also add a script by **dragging and dropping** it from the **Asset view** panel to an entity in the scene, or the **Property grid**.

## Add a script from code

To add a script to an entity, use the [`Entity.Add`](xref:Stride.Engine.Entity.Add*) method.

```cs
Entity.Add(new myScript());
``` 

## See also

* [Types of script](types-of-script/index.md)
* [Create a script](create-a-script.md)
* [Public properties and fields](public-properties-and-fields.md)
* [Scheduling and priorities](scheduling-and-priorities.md)
* [Events](events.md)
* [Debugging](debugging.md)
* [Preprocessor variables](preprocessor-variables.md)
