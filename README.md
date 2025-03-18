cl# Password-Cracking-on-Linux

## Objective
The purpose of this project is to demonstrate how to use pasword crackers in linux.

<mark style="color : red">Disclaimer: This project is for educational purposes only, and should not be used on any machines/ networks you do not own or are authorized to ethically Hack.</mark>

### Skills Learned
- Password cracking and ethically hacking passwords within a linux directory

### Tools Used
- Kali Linux
- John the Ripper

## Steps

### Create User Accounts and Passwords
Within your Kali Linux CLI (Command Line Interface) you'll want to create a series of user accounts and passwords to use in the demonstration.

(Note:<code>sudo</code> which grants temporary admin prieveleges, may be required to run these commands.)

To create a user account enter in: <code>useradd -m (username)</code>

To assign a password for the user account you just created use: <code>passwd (username)</code> 

(Note: You will be asked to enter this password twice and will not be displayed on screen.)

Repeat these steps for each account you wish to create and keep track of them.

![image](https://github.com/user-attachments/assets/24428cb3-9ba2-49b3-8ad0-249ef6352a63)

Below is the top 10 list of common passwords in 2024, feel free to use these as this list will be used for this demonstartion.

| Username | Password  |
|---       |---        |
| alpha    | 123456    |
| beta     | 123456789 |
| gamma    | 12345678  |
| delta    | password  |
| epsilon  | qwerty123 |
| zeta     | Qwerty1   |
| eta      | 111111    |
| theta    | 12345     |
| iota     | secret    |
| kappa    | 123123    |


### Creating Hash Dump File
In Linux, usernames are stored in a file named <code>passwd</code> and the hashes are stored ina file named <code>shadow</code>. 

These files usually live in <code>/etc/</code> path.

To generate a hasdump file you'll need to combine these files.

This can be done using <code>unshadow</code> command.

<code>unshadow (password_file) (shadow_file)</code>

Before you continue, besure to refresh you Linux commands knowleged and navigate your directory.

Use <code>cd (directory name)</code> to navigate directories

and use <code>ls</code> to display whats contained in the directory you are at.

![image](https://github.com/user-attachments/assets/a68757cc-ce6a-4c10-bfb4-a81d9a16446b)

In Linux, the output is usually displayed immedietly when a command is entered. In this case we want to combined has file to out put into a directory of our choosing.

To do this we will use <code>></code> and name the file <code>hack_me</code>

<code>unshadow /etc/passwd /etc/shadow > ~/hack_me</code>

![image](https://github.com/user-attachments/assets/f56b9688-90af-4b36-9f28-3bff061f12b3)

Use <code>sudo</code> if necessary and a new file called <code>hack_me</code> will be created.

Be sure to use the Linux command <code>cat</code> to display the contents of the file and verify it contains a combination of the <code>shadow</code> and <code>passwd</code> files.


### Use the file for the Password Cracker
Every password cracking tool works differently and your free to use whatever to works for you. 

For the demonstration we will be ussing the tool John the Ripper

John the Ripper requires an input of the hash dump file and without using any other inputs the command:

<code>john ~/hack_me</code> will run brute force mode.

John the Ripper can also perform a dictionary attack which uses a wordlist already contained within the tool. <code>/usr/share/john/password.lst</code>

With all this we can use the command:

<code>john --wordlist=/usr/share/john/password.lst ~/hack_me</code>






