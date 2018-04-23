# JavaFileUploader V1.0

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

* PS: File name as stored in server is the return value of the upload method in the JavaFileUploader API

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
* http://localhost/exemplefolder/uploads/f_5ac66af018455.jpg
* http://localhost/exemplefolder/uploads/f_c4zd625c12785.pdf
* http://localhost/exemplefolder/uploads/f_t4ce8a4135btw.txt               

- - -

### Code snippets
#### Upload & Delete

```java
    // ...
    import java.io.IOException;
    import java.net.ProtocolException;
    import rest.file.uploader.tn.FileUploader;
    // ...
    
    public static void main(String[] args) throws ProtocolException, IOException{
        // ...
        FileUploader fu = new FileUploader("localhost/exemplefolder");
        
        //Upload
        String fileNameInServer = fu.upload("C:/Users/Public/test.pdf");
        
        // ...
        
        //Delete
        if(fu.delete(fileNameInServer)){
            System.out.println("File "+fileNameInServer+" deleted.");
        }
        
        // ...
    }
```
    
#### Get file extension

```java
    // ...
    System.out.println(FileUploader.getFileExtension("C:/Users/Public/test.png")); /*This will print "png"*/
    // ...
```

# Usage with Symfony
To make this uploader compatible with Symfony, place the scripts inside your project web folder, the scripts will then create a folder named "Uploads", all uploaded files will be saved inside that folder. To change the upload destination folder, open the upload.php script and change the folder path (do the same for delete.php script).

The upload method will return a string consisting of the file name as stored in the service, concat it with your server web folder url to get the url to the uploaded image.
### Exemple
    http://localhost/[PROJECT_NAME]/web/uploads/[FILE_NAME]

### Code snippets
```java
    // ...
    import rest.file.uploader.tn.FileUploader;
    // ...
    
    try{
        FileUploader fu = new FileUploader("localhost/[PROJECT_NAME]/web/");
        
        //Upload
        String fileNameInServer = fu.upload("[FILE_PATH]");
        
        //Delete
        if(fu.delete(fileNameInServer)){
            System.out.println("File "+fileNameInServer+" deleted.");
        }
    }catch(Exception ex){
        ex.printStackTrace();
    }
    
    // ...
```

- - -

#### Potential errors:
* Try changing your server limits (post_max_size, upload_max_filesize, memory_limit) to -1 in the server's php.ini file.
