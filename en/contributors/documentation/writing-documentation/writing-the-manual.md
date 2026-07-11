# Writing the manual

The manual is the most important part of the docs. It contains information on how to use Stride.

## Creating a new manual page

Manual pages are located in the `manual/` folder.

1. Create the page in one of the subfolders of `manual/`.

    > [!WARNING]
    > Make sure the name of the file corresponds to the lowercase name of the page with whitespace being replaced with `-`.
    > 
    > ```txt
    > Do:
    > create-an-entity.md
    > 
    > Don't:
    > Create an entity.md
    > ```

2. If you need to create a new sub-folder, make sure to create an `index.md` page for it. You can take a look at how other folders look like.

3. Write the page following the [style-guide](#style-guide).

4. Update table of contents file (`toc.yml` or `toc.md`) in the `manual/` folder to include the new page or folder.

    > [!WARNING]
    > Make sure the name of the page in the `toc` file is the same as the page's title.
    >
    > ```yml
    > # Do:
    > name: Entities
    > href: ...
    > items:
    >   - name: Create an entity
    >     href: ...
    > 
    > # Don't:
    > name: Entities
    > href: ...
    > items:
    >     - name: Create
    >       href: ...
    > ```

## Media

You can observe that existing folders might have a `media` folder. This folder contains images and videos used in the manual pages. When adding new media, make sure that:

* all images are in the `.webp` format
* all videos are in the `.mp4` format

## Style guide

> [!TIP]
> Don't worry about adhering to the style-guide too much. We welcome most contributions and we can always edit your changes after they are merged.

Rule of thumb: try to imitate the style of other files.

> [!NOTE]
> These guidelines are work-in-progress.

1. Pages should be named using sentence case.

    ```md
    Do:
    Create a prefab using Game Studio
    
    Don't
    Create a Prefab Using Game Studio
    ```

1. Start pages with header1, containing their full name as it appears in the table of contents (the `toc` file).

    ```md
    Do:
    # Manual
    
    Don't:
    # Writing manual pages
    ```

1. Use **sentence-case** in headers.

    ```md
    Do:
    ## Add a new entity

    Don't
    ## Add a New Entity
    ```

1. Make sure to respect names of tools and technologies.

    ```md
    Do:
    Game Studio
    
    Don't:
    Game studio, game studio
    ```

1. Paths to menus should be bold and use the `>` character.

    ```md
    Do:
    To save, go to **File > Save**.
    
    Don't:
    To save, to to `File/Save`.
    ```

1. Make all links relative in order to not break other languages.

    ```md
    Do:
    Check out the [manual](../../../manual/index.md).
    
    Don't:
    Check out the [manual](/en/manual/index.md).
    ```

1. If a page contains sub-pages, add a new bullet list containing links to them at the end of the page under `In this section`.

    ```md
    Example:
    ## In this section
    
    * [Create a prefab](create-a-prefab.md)
    * [Edit a prefab](edit-a-prefab.md)
    * [Delete a prefab](delete-a-prefab.md)
    ```

### Additional notes

* **Keep things concise** - most people are quickly glancing over the content to find what they are looking for, so there is no need to make it more difficult for them. However, you still have to provide enough information in case someone would like to learn more.
* **Use bold and italic text** - emphasizing parts of your text make it easier to find things.
* **Utilize alerts to highlight content** - for more information, visit the [docfx documentation](https://dotnet.github.io/docfx/docs/markdown.html#alerts).
