# Create a script

<span class="badge text-bg-primary">Beginner</span>
<span class="badge text-bg-success">Programmer</span>

You can create scripts using **Game Studio** or an **IDE** such as Visual Studio.

## Locations of script files

Unlike other assets, **scripts aren't stored in the Assets folder**. Instead, they are stored at the root of a [platform package](#TODO) and it's subfolders.

TODO: VISUALIZATION

In **Game Studio**, you can see the your project's scripts by going to the **Solution explorer** panel and selecting the **Scripts** folder.

TODO: IMAGE

## [Game Studio](#tab/game-studio)

1. In the **Asset view** panel, click **Add asset > Scripts** and select a [script type](types-of-script/index.md).
    
    ![Select script type window](media/create-a-script-script-asset-selection.png)
    
    > [!NOTE]
    > For information about different types of script, see [Types of script](types-of-script/index.md).

2. Specify a class and namespace for the script and click **Create script**.
  
  	![New script](media/script-wizard.png)
  
    > [!NOTE]
    > If you don't know what a namespace is, you can just leave the default value.

3. To use the script, you need to save it. By default, Game Studio prompts you to save the script now.

TODO: CHECK THIS

After you save the script, you can see it in the **Asset View**.

Here's an example of a script's contents.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Stride.Core.Mathematics;
using Stride.Input;
using Stride.Engine;

namespace NameOfGame;

public class ScriptExample : SyncScript
{
    // Declared public member fields and properties will show in the game studio

    public override void Start()
    {
        // Initialization of the script.
    }

    public override void Update()
    {
        // Do stuff every new frame
    }
}
```

## [Visual Studio](#tab/visual-studio)

1. Open Visual Studio.
    
    TODO: IMAGE OF THE OPEN IS VS BUTTON

2. In the **Solution Explorer** panel, locate the C# project (Visual Studio's name for [project packages](#TODO)) in which you want to create your script in.

    In most scenarios, it's going to be the C# project named after your game (the one that doesn't end with `.Windows` or any other platform name).
    
    TODO: IMAGE

3. Right click on the C# project or one of it's directory and select **Add > New Item...**
    
    TODO: IMAGE

4. Select **Class**, fill out the name of your script and click **Add**.

5. Make your class inherit one of the [types of script](types-of-script/index.md) and implement the necessary abstract methods.
    
    For example:
    
    ```cs
    using Stride.Engine;
    
    namespace MyGame;
    
    public class SampleSyncScript : SyncScript
    {			
        public override void Update()
        {
            if (Game.IsRunning)
            {
                // Do something every frame
            }
        }
    }
    ```

TODO: FINISH

6. Save the project and script files.

7. Because you modified the script, Game Studio needs to reload the assembly to show the changes.
      
    ![Confirmation message](media/create-a-script-confirmation-message.png)
    
    Click **Yes**.
    
You can see the script in the **Asset View**.

![New script on Asset View tab](media/create-a-script-new-script-asset-view.png)

## [Manual](#tab/manual)

1. Create a new blank text file in a [platform package](#TODO) with the `.cs` extension
2. Implement the necessary abstract methods. For example:\
    
    ```csharp
    using Stride.Engine;
    
    namespace NameOfGame;
    
    public class ScriptExample : SyncScript
    {
        public override void Start()
        {
            // Initialization of the script.
        }
    
        public override void Update()
        {
            // Do stuff every new frame
        }
    }
    ```

---

## See also

* [Best Practice](best-practice.md)
* [Types of script](types-of-script/index.md)
* [Use a script](use-a-script.md)
* [Public properties and fields](public-properties-and-fields.md)
* [Scheduling and priorities](scheduling-and-priorities.md)
* [Events](events.md)
* [Debugging](debugging.md)
* [Preprocessor variables](preprocessor-variables.md)
