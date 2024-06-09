# POSTMORTEM REPORT
## 0x19. Postmortem, an ALX software engineering project
### 500 Error while accessing a web page

![3819287](https://github.com/Shija-cmd/alx-system_engineering-devops/assets/82152746/156e89d2-3295-4c71-9d2b-22b8fd643e28)
<a href="http://www.freepik.com">Designed by stories / Freepik</a>

#### Introduction
On 5th January 2024 at 7:00 AM (EAT), the server was inaccessible to anyone who wanted to access it. Users reported error 500 
when they were accessing the server.

#### Timeline
* 7:00 AM (EAT), Reported error 500 when accessing some pages of the website
* 7:10 AM (EAT), Checking servers and all database software if they are running
* 7:15 AM (EAT), Diagnosing the Apache logs which included the error logs at /var/log/apache2/error.log
* 7:20 AM (EAT), Find the errors by diagnosing the messages from the error logs
* 7:22 AM (EAT), Checking for syntax errors in some scripts of the Python files
* 7:25 AM (EAT), Checking some configuration files like httpd.conf
* 7:30 AM (EAT), Checking resources like CPU and memory of the server
* 7:35 AM (EAT), Reviewing some changes made recently if there are some changes made
* 7:38 AM (EAT), Checking the database errors in the log files
* 7:40 AM (EAT), Checking the permissions to some directories and files, this can be because some files were not
  given permissions like 755 permissions for directories and 644 for files.
* 7:45 AM (EAT), Restarting the server after fixing some errors in the steps above
* 7:50 AM (EAT), The server is running normally after fixing the error

#### Cause of the Outage
The issue that caused 500 internal server errors was a bad configuration in the httpd.conf file. There were some syntax errors 
in the configuration file which results in preventing APACHE from parsing the file, also some modules were not configured correctly;
for example, the line with the name LoadModule has a typo.

#### Solution of the Outage
The outage was solved by correcting the syntax errors found in the httpd.conf file and after restarting the server, it was 
running normally. 
Also, I listed all modules by running the command httpd -M and correcting the typo in the module which was written loadModule
instead of LoadModule.
Also after resolving the outage, the team established some preventive measures for the outages not occurring and cause some 
inconveniences to the customers. These included:
* Backup regularly
* Doing version control
* Coding clean code and checking for bugs regularly
* Test the load of the server regularly to know its capacity before overloading it
* Using configuration tools like Puppet and
* Proper error handling


