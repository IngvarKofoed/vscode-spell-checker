# vscode-spell-checker
[![Build Status](https://travis-ci.org/Jason-Rev/vscode-spell-checker.svg?branch=master)](https://travis-ci.org/Jason-Rev/vscode-spell-checker)

A simple source code spell checker for typescript and javascript.

For the readme on the plugin: [README](./client/README.md).

## Contributions

## Building the extension

1. Build the server: `cd server && npm install && npm run build && cd ..`
1. Build the client: `cd client && npm install && npm run build && cd ..`
1. Launch vscode: `code client`
1. Run the extension from vscode: `F5`

## Dictionaries / Word List

Improvements to existing word lists and new word lists are welcome.

The source text for each dictionary is in `./server/dictionaries`.

### Format for Dictionary Word lists

The simplest format is one word per line.

```text
apple
banana
orange
grape
pineapple
```

For programming languages, a word list might look like this:

```php
ZipArchive::addGlob
ZipArchive::addPattern
ZipArchive::close
ZipArchive::deleteIndex
ZipArchive::deleteName
ZipArchive::extractTo
```

The word list complier will convert camelCase and snake_case words into a simple word list.
This is both for speed and predictability.

```php
ZipArchive::deleteIndex
```

becomes:

```text
zip
archive
delete
index
```

Spaces between words in the word list have a special meaning.

```text
New Delhi
New York
Las Angles
```

becomes in the compiled dictionary:

```text
new delhi
new
delhi
new york
york
las angles
las
angles
```

Spaces in the compiled dictionary have a special meaning.
They tell the suggestion algorithm to suggest: 'newYork', 'new_york', 'new york', etc. for 'newyork'.

### Compiling Word List

Use the `npm run build-dictionaries` command to build the dictionaries for the extension.

### Locals

The default language is English: `"cSpell.language": "en"`

cSpell currently has English locals: `en-US` and `en-GB`.

Example words differences: behaviour (en-GB) vs behavior (en-US)

<!---
    cSpell:ignore newyork
    cSpell:words behaviour behavior
-->
