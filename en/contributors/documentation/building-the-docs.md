# Building the docs

If you are working on large changes to the documentation or just prefer editing files locally instead of GitHub, this guide will walk you through the steps to install the documentation on your local machine and build it.

## Prerequisites

Before starting, make sure you are familiar with the following prerequisites:

[!INCLUDE [docs-prerequisites](../../includes/docs-prerequisites.md)]

## Installation steps

1. 📥 Clone the Stride docs repository using a git client such as [GitHub Desktop](https://desktop.github.com/download/).

    > [!NOTE]
    > It's recommended to **fork the repository** and then clone your own fork. This will **allow** you to **commit** your changes and **submit pull requests**. 
    >
    > ![The fork button is located next to the repository name.](media/fork-the-repository.webp)

2. Install Docfx with the following command:

    ```bash
    dotent tool install -g docfx
    ```

    ...or if you already have it installed, check that it's version is at least `2.74.1`:

    ```bash
    docfx --version
    ```

    Docfx can be updated using the following command:
    
    ```bash
    dotnet tool update docfx
    ```

3. Clone the main Stride repository (doesn't have to be a fork) in the same folder with the documentation. It's needed in order to build the API docs and get rid of missing page warnings while building.

    TODO: VISUALIZATION

Now you should have everything prepared for running a local build.

## Running the development server

We've created a PowerShell script [BuildDocs.ps1](https://github.com/stride3d/stride-docs/blob/master/BuildDocs.ps1) with a context menu where you can select the language, include the API build, and run the development server.

1. 🚀 Run `run.bat` in the command line to start the script:

    ```powershell
    ./run.bat
    ```

2. 📋 You will see the following self-explanatory menu:
    ```
    Please select an option:

      [en] Build English documentation
      [jp] Build Japanese documentation
      [all] Build documentation in all available languages
      [r] Run local website
      [c] Cancel

    Your choice:
    ```

    Follow the instructions in order to build the docs.

    > [!TIP]
    > We recommend building the API at least once in order to get rid of build warnings.

3. 🖥️ If you select `[r]`, the english documentation site will open automatically in your browser:

    ```txt
    http://localhost:8080/en/index.html
    ```

    For other languages, you will have to change `en` in the URL manually.

4. 😃 Happy writing!

> [!NOTE]
> The documentation needs to be rebuild after every change by running the script again.

Let's [update the content](content.md) now!

### Running the development server on Linux

> [!WARNING]
> Note that the documentation tooling was developed for Windows. You might run into some issues which you will have to solve on your own.

The main hurdle when running the server on Linux is the build script, which was written for **PowerShell** — the command-line shell used by Windows. However did you know that **PowerShell is available on Linux?**

You can look for download instructions on it's official website.

### Running the development server on Linux without PowerShell

You can manually use the `docfx` command to build the english documentation.

1. Make sure to add .NET tools folder to your `PATH` environment variable.

2. Build the docs with the following command:

    ```bash
    docfx build ./en/docfx.json -o ./_site
    ```

3. Run the development server with the following command:

```bash
docfx serve ./_site
```

> [!TIP]
> If you are using a dual-boot setup or have a Virtual Machine setup, you should try building the API on Windows to get rid of build warnings.
>
> You only need to do this one time.
