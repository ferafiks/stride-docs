# Translating the docs

## How it works

All languages are placed in separate folders (`en`, `jp`). The `en` folder contains the base documentation files, while others only contain the translated files.

When building other languages, files from their folders are used to override the ones in `en`.

## Adding a new language

Currently we aren't accepting new languages, as we are trying to rewrite most of the documentation to bring it up-to-date.

## Translating existing pages

1. Copy a page from `en` to a relative location in `jp` (for example: `en/manual/get-started/index.md` to `jp/manual/get-started/index.md`).
2. Translate the page.
3. Check if your page has any errors.
