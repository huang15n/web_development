

### Saving Data for Later

You can store data in two basic ways: in flat files or in a database.
a flat file can ave many formats, but in general, when we refer to a flat file, we mean a simple text file, very limiting 


### Processing Files 
writing data to a file requires three steps 
1 open the file, if the file does not already exist, you need to creat it 
2 write the data to the file 
3 close the file 


Similarly, reading data from a file takes three steps:
Open the file. If you cannot open the file (for example, if it doesn’t exist), you need to recognize this and exit gracefully.
Read data from the file.
Close the file.



Opening a File: to open a file, you use fopen() function 
choosing file modes. it needs to know whether the file can be opnened by another script while you have it open and whether you have permission to use it in the requested way 
essentially , file modes give the os a mechanism to determine how to handle access requests from other 


### using fopen() to open a file 
$fp = fopen("/path/file_name.txt",w)

When fopen() is called, it expects two, three, or four parameters. Usually, you use two

The first parameter should be the file you want to open. You can specify a path to this file, as in the preceding code; here, the orders.txt file is in the orders directory. We used the PHP built-in variable $_SERVER['DOCUMENT_ROOT'] but, as with the cumbersome full names for form variables, we assigned a shorter name.

this variable points at the base of the document tree on your web server. This code line uses .. to mean “the parent directory of the document root directory.” This directory is outside the document tree, for security reasons. In this case, we do not want this file to be web acces- sible except through the interface that we provide. This path is called a relative path because it describes a position in the file system relative to the document root.


On our Unix server, this path could be something like /data/orders. If no path is specified, the file will be created or looked for in the same directory as the script itself. 

In a Unix environment, you use forward slashes (/) in directory paths. If you are using a Windows platform, you can use forward (/) or backslashes (\). If you use backslashes, they must be escaped (marked as a special character) for fopen() to understand them properly. To escape a character, you simply add an additional backslash in front of it

The second fopen() parameter is the file mode, which should be a string. This string speci- fies what you want to do with the file. In this case, we are passing 'w' to fopen(); this means “open the file for writing.”

