# POSTMORTEM REPORT
## 0x19. Postmortem, an ALX software engineering project
### 500 Error while accessing a web page

#### Introduction
On 5th January, 2024 at 7:00 AM (EAT), the server was not accessible by anyone who wanted to access it. Users reported error 500 
when they were accessing the server.

#### Timeline
* 7:00 AM (EAT), Reported error 500 when accessing some pages of the website
* 7:10 AM (EAT), Checking servers and all database software if they are running
* 7:15 AM (EAT), Diagnosing the apache logs which included the error logs at /var/log/apache2/error.log
* 7:20 AM (EAT), Find the errors by diagnosing the messages from the error logs
* 7:22 AM (EAT), Checking for syntax errors in some scripts of the Python files
* 7:25 AM (EAT), Checking some configuration files like httpd.conf
* 7:30 AM (EAT), Checking resources like CPU and memory of the server
* 7:35 AM (EAT), Reviewing some changes made recently if there are some changes made
* 7:38 AM (EAT), Checking the database errors in the log files
* 7:40 AM (EAT), Checking the permissions to some directories and files, this can be some files were not
  given permissions like 755 permission for directories and 644 for files.
* 7:45 AM (EAT), Restarting the server after fixing some errors in the steps above
* 7:50 AM (EAT), The server is running normally after fixing the error

#### Cause of the Outage
The issue which caused 500 internal server error was bad configuration in the httpd.conf file. There was some syntax errors 
in the configuration file which results preventing APACHE to parse the file, also some modules were not configured correctly;
for example the line with the name LoadModule has typo.

#### Solution of the Outage
The outage was solved by correcting the syntax errors found in the httpd.conf file and after restarting the server, it was 
running normally. 
Also listed all modules by running the command httpd -M and correct the typo in the module which was written loadModule
instead of LoadModule.
Also after resolving the outage, the team established some preventive measures for the outages not occur and cause some 
incoviniences to the customres. These included:
* Backup regularly
* Doing version control
* Coding clean code and checking for bugs regularly
* Test the load of the server regularly to know its capacity before overloading it
* Using configuration tools like puppet and
* Proper error handling


