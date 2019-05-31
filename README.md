# react-native-download

A simple straightforward react native module that lets you schedule downloads onto your download manager for android.

- Support custom headers for authentication
- File download scheduler
- Cancel file downlaod
- Check status of the download

TODO - ios module

### Installation:

`yarn add react-native-simple-download-manager`

or

`npm i react-native-simple-download-manager --save`

### Mostly automatic installation

`react-native link react-native-simple-download-manager`

### Manual installation

#### Android

1. Open up `android/app/src/main/java/[...]/MainApplication.java`

- Add `import com.masteratul.downloadmanager.ReactNativeDownloadManagerPackage;` to the imports at the top of the file
- Add `new ReactNativeDownloadManagerPackage()` to the list returned by the `getPackages()` method

2. Append the following lines to `android/settings.gradle`:
   ```
   include ':react-native-simple-download-manager'
   project(':react-native-simple-download-manager').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-simple-download-manager/android')
   ```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
   ```
     compile project(':react-native-simple-download-manager')
   ```

### Usage

```js
const downloadManager = require("react-native-simple-download-manager");

const url = "http://url/to/file.ext?query=parmas";
const headers = { Authorization: "Bearer abcsdsjkdjskjdkskjd" };
const config = {
  downloadTitle: "Title that should appear in Native Download manager",
  downloadDescription:
    "Description that should appear in Native Download manager",
  saveAsName: "File name to save",
  allowedInRoaming: true,
  allowedInMetered: true,
  showInDownloads: true,
  external: false, //when false basically means use the default Download path (version ^1.3)
  path: "Download/" //if "external" is true then use this path (version ^1.3)
};

downloadManager
  .download((url = ""), (headers = {}), (config = {}))
  .then(response => {
    console.log("Download success!");
  })
  .catch(err => {
    console.log("Download failed!");
  });
```

### Advanced Usage

The module currently supports

- download,
- queueDownload,
- attachOnCompleteListener,
- cancel,
- checkStatus

You can check https://github.com/master-atul/react-native-simple-download-manager/blob/master/index.js

### Contributors

- [Atul R](https://github.com/master-atul)
- [Shivam Barsaley](https://github.com/shivambarsaley)
- [ibrahimtelman](https://github.com/ibrahimtelman)
- [KingDark](https://github.com/kingdark1234)

Peace ! ✌🏻🌮
