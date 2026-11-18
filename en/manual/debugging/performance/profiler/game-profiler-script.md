# Game profiler script

Stride includes a built-in script template that allows you to view and control profiling data at runtime.

TODO: IMAGE

## Setup the game profiler script

1. In the Asset view, go to the **Code** folder, click the **➕ Add asset** button and select **Game profiler**.

    TODO: IMAGE

2. Optionally change the script's name and press **Create script**.

    TODO: IMAGE

3. Create a new entity in your scene and add your newly created script to it.

    TODO: IMAGE

Now when you run the game, you should see profiling information appear on your screen:

TODO: IMAGE

## Script runtime controls

You can change the settings of the game profiler script at runtime using keyboard shortcuts.

| Action | Control |
| :-- | :-- |
| <kbd>Left Ctrl</kbd> + <kbd>Left Shift</kbd> + <kbd>P</kbd> | Enable/disable the profiler |
| <kbd>F1</kbd> | Toggle between CPU, GPU, and FPS-only results. |
| <kbd>F2</kbd> | Toggle between sorting by profile key and time. |
| <kbd>-</kbd> / <kbd>+</kbd> | Slow down / speed up the refresh time. |
| <kbd>F3</kbd> / <kbd>F4</kbd> | Page back / page forward. |
| Number keys | Jump to a page. |

## Understanding profiling data

Depending on the mode, the top row displays different information.

**FPS**

![](media/profiling-fps.webp)

| Displaying | The kind of information the profiler displays (FPS only, CPU, or GPU). |
| :-- | :-- |
| Frame | The current frame. |
| Update | The average time (ms) taken to update the game since the profiler last refreshed. |
| Draw | The average time (ms) taken to render the frame since the profiler last refreshed. |
| FPS | The average number of frames rendered per second. |

**CPU**

![](media/profiling-cpu.webp)

| Total | The amount of memory currently used. |
| :-- | :-- |
| Peak | The peak memory use since the game started. |
| Allocations | The amount of memory allocated or freed since the profiler last refreshed. |
| Gen0, Gen1, Gen2 | The number of garbage collections per each generation of object (`Gen0` is the most recent generation). |

**GPU**

![](media/profiling-gpu.webp)

| Device | The graphics device (manufacturer's description). |
| :-- | :-- |
| Platform | The currently used backend (Direct3D or Vulkan). |
| Profile | The feature level for your game, set in **Game Settings > Rendering** (see [Game settings](../../../game-studio/game-settings.md)). |
| Resolution | The game resolution. |
| Drawn triangles | The number of triangles drawn per frame. |
| Draw calls | The number of draw calls per frame. |
| Buffer memory | The amount of memory allocated to buffers . |
| Texture memory | The amount of memory allocated to textures. |

In the **GPU** and **CPU** modes, the profiler displays information about the parts of the code being profiled, including active scripts.

![](media/profiler-columns.webp)

> [!NOTE]
> Each value describes the events per frame since the last profiler refresh.

| Column | Description |
| :-- | :-- |
| TOTAL | The total time taken to execute the code in one frame. |
| AVG/CALL | Average time taken to execute a single call of the code. |
| MIN/CALL | The shortest amount of time taken to execute a single call of the code. |
| MAX/CALL | The longest amount of time taken to execute a single call of the code. |
| CALLS | The number of times the code was executed in one frame. |
| MARKS | The number of times per frame marked code is executed. This column is only displayed if marked code is executed. |
| PROFILE KEY / EXTRA INFO | The part of the code (such as a function or script) being profiled. This column also displays additional information, such as the number of entities affected. |
