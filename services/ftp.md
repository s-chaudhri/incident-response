<!-- This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA. -->

# FTP Install on Kali Linux

[**Incident Response Home**](../README.md)

Log into Kali system

Open terminal on desktop screen

If you do not have root access input command 'sudo' then command you want for example: 
kali@kali:~$ means you do not have root access. 
kali@kali:~$ sudo apt-get update gives you root access also inputing 'su -' will give root access. 
kali@kali:~$ su - becomes root@kali:~#.

Password is needed to gain root access. Root password for Kali is 'toor'

After root access, type command: 'apt-get update' to make sure your system is up-to-date

Run: 'apt-get upgrade' to make sure your updates are upgraded to newest applications. 
The 'update' and 'upgrade' commands may take a little time depending on your system

Run: 'apt-get install vsftpd'. 
VSFTPD is a highly secure and easy to run ftp server that is good for business and professional use

The installation takes time so let it download

Once it is downloaded you have to configure the server. 
This one is a basic configuration that will get the server up and running with decent security. 
Later I will post a more in depth configuration that will give more security to the server

To configure the ftp server type the command: 'vim /etc/vsftpd.conf'. 
I use vim as my text reader, yours might be different so try either 'nano' or 'vi'
Type 'i' to start editing the file

Uncomment the following files 
(the files will have a # symbol infront of them so in order to uncomment you just delete the # symbol): 
anonymous_enable=NO (protects against anonymous login) 
local_enable=YES
write_enable=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
Hit ESC key

Run: ':x! !' to save the file

Run: '/etc/init.d/vsftpd restart' to lock in the changes. You can also use the command 'service vsftpd restart'

Before logging into the server you have to create users for it

Run: 'useradd' or 'adduser' command which then prompts you to make a root user for the server. 
Create your username and password that you will use for the server

Run: '/etc/init.d/vsftpd start' to start the server. You can also use 'service vsftpd start'

Run: '/etc/init.d/vsftpd status' to check the server to see if it is active. You can also use 'service vsftpd status'

Using the command 'localhost' will automatically connect the server to your local/internal IP address

Run: 'ftp localhost' it will then prompt you to type your username and password you created earlier. 
If it logs in you have successfully installed your ftp server.

To check and see for sure type command: 'ip a' or 'ifconfig' to see the local host/internal IP
Once you have that IP, open a web browser and type: 'ftp://insertyouripaddresshere and then click ENTER
If your server is up and running it should take you to a screen that asks for a username and password.
Input your username and password that you used for the ftp login. This is the protection from anonymous use.