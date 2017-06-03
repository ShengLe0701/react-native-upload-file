# react-native-upload-file
## Getting started

`npm install react-native-upload-file --save`

### iOS

Add the `node_modules/react-native-upload-file/UploadFile.m` file to ios project by opening xcodeproj with      XCode(`your project/Add Files to [your project's name]`) 

### Android

* Edit `android/settings.gradle` to look like this:

  include ':react-native-upload-file'
  project(':react-native-upload-file').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-upload-file/android')

* Edit `android/app/build.gradle` (note: **app** folder) to look like this: 

  dependencies {

    compile project(':react-native-upload-file')
  }

* Edit `MainApplication.java`

  protected List<ReactPackage> getPackages() {
    return Arrays.<ReactPackage>asList(

          new UploadFilePackage()
    );
  }

## Usage

  Please refer the following sample code.
  ```javascript
  var UploadFile = require('NativeModules').UploadFile;

  //Custom Function to upload a file.
  function upload(token, ) {
    var obj = {
        uploadUrl: API_UPLOAD_SERVER_URL, //https://test.com/upload/
        method: 'POST', 
        headers: {
          'Accept': 'application/json',
          'Authorization': 'jwt ' + token,
        },
        files: [
          {
            name: 'files', //key name
            filename: 'photoid2.jpg', //the name which server will receive  
            filepath: 'file:///storage/emulated/0/Android/data/com.nativeapp/files/Pictures/image-a8196a8f-dec6-4434-a9ae-60f59345efc8.jpg', //local file path
            filetype: 'image/jpeg', //file type
          },
        ],
        fields: { //additional parameters
        },
    };

    FileUpload.upload(obj, (returnCode, returnMessage, resultData) => {
        if( returnCode == 201 ){

        }
        else{
          
        }
    })
  }
  ```

## License

MIT
