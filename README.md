# klei-fs

The `klei-fs` module contains some nice to have addons to the native node.js fs (filesystem) module.

## Installation

```bash
npm install klei-fs
```

## Usage

```javascript
var fs = require('klei-fs');

// Now you can use it as the native fs module,
// and you also have access to klei-fs own functions
```

## Functions

### forEachInDir

#### Params

 * *String* **dir** - The directory to read
 * *Function* **cb** - A callback that is called for each file in the directory, and gets following parameters:
    * *Error* **err** - An error if something went wrong, or empty if everything is ok
    * *String* **file** - The full path to the file
    * *Number* **index** - The index of the file in the files array
    * *Array* **files** - The files array, containing only the filenames and not the full paths
 * *Function* **emptyCb** - A callback that is called if the directory is empty

Reads a directory (like fs.readdir), iterates over all files and returns the full file path to the callback. (i.e. you don't have to do a `path.join(dir, file)` in order to read the file)

### filterDir

#### Params

 * *String* **dir** - The directory to read
 * *Function* **filter** - The filter method. *cb* is only called for the files where *filter* returns a thruthy value.
    * *String* **file** - The full path to the file
 * *Function* **cb** - A callback that is called for each file in the directory, and gets following parameters:
    * *Error* **err** - An error if something went wrong, or empty if everything is ok
    * *String* **file** - The full path to the file

Reads a directory (like fs.readdir), filters the files with the given *filter* function, iterates over the filtered files and returns the full file path to the callback. (i.e. you don't have to do a `path.join(dir, file)` in order to read the file)

### readJson

#### Params

 * *String* **file** - The file to read
 * *Function* **cb** - A callback that is called when the file has been read and parsed:
    * *Error* **err** - An error if something went wrong, or empty if everything is ok
    * *String* **json** - The parsed json contents of the file

### mkdirp

#### Params

 * *String* **path** - The directory path to create
 * *String* **mode** - The mode to create the dir(s) with, defaults to `0777`
 * *Function* **cb** - A callback that is called when the dir(s) have been created:
    * *Error* **err** - An error if something went wrong, or empty if everything is ok

Creates directories recursively, like `mkdir -p` in the shell.
