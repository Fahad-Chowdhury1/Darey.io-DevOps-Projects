# Advanced Linux Commands

### <u>Summary</u>
Within this part of my project i will be understanding how to manage file permissions and ownerships within Linux. This knowledge will allow me to control access to files and directories, ensuring the security and integrity of my system.

In Linux, permissions are represented using numberic values, each permission such as no permissions, read, write, and execute is assigned a numerical value as seen below:

no permissions = 0
Read = 4
Write = 2
Execute = 1

In total the numbers add up to 7.

#### <u>Understanding Linux User Classes</u>
Before managing file access, you need to know who Linux is actually talking to. Permissions are divided into three distinct categories:

Owner: The individual who created the file often labeled as 'user'.

Group: A specific set of users granted shared access.

Others: Everyone else on the system who doesn't fit the first two roles.

#### <u>The Meaning of Hyphens (-)</u>
In permission strings, a hyphen isn't a user type, it’s a placeholder. It simply indicates a lack of permission, showing exactly where access has been restricted.


## <u>Example commands</u>

I'm going to get a bit practical with examples using the ls -latr command.

![ls-latr_Command](IMG/ls-latr_Command.png)

In the terminal output above you can notice the first characters either being a hyphen (-) or a d, the d stands for directory whereas the - stands for file.

You'll also notice letters like 'r' and 'w' and 'x' these stand for "read, write and execute" if a permission is not granted in place of these characters you will only see a hyphen (-)

## <u> File Permission Command</u>
To manage file permissions and ownership, Linux provides Several commands:

#### chmod command - 
The 'chmod' command allows me to modify file permissions. You can use both symbolic and numeric representations to assign permissions to the user, group and others.

For example, i will create an empty file using the 'touch' command and will then check the permission of the file.

![File_Permissions](IMG/File_Permissions.png)

As you can see above, this is a file (represented by the -) as a user i also have read and write permissions, but i do not have 'x' (execution permissions), the same is for the group user, however for 'others' they only have the read permission.

#### Updating permissions - 
Now i'll go ahead and update the permissions on this file so that all the user classes have the execute permission by using the 'chmod +x' command.

![Changing_Permissions](IMG/Changing_Permissions.png)

As you can see above now, represented by the 'x' all user groups across the board now have execute permissions.

The same command can be executed to achieve the same result using the numbers approach, as mentioned earlier R+W+X add up to 7 with Read being number 4, Write being number 2 and Execute being number 1. In this instance i will use the chmod 755 script.sh command to change permissions

![Numerical_Permissions](IMG/Numerical_Permissions.png)

As you can see above with the command 755 i have given the first group (Owner) a 7, which means W+R+X permissions, whereas the 2nd (group) and 3rd (other) groups both have a 5, which means only R + X permissions.

(4+2+1) = 7 for the user (Read, write and execute)
(4+1)   = 5 for the group (read and execute)
(4+1)   = 5 for the others (read and execute)

which is how we've come to '755'


I'll use another example where the owner of a file is currently the onlyone with full permissions to 'note.txt'

To allow group members and others to read, write and execute the file, i will change it to -rwxrwxrwx permission type (Numerically this will be 777)


![Owner_Permisions](IMG/Note_Permissions.png)


#### <u>chown Command</u>
The ch(change)own(ownership) command allows me to change the ownership of files, directories or symbolic links to a specific username or group.

Below is generally the basic format used to execute the command:

'chown [option] owner[:group] file(s)'

In this example i'm going to assume there is a user on the server called "John", a group on the server called "Developers" and i want the owner of 'filename.txt' changed from 'fahad' to 'john', and to ensure that any user in the developer group has ownership of the file as well.

The command i will use would look like this:

chown john:developer filename.txt.

![Changing_Ownership](IMG/Change_Ownership.png)

As you can see above the file 'filename.txt' is now owned by 'john' and the 'developers' group.

#### <u>superuser privelleges</u>
It is sometimes necessary t become the superuser to perform important tasks in linux, but as we know, we should not stay logged in as the superuser. Thankfully the terminal only grants access to superuser 15 minutes at a time before requesting the password be inserted again. 

To use the superuser privilleges i will be using the command 'sudo' which stands for super user.

To simply switch to the root user, i will run the sudo -i command.

![Super_User](IMG/Super_User.png)

As you can see above i have now become a sudo user with 'fahad@fahad' changing to 'root@fahad'

