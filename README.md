# CyberOperations
Incidents_Events_logging


Exercise 1: Local Logging: Configuring, Monitoring, and Analyzing Windows Logs
Windows OS tracks various events, activities, and functions through logs. The events recorded are categorized as application, security, setup, system and forwarded events.

Lab Scenario
Log files is an important source that provides SOC about events and incidents to detect attacks, fraud, and inappropriate uses of data within a system.
As a SOC analyst, you should be aware of logging mechanism of Windows OS, location where logs gets stored, configuration needed to log specific type of incidents, format of logs, etc.


Lab Objectives
The objective of this lab is to help students learn how to configure, view, and analyze Windows security logs.
Lab Tasks
1.	Click WinServer2012 to launch WinServe2012 Machine , click Ctrl+Alt+Delete link to login.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/737ad925-dca2-4c93-bba4-527549973381" />
 
If you get "Do you want to allow your PC to be discoverable by other PCs and devices on this network?" prompt, click Yes.

 
2.	Windows audit policy decides what data is logged in the security logs. Configuring audit policy to record failed login attempts will help identify unauthorized users trying to access the system. To enable auditing of Sucessfull and failed logins, click the Windows Start and click Search icon. Type Local Security Policy in the Search textbox and press Enter to open the Windows Local Security Policy editor.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/5455fa29-7d39-44dc-9af5-775ef1afa465" />


3.	The Local Security Policy window will open. Expand Local Policies and click Audit Policy. You will see the categories of security-related events for configuring audit policy. To enable auditing of Sucessfull and failed logins, double-click Audit logon events displayed in the right pane.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/04c5fdef-3cda-464e-870d-6c64dc10e3ec" />


4.	Audit logon events Properties window will appear. Check Success and Failure checkboxes to enable logging both sucessfull and failed login attempts by users and click Apply. Click OK to close the window. Close the Local Security Policy window. Similarly, you can enable any of the listed category policy for auditing. For example to log events related to access of files, folders, registry keys and printers enable Audit Access Object.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/c630fee7-6798-4616-96e9-b58b6afc3804" />

5.	launch Kali Linux Machine.

 
6.	To generate logs for failed and sucessfull login attempts in WinServer2012, use Hydra, a brute force password cracking tool, click on the terminal icon from the favourites bar. Type hydra -L '/root/Wordlist/userlist.txt' -P '/root/Wordlist/pass.txt' ftp://10.10.10.12. Press Enter
This command will attempt brute force attack to crack username and password for FTP using a dictionary to guess the valid combination of username and passwords from the specified text files. The userlist.txt file in root/Wordlist folder contains the list of usernames for performing brute force attack, and the pass.txt file in root/Wordlist folder contains the list of passwords for performing brute force attack.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/34824cf4-0012-4bb6-b7dd-35062e0efc37" />

7.	Hydra tries various combinations of usernames and passwords present in the userlist.txt and pass.txt files on the target, and after 30 login tries found 1 valid username: Administrator with password:Pa$$w0rd for FTP login.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/5a9edbde-9a4e-4ad6-b150-51167211312e" />

8.	Try to log in to the target using one of the cracked username and password combinations. Use administrators' credentials to gain access to the server.

9.	In the terminal, type ftp 10.10.10.12 and press Enter.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/557a0e68-ba41-4450-9dae-c5eb84c6751c" />

10.	Enter Administrators' user credentials, type administrator and Pa$$w0rd as credentials to check whether you can successfully log in to the server. You will be able to successfully log in to the server and ftp terminal appears.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/7f58399a-9842-4b73-83b4-c23db748f6b8" />

11.	Enter quit to exit the FTP terminal. Close all the open terminals.

 
12.	Enter WinServer2012. Since WinServer2012 is configured to audit both failed and sucessfull login attempts. To view the logs of login attempts made by Hydra for brute force attempts, right-click Windows Start button and click Event Viewer.
<img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/bba14cd1-6521-4a78-96c5-673299069b9d" />

13.	Event Viewer window appears, expand Windows Logs from the left pane and click Security from the left pane. Click Filter Current Log… from the right pane.
Windows records the sucess and failed login attempts log under Security category.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/e09b19bf-23f0-4ab9-8a34-a088c64683a4" />

14.	Filter Current Log window appears, enter the ID 4625 in the Event IDs field and click OK to filter out logs related to login failed attempts.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/b7a37f8a-ecbd-4d9c-b1d6-e1c80dc752cf" />

To display logs related to failed login attempts only, use the Filter Current log feature of Windows event Viewer. This will filter and display logs related to the specified ID 4625.  

15.	Audit Failure log entries are shown. Click on one of the entries to view its details.
 <img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/b0d100ef-d873-4e50-884f-fccb259f92e6" />

16.	These logs will be stored in the C:\Windows\System32\winevt\Logs location.
 
In this exercise you have learned how to configure, view, and analyze Windows security logs.

Assessment 3.1.1:
Write down the event ID (number) associated with the audit failure log events in the event viewer.

