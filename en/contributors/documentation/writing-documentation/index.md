# Writing documentation

Each page of the documentation is a markdown file (`.md`), which you can edit in an editor of your choosing (either a markdown editor or an IDE).

> [!TIP]
> You can edit the documentation in **Visual Studio** by opening the `Stride.Docs.sln` file.

## Small updates

A small update can be identified as one of the following:

* Updating content on an existing page (manual, tutorial, release notes, etc).
* Adding a single manual page, tutorial or any new content.
* Fixing a typo.

These updates do not require you to create an issue and can be created directly through editing pages on **GitHub**.

## Major updates

A major update can be idenditied as one of the following:

* Change to the structure (e.g. adding a new section to the manual).
* Updating Docfx version.
* Modifying layouts.
* Revampiung design elements.

When creating a major issues you are required to:

* [Create an issue](https://github.com/stride3d/stride-docs/issues), so that others can comment on your changes and provide feedback.
* Test your changes locally by [building the website](../installation.md).
* (Recommended) Provide screenshots of your changes.
* (Recommended) Setup a page for deomsntration using [GitHub Pages](../deployment-azure.md#deployment-to-github-pages).
