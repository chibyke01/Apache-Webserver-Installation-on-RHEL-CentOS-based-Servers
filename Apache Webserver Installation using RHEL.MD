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

Step 1 - SSH into the EC2 terminal using the widnows cmd prompt. Changed permission to root user using the below cmd:

`root -i` 

![Alt text](image.png)

Run the below command to update the seever and install the Apache webserver as this will install the latest version of the web server.
```
yum update -y
yum install httpd -y
     or
yum install httpd
```
![Alt text](image-1.png)
![Alt text](image-2.png)
