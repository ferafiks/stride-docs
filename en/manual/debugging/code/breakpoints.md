# Breakpoints

Dotnet allows you to pause the execution of your game when it reaches a certain place in code using breakpoints.

TODO: IMAGE

In this pause state, you can inspect values of variables.

TODO: IMAGE

> [!NOTE]
> Not all IDEs (code editors) support setting breakpoints. This page includes instructions for a select few.

## Create a breakpoint

### [Visual Studio](#tab/visual-studio)

1. Find the line in your code before which you want to pause execution.

2. Hover your mouse next to it's line number to reveal a dot icon.

    TODO: IMAGE

3. Press the dot icon, which will make it red.

    TODO: IMAGE

> [!NOTE]
> The breakpoint will only be triggered if you **launch the game through Visual Studio**.

### [Visual Studio Code](#tab/visual-studio-code)

1. Find the line in your code before which you want to pause execution.

2. Hover your mouse next to it's line number to reveal a translucent dot icon.

    TODO: IMAGE

3. Press the dot icon, which will make it opaque.

    TODO: IMAGE

> [!NOTE]
> The breakpoint will only be triggered if you **launch the game through Visual Studio Code**.

---

## Add a conditional breakpoint

Conditional breakpoints let you specify a condition under which the execution will be paused (e.g. if a certain variable is set to a specific value).

### [Visual Studio](#tab/visual-studio)

You can create a conditional breakpoint similarly to a normal breakpoint, by right clicking on the breakpoint icon and selecting **TODO: CHECK WHAT IT SAYS**.

TODO: IMAGE

Then, you can specify a condition.

TODO: IMAGE

### [Visual Studio Code](#tab/visual-studio-code)

You can create a conditional breakpoint similarly to a normal breakpoint, by right clicking on the breakpoint icon and selecting **Add Conditional Breakpoint...**.

TODO: IMAGE

Then, you can specify a condition.

TODO: IMAGE

---

## Remove a breakpoint

### [Visual Studio](#tab/visual-studio)

You can remove individual breakpoints by clicking on them.

TODO: IMAGE

To remove all breakpoints, select from the top menu **TODO: CHECK**.

### [Visual Studio Code](#tab/visual-studio-code)

You can remove individual breakpoints by clicking on them.

TODO: IMAGE

To remove all breakpoints, select from the top menu **Run > Remove All Breakpoints**.

---
