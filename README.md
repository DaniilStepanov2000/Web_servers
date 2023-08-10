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