if i want to exit superuser i simply just have to type 'exit' in the terminal and this will log me out of superuser.


![Super_User_Exit](IMG/Super_User_Exit.png)

<br>
<br>


## <u>User Management on Linux</u>

As a devops engineer i am also going ot be doing systems administration which involves managing diffrent users on the servers. So it's important i know how to create a new user, or group, modify their permissions, update password and such similar tasks.


#### <u>Creating a User</u>
I'll be creating a new user on the Ubuntu Server, by using the 'adduser' command. Assuming the name of the user to be created is 'John' i'll be using the command line - 'sudo adduser john'

![New_User](IMG/New_User.png)

As you can see above, after creating the user i was prompted to enter and confirm the password for 'john' as well as some additional contact information. After successfully creating the user john, the system will create a home directory for the user account. which i will access by navigating to /home/john this is where the server will store their respective data.

![Changing_User](IMG/Changing_User.png)


#### <u>Granting Admin Privileges</u>
So by default new created user accounts do not have admin privileges. So in this instance i will grant my new user 'john' access to admin privileges by adding him to his user to the 'sudo' group. As you well know users in the sudo group can run commands with admin privileges. I will accomplish this by running the command 'sudo usermod -aG sudo john'


![Granting_John_Admin](IMG/Granting_Admin_Privs.png)

to break down the command line i used, 'usermod' is a command that modifies the users account properties.

-a stands for 'append' and is used to add the user to teh spcified group(s) without removing them from other groups they may already belong to.

-G stands for 'supplementary groups' it specifies the grtoups to which the user should be added or modified to.

#### <u>Switching User Accounts</u>

Now that i've created John as a user and given him admin privileges i will log out of my own account and log in as john. I can do this on the terminal by using the 'su' command line, this is used to switch to another user account followed by the username, in this instance the username is 'john'

So for example the command i will run is 'su john'.

![Switching_to_John](IMG/Changing_Accounts.png)

As you can see above, the terminal has changed from 'fahad@fahad' to 'john@fahad'

## <u>Modifying User Accounts</u>

#### <u>Changing User Password</u>

I'm going to now change the password for the user, this will be accomplished by running the 'passwd' command followed by the username.

My command will look something like this: 'sudo passwd john'


![Password_Change](IMG/Password_Change.png)


#### <u>Creating a Group</u>

To create a new group i'll be using the 'groupadd' command to create a group called 'developers'

![Group_Creation](IMG/Creating_A_Group.png)

#### <u>Adding Users to the Group</u>
Using the 'usermod' command i'll be able to add users to the group. For example, to add the user i created earlier 'john' and a new user i will create called 'jane' i will add them both to the developers group using the command line below:

sudo usermod -aG developers john
sudo usermod -aG developers jane


![Jane_John_Group](IMG/Adding_Users_to_Group.png)

#### <u>Verifying Group Memberships</u>
To confirm john & jane's group i will verify it by using the 'id' command, this command will check the group memberships for the users.

![Group_Verification](IMG/Group_Verification.png)

As you can see above, both john and jane are within the 'developers' group.


#### <u>Deleting a User</u>

To delete a user i'll be running the command line 'sudo userdel jane'

![User_Deletion](IMG/User_Deletion.png)

As you can see above, i deleted the user 'jane' and then ran the id command to verify she does not exist as a user anymore.


#### <u>Ensuring Proper Group Permissions</u>

Groups in linux are used to manage permissions for files and directories, i will ensure that the relevant files or directories have the appropriate group ownership and permissions. In this example i will be granting the 'developers' group ownership of a directory.

This will be done using the command 'sudo chown :developers /path/to/directory'

![Group_Permissions](IMG/Group_Permissions.png)

Now to grant read and write permissions to the group i'll run the command
'sudo chmod g+rw /home/DevOps'

![Read_Write_Privs](IMG/Read_Write_Privs.png)

As you can see i ran the command to give the group Read + Write to the directory and verified it using the 'ls -ld' command.

Task:

Create a group on the server named 'devops'

![Group_DevOps](IMG/DevOps_Group.png)

Create 5 users: mary, mohammed, ravi, tunji, sofia and ensure they belong to the 'devops' group.

![User_Group_Additions](IMG/User_Task_Creation.png)

Create a folder for each user in the '/home' directory and ensure that each folders group ownership is under 'devops'

![Directory_Groups](IMG/Directory_Groups.png)