The third parameter of fopen() is optional. You can use it if you want to search the include_path (set in your PHP configuration

If you want to do this, set this parameter to true. If you tell PHP to search the include_path, you do not need to provide a directory name or path:
$fp = fopen('orders.txt', 'ab', true);

The fourth parameter is also optional. The fopen() function allows filenames to be prefixed with a protocol (such as http://) and opened at a remote location. Some protocols allow for an extra parameter. We look at this use of the fopen() function in the next section of this chapter.
If fopen() opens the file successfully, a resource that is effectively a handle or pointer to the file is returned and should be stored in a variable—in this case, $fp. 


### Opening Files Through FTP or HTTP
In addition to opening local files for reading and writing, you can open files via FTP, HTTP, and other protocols using fopen(). You can disable this capability by turning off the allow_url_fopen directive in the php.ini file. If you have trouble opening remote files with fopen(), check your php.ini file.
If the filename you use begins with ftp://, a passive mode FTP connection will be opened to the server you specify and a pointer to the start of the file will be returned.
If the filename you use begins with http://, an HTTP connection will be opened to the server you specify and a pointer to the response will be returned.


### Addressing Problems Opening Files
An error you might make is trying to open a file you don’t have permission to read from or write to. (This error occurs commonly on Unix-like operating systems, but you may also see it occasionally under Windows.) 


If you receive this error, you need to make sure that the user under which the script runs has permission to access the file you are trying to use. Depending on how your server is set up, the script might be running as the web server user or as the owner of the directory where the script is located.



If the call to fopen() fails, the function will return false. It will also cause PHP to emit a warning_level error (E_WARNING). You can deal with the error in a more user-friendly way by suppressing PHP’s error message and giving your own


```PHP
<?php 


$document_root = $_SERVER["DOCUMENT_ROOT"];

$fp = fopen("$document_root/something.txt",'r');
if(!$fp){
	echo "<h1>your encounter some errors this time</h1>";
	exit;
}


?>

```
Note
In general, use of the error suppression operator is not considered good style, so consider it a shortcut for now. The method described here is a simplistic way of dealing with errors. We look at a more elegant method for error handling in Chapter 7, “Error and Exception Handling.” But one thing at a time.
$fp = @fopen("$document_root/something.txt",'r');
The @ symbol in front of the call to fopen() tells PHP to suppress any errors resulting from the function call. Usually, it’s a good idea to know when things go wrong, but in this case we’re going to deal with that problem elsewhere.
Using this method tends to make it less obvious that you are using the error suppression operator, so it may make your code harder to debug.


### Writing to a File
you can use either of the functions fwrite() (file write) or fputs() file put string; fputs() is an alais to fwrite() 


you can call fwrite() in the following way:
fwrite($fp,$outputstring);


an alternative to fwrite() is the file_put_contents() function 
int file_put_contents(string filename, mixed data,)
this function writes the string contained in data to the file named in filename without any need for an fopen() or fclose() function call

this funciton is the half of a matched pair, the other half being file_get_contents()
you most commonly use the flags and context optional parameters when writing to remote files using HTTP or FTP 



### Parameters for fwrite() 
the function fwrite() actually takes three parameters, but the third one is optional 
the prototype for fwrite() is 
int fwrite(resource handle, string [, int length])
the third parameter, length , is the maximum number of bytes to write 
if this parameter is supplied, fwrite() will write strign to the file pointed to by handle until it reaches the end of string or has written lenght bytes, whichever coems first 

You can obtain the string length by using PHP’s built-in strlen() function, as follows: fwrite($fp, $outputstring, strlen($outputstring)); 
Using a special field separator allows you to split the data back into separate variables more easily when you read the data back. 


### Closing a File
You should do this by using the fclose() function as follows:
fclose($fp);
This function returns true if the file was successfully closed or false if it wasn’t. This process is much less likely to go wrong than opening a file in the first place, so in this case we’ve chosen not to test it.



```PHP
<?php 

$document_root = $_SERVER["DOCUMENT_ROOT"];

$my_file = fopen("$document_root/new_text.txt","w") or die("this is error");
for($counter = 1; $counter < 100; $counter++){
	$text = "I am awesome +".$counter."\n";
	fwrite($my_file,$text);
}
echo "<h1>File has been processed, please check out $document_root/new_text.txt </h1>";
fclose($my_file);


?>
```
### Reading from a File

Again, you open the file by using fopen(). In this case, you open the file for reading only, so
you use the file mode 'rb'


Knowing When to Stop: feof(), you use a while loop to read from the file until the end of the file is reached.
The while loop tests for the end of the file using the feof() function


Reading a Line at a Time: fgets(), fgetss(), and fgetcsv()

This function reads one line at a time from a file. In this case, it reads until it encounters a newline character (\n) or EOF.
You can use many different functions to read from files. The fgets() function, for example, is useful when you’re dealing with files that contain plain text that you want to deal with in chunks.
An interesting variation on fgets() is fgetss(), which has the following prototype: string fgetss(resource fp[, int length[, string allowable_tags]]);
This function is similar to fgets() except that it strips out any PHP and HTML tags found
in the string. If you want to leave in any particular tags, you can include them in the allowable_tags string. You would use fgetss() for safety when reading a file written by somebody else or one containing user input. Allowing unrestricted HTML code in the file could mess up your carefully planned formatting. Allowing unrestricted PHP or JavaScript could give a malicious user an opportunity to create a security problem.

The length parameter should be greater than the length in characters of the longest line in the file you are trying to read, or 0 if you do not want to limit the line length.
The enclosure parameter specifies what each field in a line is surrounded by. If not specified, it defaults to " (a double quotation mark).

```PHP
<?php 

$document_root = $_SERVER["DOCUMENT_ROOT"];

$my_file = fopen("$document_root/new_text.txt","rb") or die("this is error");
flock($my_file,LOCK_SH);

while(!feof($my_file)){
	$lines = fgets($my_file);
	echo htmlspecialchars($lines)."<br />";
} 

flock($my_file, LOCK_UN);


fclose($my_file);


?>
```


### Reading the Whole File: readfile(), fpassthru(),
file(), and file_get_contents()
Instead of reading from a file a line at a time, you can read the whole file in one go. Here are four different ways you can do this.
The first uses readfile(). 

readfile("$document_root/../orders/orders.txt");
A call to the readfile() function opens the file, echoes the content to standard output (the
browser), and then closes the file. The prototype for readfile() is
int readfile(string filename, [bool use_include_path[, resource context]] );


The optional second parameter specifies whether PHP should look for the file in the include_path and operates the same way as in fopen(). The optional context parameter is used only when files are opened remotely via, for example, HTTP; we cover such usage in more detail in Chapter 18. The function returns the total number of bytes read from the file.
Second, you can use fpassthru(). To do so, you need to open the file using fopen() first. You can then pass the file pointer as an argument to fpassthru(), which dumps the contents of the file from the pointer’s position onward to standard output. It closes the file when it is finished.
You can use fpassthru() as follows:
$fp = fopen("$document_root/../orders/orders.txt", 'rb');
fpassthru($fp);


The function fpassthru() returns true if the read is successful and false otherwise.
The third option for reading the whole file is using the file() function. This function is identical to readfile() except that instead of echoing the file to standard output, it turns it into an array. We cover this function in more detail when we look at arrays in Chapter 3. Just for reference, you would call it using
$filearray = file("$document_root/../orders/orders.txt");
This line reads the entire file into the array called $filearray. Each line of the file is stored
in a separate element of the array. Note that this function was not binary safe in older versions of PHP.


Reading a Character: fgetc()
Another option for file processing is to read a single character at a time from a file. You can do this by using the fgetc() function. It takes a file pointer as its only parameter and returns the next character in the file. You can replace the while loop in the original script with one that uses fgetc()




Reading an Arbitrary Length: fread()

The final way you can read from a file is to use the fread() function to read an arbitrary
number of bytes from the file. This function has the following prototype:
string fread(resource fp, int length);
It reads up to length bytes, to the end of the file or network packet, whichever comes first.



### Checking Whether a File Is There: file_exists()


If you want to check whether a file exists without actually opening it, you can use
file_exists()

```PHP
if(file_exists("something.txt")){
   echo "this exists";
} else{
	echo "this is bullshit";
	exit;
}
```


### Determining How Big a File Is: filesize()

It returns the size of a file in bytes and can be used in conjunction with fread() to read a whole file (or some fraction of the file) at a time. 
```PHP
echo "the size of the file is ".filesize("$document_root/new_text.txt")."<br />";



```



### Deleting a File: unlink()

If you want to delete the order file after the orders have been processed, you can do so by using unlink()

```PHP
<?php 

$document_root = $_SERVER["DOCUMENT_ROOT"];



$result = unlink("$document_root/next_text.txt");

if(!$result){
	echo "<h1> file being deleted</h1>";
}else{
	echo "<h1> Error/h1>";
}

?>

```




### Navigating Inside a File: rewind(), fseek(), and ftell()


You can manipulate and discover the position of the file pointer inside a file by using
rewind(), fseek(), and ftell().
The rewind() function resets the file pointer to the beginning of the file. The ftell() function reports how far into the file the pointer is in bytes.


You can use the function fseek() to set the file pointer to some point within the file. Its prototype is
int fseek ( resource fp, int offset [, int whence])
A call to fseek() sets the file pointer fp at a point starting from whence and moving offset bytes into the file. The optional whence parameter defaults to the value SEEK_SET, which is effectively the start of the file. The other possible values are SEEK_CUR (the current location of the file pointer) and SEEK_END (the end of the file).
The rewind() function is equivalent to calling the fseek() function with an offset of zero. For example, you can use fseek() to find the middle record in a file or to perform a binary search. If you reach the level of complexity in a data file where you need to do these kinds of things, your life will be much easier if you use a built-for-purpose database.



### Locking Files
(This situation is not uncommon, especially when your website starts to get any kind of traffic volume.) What if one customer calls fopen() and begins writing, and then the other customer calls fopen() and also begins writing

To avoid problems like this, you can use file locking. You use this feature in PHP by using the flock() function. This function should be called after a file has been opened but before any data is read from or written to the file.
The prototype for flock() is
bool flock (resource fp, int operation [, int &wouldblock])
You need to pass it a pointer to an open file and a constant representing the kind of lock you require. It returns true if the lock was successfully acquired and false if it was not. The optional third parameter will contain the value true if acquiring the lock would cause the current process to block (that is, have to wait).

Value of Operation
LOCK_SH Reading lock. The file can be shared with other readers.
LOCK_EX Writing lock. This operation is exclusive; the file cannot be shared.
LOCK_UN The existing lock is released.
LOCK_NB Blocking is prevented while you are trying to acquire a lock. (Not supported on Windows.)


If you are going to use flock(), you need to add it to all the scripts that use the file; otherwise, it is worthless.
Note that flock() does not work with NFS or other networked file systems. It also does not work with antique file systems that do not support locking, such as FAT. On some operating systems, it is implemented at the process level and does not work correctly if you are using a multithreaded server API.



### A Better Way: Databases


Problems with Using Flat Files
There are a number of problems in working with flat files:
■ When a file grows large, working with it can be very slow.
■ Searching for a particular record or group of records in a flat file is difficult. If the records are in order, you can use some kind of binary search in conjunction with a fixed-width record to search on a key field. If you want to find patterns of information (for example, you want to find all the customers who live in Sometown), you would have to read in each record and check it individually.
■ Dealing with concurrent access can become problematic. You have seen how to lock files, but locking can cause the race condition we discussed earlier. It can also cause a bottleneck. With enough traffic on a site, a large group of users may be waiting for the file to be unlocked before they can place their order. If the wait is too long, people will go elsewhere to buy.
■ All the file processing you have seen so far deals with a file using sequential processing; that is, you start from the beginning of the file and read through to the end. Inserting records into or deleting records from the middle of the file (random access) can be difficult because you end up reading the whole file into memory, making the changes, and writing the whole file out again. With a large data file, having to go through all these steps becomes a significant overhead.
■ Beyond the limits offered by file permissions, there is no easy way of enforcing different levels of access to data.


Relational database management systems address all these issues:
■ RDBMSs can provide much faster access to data than flat files. And MySQL, the database system we use in this book, has some of the fastest benchmarks of any RDBMS.
■ RDBMSs can be easily queried to extract sets of data that fit certain criteria.
■ RDBMSs have built-in mechanisms for dealing with concurrent access so that you, as a
programmer, don’t have to worry about it.
■ RDBMSs provide random access to your data.
■ RDBMSs have built-in privilege systems. MySQL has particular strengths in this area.
Probably the main reason for using an RDBMS is that all (or at least most) of the functionality that you want in a data storage system has already been implemented. Sure, you could write your own library of PHP functions, but why reinvent the wheel








     

