# Nativescript Share File

[![npm](https://img.shields.io/npm/v/@finanzritter/nativescript-share-file.svg)](https://www.npmjs.com/package/@finanzritter/nativescript-share-file)
[![npm](https://img.shields.io/npm/dt/@finanzritter/nativescript-share-file.svg?label=npm%20downloads)](https://www.npmjs.com/package/@finanzritter/nativescript-share-file)
![Publish](https://github.com/FinanzRitter/nativescript-share-file/workflows/Publish/badge.svg?event=release)

:construction: **Work in progress**

This package was forked from the unmaintained package
[braune-digital/nativescript-share-file](https://github.com/braune-digital/nativescript-share-file).
We are currently cleaning up and updating the code.

---

Send/Share files to other apps.

Android Intent, IOS InteractionController:

<img src="https://github.com/FinanzRitter/nativescript-share-file/blob/master/preview/preview-android.png?raw=true" width="250"> .   <img src="https://github.com/FinanzRitter/nativescript-share-file/blob/master/preview/preview-ios.png?raw=true" width="250">



## Installation

Install the plugin in your app.

~~~
npm install @finanzritter/nativescript-share-file
~~~

## Usage

Info: Shared files should be in the `documents` path.

```TypeScript
import { ShareFile } from '@finanzritter/nativescript-share-file';
import { Observable, knownFolders, path, File } from "@nativescript/core";

export class TestClass extends Observable {
  shareFile;
  fileName;
  documents;
  path;
  file;

  constructor() {
    super();

    this.fileName = 'test.txt';
    this.documents = knownFolders.documents();
    this.path = path.join(this.documents.path, this.fileName);
    this.file = File.fromPath(this.path);

    this.shareFile = new ShareFile();

    this.shareFile.open({
      path: this.path,
      intentTitle: 'Open text file with:', // optional Android
      rect: { // optional iPad
        x: 110,
        y: 110,
        width: 0,
        height: 0
      },
      options: true, // optional iOS
      animated: true // optional iOS
    });
  }
}
```

### Arguments

#### path
Path to the file which will be shared.


`String`: Required


#### intentTitle
Title for the intent on Android.

`String`: (Optional)
Default: `Open file:`.


#### rect
Positioning the view for iPads. On iPhones it's always shown on the bottom.

`Object`: (Optional)
Default: `{x: 0, y: 0, width: 0, height: 0 }`.

#### options
Show additional opening options for iOS devices.

`Boolean`: (Optional)
Default: `false`.

#### animated
Opening animation for iOS devices.

`Boolean`: (Optional)
Default: `false`.

## Credits

- **@braune-digital**: for being the original author of this plugin **[braune-digital/nativescript-share-file](https://github.com/braune-digital/nativescript-share-file)**