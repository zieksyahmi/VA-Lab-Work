LAB 4

1.0 exiftool

    exiftool ocean.jpg

We use exiftool to extract metadata from the image file so that hidden information stored inside the image such as file details, creation data and additional embedded information that cannot be seen normally

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/f42bdc157c813a1692c1947666228f2d12662dd6/gambar/lab4%201.png)

and then we found in the comment: THIS IS HIDDEN FLAG

This show that image can contain hidden data within metadata fields such as comments

2.0 hexeditor

    hexeditor computer.jpg

We use hexeditor to view the raw binary content of the file. It will allows us to analyze both hexadecimal values and ASCII-readable text inside the image, which may reveal hidden or embedded information.

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/ec895856578488a3e21e7239d398f925cb5b8074/gambar/lab4%202.png)

From the ouput, we can see that hexeditor displays two sections which: • Left side shows hexadecimal values • Right side shows ASCII-readable text

3.0 binwalk

    binwalk dog.jpg

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/2a553b1c0feac5daa3e5cffa99adcdc558a73b21/gambar/lab4%203.png)

We can see zip file is embedded in this file. So now we can extract it using

    binwalk -e dog.jpg

and then we will get _dog.jpg.extracted folder. so we can see what is in the folder.

    cd _dog.jpg.extracted
    ls
    
So, we can see it contains hidden_text.txt now open the hidden_text.txt to see what is inside

    open hidden_text.txt

![image](https://github.com/0yells/VA-Lab-Work/blob/b3cbe7908ba97d7027653503dbed046a5f88bdf4/gambar/empat.png)
and then we found the THIS IS A HIDDEN FLAG

4.0 strings

    strings computer.jpg

We use the strings command to extract human readable text from a binary file. This will helps identify any embedded text or information without analyzing raw hexadecimal data

![image](https://github.com/0yells/VA-Lab-Work/blob/0c1c51ec2b7dda45b515c905718f44cc6aba7484/gambar/lima.png)
The command displays multiple readable strings such as: • JFIF • ICC_PROFILE • RGB XYZ • lcms

Some random or unreadable characters are also shown. No hidden flag or meaningful secret message was found

5.0 file

    file solitaire.exe

We use the file command to determine the actual type of a file based on its content, not just its file extension.

![image](https://github.com/0yells/VA-Lab-Work/blob/12bb95c35834113b0ed19ca66bd4c3f9f89fa340/gambar/enam.png)
and we can see that the actual file extension of solitaire.exe is actually .png so we can change the file's extension

    mv solitaire.exe solitaire.png

    open solitaire.png

now we can open solitaire image

![image](https://github.com/0yells/VA-Lab-Work/blob/3546b72f2aa52e41851c6c5f43d1e422b16343e6/gambar/tujuh.png)
it also same to rubiks.jpg

![image](https://github.com/0yells/VA-Lab-Work/blob/3eaedbcdc7ea966a31983579b7701344362c12a6/gambar/lapan.png)
nd it turns out to be .png extension. we can change the extension by using

    mv rubiks.jpg rubiks.png

    open rubiks.png

![image](https://github.com/0yells/VA-Lab-Work/blob/1209cc18d84dc838c834f3c3da65c90b2ac0a3b5/gambar/sembilan.png)
