# INSTALLATION OF APACHE WEBSERVER ON RHEL/CENTOS SERVER
A web server is a Server Side software which listens and processes the client http or https requests. A Request always originates from the client machine to web server where application or other documents are hosted to be served. It can also process web applications files written in various progranning languages such as php into static html file.

Some of the accronmy used in the course of this project are:
* **rpm -** RedHat Package Manager
* **yum -** Yellowdog Updater modified

**N/B -** However we need to be aware that the RHEL/Centos use rpm and yum to execute their commands which is other than the regular sudo linux commands 

## Prerequisites:
* RHEL-9.2.0 active EC2 instance
* Windows Command prompt 
* Admin/Root privilege

**Step 1:** SSH into the EC2 terminal using the widnows cmd prompt. Changed permission to root user using the below cmd:

`sudo -i` 

![image](https://github.com/chibyke01/Apache-Webserver-Installation-on-RHEL-CentOS-based-Servers/assets/103823637/648818ea-9eb3-4069-b4c6-75c97c0384a5)

**Step 2:** Run the below command to update the seever and install the Apache webserver as this will install the latest version of the web server.
```
yum update -y
yum install httpd -y
     or
yum install httpd
```
![image](https://github.com/chibyke01/Apache-Webserver-Installation-on-RHEL-CentOS-based-Servers/assets/103823637/cc9cfbcb-d459-45c8-9f35-fec507d19c89)
![image](https://github.com/chibyke01/Apache-Webserver-Installation-on-RHEL-CentOS-based-Servers/assets/103823637/fed1d587-77c2-44b5-84bb-2b95c773255d)

**Step 3:** From the above screenshot I can confirm that the installation is complete and successful, next I will install some models depending on what is required, but most importantly mysql and the openssl modesl will be installed in the course of this project but will also list other models below:
```
yum install httpd-devel
yum install httpd_perl
yum install mod_perl
yum install php-mysqlnd
```
![image](https://github.com/chibyke01/Apache-Webserver-Installation-on-RHEL-CentOS-based-Servers/assets/103823637/75ddd285-94d8-4e20-ad40-c52b838a123f)
![image](https://github.com/chibyke01/Apache-Webserver-Installation-on-RHEL-CentOS-based-Servers/assets/103823637/70675da0-321d-4035-b517-151d2c39fb7f)

**Step 4:** After installion of the Apache server, you confirm the status and either choose to start or enable using any the below cmds depending on what you choose to do at anytime.

I confirmed the status and it was not running then I started the server as seen in the screenshot below.
```
systemctl status httpd
systemctl start httpd
systemctl stop httpd
systemctl reload httpd
systemctl restart httpd
```
![image](https://github.com/chibyke01/Apache-Webserver-Installation-on-RHEL-CentOS-based-Servers/assets/103823637/10331f3a-42d9-42da-9d94-c0b0431eab40)

# Managing the Apache Service
By default Apache uses port 80/443 to listen, this can be confirmed using the nestat command, however before using the netstat command we need to install the net tools using the command

`yum install net-tools -y`

To confirm the port that Apache is listening run the command below.

`netstat -tupan | grep -i httpd`

![image](https://github.com/chibyke01/Apache-Webserver-Installation-on-RHEL-CentOS-based-Servers/assets/103823637/9a6eb503-b87a-413b-b0d6-fc113149ba8d)

Should we have any other port we want Apache to listen this can be forced using the below comman.

`netstat -tupan | grep -i '80\|443'`

To check what is running on the Apache service.

`ps aux | grep -i [h]ttp`

To check the version: `http -v`

To check if the syntax is ok, lets say some changes were made to the configuration file and we need to check if all is ok with it, run the command.

`httpd -t`

![image](https://github.com/chibyke01/Apache-Webserver-Installation-on-RHEL-CentOS-based-Servers/assets/103823637/fa9e798f-2067-47c2-b484-a0521dcd0a28)

# Configuration file (/etc/httpd/conf/httpd.conf)
* **Server Root** - Root directory for web server configuration.
* **Listen** - Specifies the port to listen on.
* **Include** - Include files into the confirguration.
* **User/group** - Users and Group for Apache to run as.
* **Server token** - Default OS, change of product only.
* **Server signature** - Set to off.
```
/etc/httpd/conf.d/*.conf
/etc/httpd/conf/httpd.conf
```

PID file - Process ID file is a file containing the process identification number (pid) that is stored in a well-defined location of the file system thus allowing other programs to find out the pid of a running script, its stores the process ID of a given program. If you vi into the path using the below command, we see the process ID **14816** of the root server. 

`vi /var/run/httpd/httpd.pid`

![image](https://github.com/chibyke01/Apache-Webserver-Installation-on-RHEL-CentOS-based-Servers/assets/103823637/5e78a8ce-c651-4490-a00b-e1f065e72197)
![image](https://github.com/chibyke01/Apache-Webserver-Installation-on-RHEL-CentOS-based-Servers/assets/103823637/b4fb66c3-9104-4aef-8f18-2617c6327535)

However, if you want to further know how these configurations are done to have an active web page you can reference my 
[**LAMP Stack Implementation project**](https://github.com/chibyke01/DevOps_Projects/blob/814bb8b0ba466654a9ace48306e62f483b1fafc3/Project03_LAMP_Stack_Implementation.MD) and  [**Automating Load Balancer project**](https://github.com/chibyke01/DevOps_Projects/blob/814bb8b0ba466654a9ace48306e62f483b1fafc3/Project08_Automating_Load_Balancer_Configuration_With_Shell_Scripting_Using_Nginx_Webserver.MD)
by clicking on either of the projects as they are links enabled.

# **Thank you**

