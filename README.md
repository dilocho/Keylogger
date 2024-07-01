# Keylogger

## Objective
To create a keylogger on Kali Linux and be able to log keystrokes from a separate virtual device on Windows XP using Virtual Box following this tutorial by using the Microsoft-ds exploit on port 445/tcp 

## Tools Used: 
Software: 
- VirtualBox

Operating Systems: 
- Windows XP
- Kali Linux

## Steps:
  1. Install Virtual Box 
  2. Download an apply the Windows XP and Kali Linux OS 
  3. Create a Network Manager 
        a) The reason we do this is so the Kali Linux system and the XP systems are on the same subtnet network. If you skip this step on initial setup both systems will have the same IP addresses. 
        b) Ensure that the firewall on the XP has been disable first! 
        c) After creating the networks test to see the ip configuration by using the “ipconfig” on XP and “ifconfig” on Kali to confirm connection to both. 
  4. After confirming the connection to both we can start the exploit by scanning using “nmap -sV” 
        a) Nmap – is a free network scanner that shows all networks connected to the computer network 
        b) By scanning for our network for the XP device we can see what ports and services are opened that could potentially be exploited 
        c) Since XP has a known exploit using port 445 we will use “Metasploit” to get this to get access. “Metasploit” scans for known security vulnerabilities in a system
  5. To start Metasploit we use the command “msfconsole”
  6. Then we search for the exploit code by typing in “search ms08-067”
  7. Metasploit then comes back with the exploit type and the number listed for it (0)
  8. Typing in “use 0” selects that option. 
  9. We need to then establish the remote host we want to connect to by typing in “set RHOST <ip address> ”
  10. Then type “Run” to run the exploit which then starts up meterpreter
        a) Meterpreter is a 
  11. List all the systems running to find the “exploter.exe” and the corresponding process ID (PID)  
  12. Typing in “migrate <PID>” will then get access to the XP OS
  13. Confirming that you are in the system use “getuid” for the User ID and permissions that you have. 
  14. To change to admin permissions type “getsystem” then confirm permissions with “getuid”
  15. You can then type in “help” to get a list of commands that you can execute on the system
  16. For the keylogger we type in “keyscan_start” to start the keyboard logger program 
  17. To get the data back to Kali Linux we then use “keyscan_dump” to display the keystrokes logged. 
       

## Skills Learned: 
In this lab I learned how to: 
- How to create networks on VirtualBox
- nMap scanning
- Running and using Metasploit
      
## Conclusion: 
Running this project gave valuable insights to how keylogging from a threat actors view looks like. How easy it can run on legacy systems with Metasploit and how important it is to know the latest CVE’s and vulnerabilities on unsupported systems. 

## References: 
  • https://www.youtube.com/watch?v=cxCvv__AfCY&t=26s&ab_channel=Enkripsan
