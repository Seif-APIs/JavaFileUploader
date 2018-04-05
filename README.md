# PhpRestFileUploader V1.0

### Server configuration:
1. Create a folder inside your server (www for wamp).
2. Extract scripts.rar archive.
3. Copy the two php files (upload.php and delete.php) inside the folder you created earlier.
4. Done.


### Usage:
* The JAR file provided should be included as a library in your JAVA project

* You need to provide the URL to the folder you created earlier in you server to the PhpRestFileUploader JAVA API as serverURL in the constructor.<br/>(exemple: "localhost/foldername")

* Your uploaded files will be under a folder named "uploads" under the folder you created earlier.

* To get an uploaded file you need the URL to the "uploads" folder and the file name as stored in the server.<br/>(exemple: http://localhost/foldername/uploads/filename.extension)

* PS: File name as stored in server is the return value of the upload method in the PhpRestFileUploader JAVA API

- - - -

### Server folder tree exemple (wamp):
```bash
├── www
│   ├── exmplefolder
│   │   ├── upload.php
│   │   ├── delete.php
│   │   ├── uploads
│   │   │   ├── f_5ac66af018455.jpg
│   │   │   ├── f_c4zd625c12785.pdf
│   │   │   ├── f_t4ce8a4135btw.txt
```

#### URLs for this tree will be:

##### Valid ServerUrls: 
* localhost/exemplefolder
* localhost/exemplefolder/
* http://localhost/exemplefolder
* http://localhost/exemplefolder/

#### Files URL: 
* http://localhos/exemplefolder/uploads/f_5ac66af018455.jpg
* http://localhos/exemplefolder/uploads/f_c4zd625c12785.pdf
* http://localhos/exemplefolder/uploads/f_t4ce8a4135btw.txt               
