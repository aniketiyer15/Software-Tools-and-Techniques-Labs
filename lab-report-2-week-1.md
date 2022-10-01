# Week 1- Remote Access and the Filesystem
**1) Installing VS Code**\
I did not do this step because I had already installed VS Code on my laptop. Once you finish installing VS Code, you should see a screen something like this:\
![Image](https://cdn.discordapp.com/attachments/891952727641456661/1025561264975523880/unknown.png)



**2) Remotely Connecting**\
First you should set a password for your CSE 15L account and then once the password has been set, you should open the terminal on VS code and type out the following command:\
`ssh cs15lfa22abc@ieng6.ucsd.edu`\
Here abc is the last two letters of your username\
After typing in this command, the terminal will ask you for the password\
Once you enter the password it would display a message something like this:\
![Image](https://cdn.discordapp.com/attachments/891952727641456661/1025564997260157069/unknown.png)\
*PS : Don't worry!! It could take some time to get logged onto the server. It took me about 25-30 attempts before I could log in*\
![Image](https://cdn.discordapp.com/attachments/891952727641456661/1025565479638667345/unknown.png)\
**Now you've been logged into the server**\
**3) Trying some commands**\
*You could try some commands like the following ones listed:*
* `ls` can be used to list the files/folders in the directory of the account cs15lfa22dp
* `pwd` can be used to print the path of the current working directory
* `cd perl5` can be used to change the working directory to perl5
* `exit` can be used to log out of the server

![Image](https://media.discordapp.net/attachments/891952727641456661/1025567636349784104/unknown.png)\

**4) Moving Files with scp**\
The command `scp` helps to copy files from the computer you are working on to the local computer (server) you are connected to\
You could create a java program and save it on your computer\
Now, you can open the VS Code terminal and type the following commands to copy the java file from your computer to the computer you are connected to\
`scp WhereAmI.java cs15lfa22abc@ieng6.ucsd.edu:~/`\
In this case WhereAmI is the name of my Java program\
It will ask you to enter a passowrd just as it prompts you when use the `ssh` command\
Now you can run the same program on the computer you are connected to and it works\
![Image](https://media.discordapp.net/attachments/891952727641456661/1025573333728759878/unknown.png)\

**5) Setting an SSH Key**\
Typing the password again and agin to log into the remote server could be painful\
Instead we could set up `ssh key` which makes it easier and less painful to log into the remote server\
To do this first open the command prompt\
Type the following command:\
`$ ssh-keygen`\
For finishing the process on windows you could follow the instructions given on this [link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation)\
Now we need to copy the public (not the private) key to the .ssh directory of your user account on the server.\
Firstly ssh into the remote server and then type the following commands:\
`mkdir .ssh`\
`exit`\
Now type the following scp command in order to copy the key onto the server\
`scp /Users/<name of the user>/.ssh/id_rsa.pub cs15lfa22@ieng6.ucsd.edu:~/.ssh/authorized_keys`\
Now instead of typing the whole password to log in, you could use the key which you set to ssh or scp to the remote server\
![Image](https://cdn.discordapp.com/attachments/891952727641456661/1025564997260157069/unknown.png)\
**6) Optimizing Remote Running**\
* You could write any command at the end of the ssh to run the command on the remote server\
For example :\
![Image](https://cdn.discordapp.com/attachments/891952727641456661/1025588559106801724/unknown.png)
* You could also use the up arrow to access the previous commands in the terminal
* Semi-colons could be used to include multiple commands in a single line
* I used a total of 10 keystrokes to execute the following command:
`ssh cs15lfa22dp@ieng6@ucsd.edu "ls"`




