# office-toolbox

This is a set of tools for creating, validating, and sideloading an Office Add-in.

## Installation
> **Important:** If this is the first time you're using this tool, first install [Node.js](https://nodejs.org). For developers on Mac, we recommend using [Node Version Manager](https://github.com/creationix/nvm) to install Node.js with the right permissions. When the installation completes, restart your console (or if you are using Windows, restart your machine) to ensure you use the updated system environment variables.

Install `office-toolbox` globally using [NPM](http://npmjs.org/):
```bash
npm install -g office-toolbox
```

## Usage
You can supply arguments on the command-line:

```bash
$ office-toolbox sideload -m my-office-addin-manifest.xml -a word
```

Alternatively, you can run the tool without arguments and it will prompt you for information.

```bash
$ office-toolbox
```

## Creating an Office Add-in
```bash
$ office-toolbox generate
```

This tool creates the scaffolding for an Office Add-in. Once it is complete, open a new command prompt in the new project's folder, and start the HTTPS site:
```bash
$ npm start
```

See [yo office](https://www.npmjs.com/package/generator-office) for more details on how to use the generated project.

## Validating an Office Add-in
```bash
$ office-toolbox validate
```

This tool validates the XML manifest for submission to the Office Store, using an online system, and displays the result in the terminal. 

If you created the manifest using the generator, it does not contain a support URL; you will be able to sideload the manifest locally, but you will need to provide a support URL before submitting it to the Office Store.

## Sideloading an Office Add-in
Before you submit your Office Add-in to the store, you should test it locally by sideloading its manifest. Be sure that the website is running, and then run the tool.

```bash
$ office-toolbox sideload
```

The tool validates the manifest against the online system. On Windows, the tool writes a registry key to HKEY\_CURRENT\_USER\Software\Microsoft\Office\16.0\WEF\Developer. On Mac, the tool creates a hard link in ~/Library/Containers/com.microsoft.Word/Data/Documents/wef to your manifest. The tool then generates a document, spreadsheet, or presentation containing your Office Add-in, which you can open every time you want to load your Add-in.

Copyright (c) 2017 Microsoft Corporation. All rights reserved.