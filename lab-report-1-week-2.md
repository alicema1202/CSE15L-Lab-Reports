# Lab Report 1
## 1. Installing VScode ##
The first step in logging into our ieng6 account is to install [Visual Studio Code](https://code.visualstudio.com/download). After downloading VScode, you should open the application and see something like this:

![](https://scontent.xx.fbcdn.net/v/t1.15752-9/278045602_299392252340012_8019902017749981740_n.png?_nc_cat=109&ccb=1-5&_nc_sid=aee45a&_nc_ohc=ExScI8dRTRQAX--Ns-C&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVKfPhszPCncKp7V19jjMwU6K1Uelt04vAXIsfVztTvhLw&oe=6279E19D)

## 2. Remotely Connecting ##
To remotely connect, make sure to have [OpenSSH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) installed on your computer (can disregard if you are on MacOS). The information we need for this next step is your course specific account, which can be found [here](https://sdacs.ucsd.edu/~icc/index.php).

Now, type this following statement into your VScode terminal:

``` 
 $ ssh cs15lsp22<username>@ieng6.ucsd.edu 
 ```
 You will see something like this in your terminal after entering your password:

 ![](https://scontent.xx.fbcdn.net/v/t1.15752-9/277922363_1376596046097950_5026305887905797457_n.png?_nc_cat=100&ccb=1-5&_nc_sid=aee45a&_nc_ohc=OVkK8JbD4XgAX96Lr1y&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVKNWdlF_Dhg1jmHcTD4gj9_31hIqAPDLrBv9kt9bVLB8g&oe=62777977)

## 3. Trying Some Commands ##
Now that we are logged into the remote server, we can try some different commands. The ones shown below are: *ls* (list files), *ls -a* (list files including hidden), and *pwd* (print working directory). 

![](commands.png)

Some other ones you may want to try out are *cd*, *cat*, *mkdir*, and *cp*.

## 4. Moving Files with scp ##
Start by creating a new Java file, name it `WhereAmI.java`. Copy the contents of [this page](WhereAmI.md) into your file. 
Now, run the following commands (if you have Java installed):
```Java
javac WhereAmI.java
java WhereAmI
```
Then, type this command to copy this file into the remote server:
```
scp WhereAmI.java cs15lsp22<username>@ieng6.ucsd.edu:~/
```
Running the *ls* command on the ieng6 account should output something like this, showing that the file `WhereAmI.java` has been successfully copied over to the home directory.

![](moveSCP.png)
## 5. Setting an SSH Key ##
Setting an SSH Key will allow us to login to ieng6 without needing a password. We will use the `ssh-keygen` command for this (press enter when prompted to type passphrase).

Now, try logging into ieng6 again using ssh, and you should be able to go in without needing to enter a password.

![](SSHKEY.png)

## 6. Optimizing Remote Running ##
We can optimize remote running and save keystrokes. For example, we are able to copy a file into the home directory and access the contents of it just by entering the following:
```Java
scp WhereAmI.java cs15lsp22<username>@ieng6.ucsd.edu
ssh cs15lsp22<username>@ieng6.ucsd.edu "javac WhereAmI.java; java WhereAmI"
```
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/277991302_3142866135955516_7070268795242236875_n.png?_nc_cat=100&ccb=1-5&_nc_sid=aee45a&_nc_ohc=as-o8cb4bEUAX8MKhKk&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVJbx4nlUjKRwr3Vexvr6wajS_95hrG4S54N8KklwerSlg&oe=627AAFF6)
