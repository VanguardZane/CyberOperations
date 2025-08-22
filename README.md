# CyberOperations
Incidents_Events_logging


Exercise 1: Local Logging: Configuring, Monitoring, and Analyzing Windows Logs
Windows OS tracks various events, activities, and functions through logs. The events recorded are categorized as application, security, setup, system and forwarded events.
Lab Scenario
Log file is an important source that provides the idea to SOC about the flaws or problems and also helps to detect the attack, fraud, inappropriate uses of data.
As a SOC analyst, you should be aware of logging mechanism of Windows OS, location where logs gets stored, configuration needed to log specific type of incidents, format of logs, etc.
Lab Objectives
The objective of this lab is to help students learn how to configure, view, and analyze Windows security logs.
Lab Tasks
1.	Click WinServer2012 to launch WinServe2012 Machine , click Ctrl+Alt+Delete link to login.
 
2.	By default Administrator account is selected, click Pa$$w0rd and press Enter to login.
 
If you get "Do you want to allow your PC to be discoverable by other PCs and devices on this network?" prompt, click Yes.
 
3.	Windows audit policy decides what data is logged in the security logs. Configuring audit policy to record failed login attempts will help identify unauthorized users trying to access the system. To enable auditing of Sucessfull and failed logins, click the Windows Start and click Search icon. Type Local Security Policy in the Search textbox and press Enter to open the Windows Local Security Policy editor.
 
4.	The Local Security Policy window will open. Expand Local Policies and click Audit Policy. You will see the categories of security-related events for configuring audit policy. To enable auditing of Sucessfull and failed logins, double-click Audit logon events displayed in the right pane.
 
5.	Audit logon events Properties window will appear. Check Success and Failure checkboxes to enable logging both sucessfull and failed login attempts by users and click Apply. Click OK to close the window. Close the Local Security Policy window. Similarly, you can enable any of the listed category policy for auditing. For example to log events related to access of files, folders, registry keys and printers enable Audit Access Object.
 
6.	Click Kali Linux to launch Kali Linux Machine. To login, drag the blue screen upwards. Type root in the Username field and press Enter.
 
7.	Type toor in the password field and press Enter.
 
8.	To generate logs for failed and sucessfull login attempts in WinServer2012, use Hydra, a brute force password cracking tool, click on the terminal icon from the favourites bar. Type hydra -L '/root/Wordlist/userlist.txt' -P '/root/Wordlist/pass.txt' ftp://10.10.10.12. Press Enter
This command will attempt brute force attack to crack username and password for FTP using a dictionary to guess the valid combination of username and passwords from the specified text files. The userlist.txt file in root/Wordlist folder contains the list of usernames for performing brute force attack, and the pass.txt file in root/Wordlist folder contains the list of passwords for performing brute force attack.
 
9.	Hydra tries various combinations of usernames and passwords present in the userlist.txt and pass.txt files on the target, and after 30 login tries found 1 valid username: Administrator with password:Pa$$w0rd for FTP login.
 
10.	Try to log in to the target using one of the cracked username and password combinations. In this lab, use administrators' credentials to gain access to the server.
11.	In the terminal, type ftp 10.10.10.12 and press Enter.
 
12.	Enter Administrators' user credentials, type administrator and Pa$$w0rd as credentials to check whether you can successfully log in to the server. You will be able to successfully log in to the server and ftp terminal appears.
 
13.	Enter quit to exit the FTP terminal. Close all the open terminals.
 
14.	Now, click WinServer2012. Since WinServer2012 is configured to audit both failed and sucessfull login attempts. To view the logs of login attempts made by Hydra for brute force attempts, right-click Windows Start button and click Event Viewer.
 
15.	Event Viewer window appears, expand Windows Logs from the left pane and click Security from the left pane. Click Filter Current Log… from the right pane.
Windows records the sucess and failed login attempts log under Security category.
 
16.	Filter Current Log window appears, enter the ID 4625 in the Event IDs field and click OK to filter out logs related to login failed attempts.
 
To display logs related to failed login attempts only, use the Filter Current log feature of Windows event Viewer. This will filter and display logs related to the specified ID 4625.  
17.	Audit Failure log entries are shown. Click on one of the entries to view its details.
 
17.	Close all open windows. In this way, Windows OS keeps track of various activities in the form of logs. These logs will be stored in the C:\Windows\System32\winevt\Logs location.
Do not cancel the lab session. You will need the configurations done in this exercise for the upcomming exercises of this module. In case, if you cancel the lab session, you need to perform this lab steps again.
End of the Exercise
In this exercise you have learnt how to configure, view, and analyze Windows security logs.
Assessment 3.1.1:
Write down the event ID (number) associated with the audit failure log events in the event viewer.

