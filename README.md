# Web-servers
This repository contains different variants of HTTP web-servers like static Apache HTTP Server, Apache HTTP Server + CGI and etc.
## Motivation
The main idea of this project is to figure out what types of HTTP servers exist and how they work.
## Samples of servers
### Static Apache Server
To run static Apache do the following steps:
1. Install Docker.
2. Copy current repository.
3. Go to the root project directory:
```
cd Web-servers
```
4. Buld the docker image:
```
docker build Apache_Server_default_static/. -f Apache_Server_default_static/Dockerfile -t apache_server_default_static
```
5. Run the docker container:
```
docker run -d -p 8081:80 --name apache_server_default_static_container apache_server_default_static
```
6. Enter in a browser __0.0.0.0:8081__. If a browser returns the html page with the message: *It works*, it means that Apache Server works well.
### Apache Server with CGI
1. Install Docker.
2. Copy current repository.
3. Go to the root project directory:
```
cd Web-servers
```
4. Buld the docker image:
```
docker build Apache_Server_plus_cgi/. -f Apache_Server_plus_CGI/Dockerfile -t apache_server_cgi
```
5. Run the docker container:
```
docker run -d -p 8081:80 --name apache_server_cgi_container apache_server_cgi                  
```
6. Connect to the container:
```
docker exec -it apache_server_cgi_container /bin/bash
```
7. Go the server config
```
cd conf
```
8. Open with nano httpd.conf and uncomment the following:
```
<IfModule !mpm_prefork_module>
        #LoadModule cgid_module modules/mod_cgid.so
</IfModule>
<IfModule mpm_prefork_module>
        #LoadModule cgi_module modules/mod_cgi.so
</IfModule>
```
9. Go the python file:
```
cd ../cgi-bin/
```
10. Change permissions for file test_cgi.py
```
chmod a+x test_cgi.py
```
11. Restart docker container
```
docker stop apache_server_cgi_container && docker start apache_server_cgi_container
```
12. Enter in a browser __0.0.0.0:8081/cgi-bin/test_cgi.py__ If a browser returns the html page with the message: *Hello Word! This is my first CGI program*, it means that Apache Server with CGI works well.
