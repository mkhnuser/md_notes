# Nginx

## Web-servers overview

There is a separation between HTTP-server and Application Server (gunicorn, uwsgi).
You usually have both: HTTP-server (nginx, for example) handles HTTP-related stuff,
whereas application server transforms HTTP-request into Python entities and the other
way around: Python Entities into HTTP-response.

## Nginx Basics

You configure nginx using directives, directives become available by *modules*.
Some modules are preinstalled, therefore some directives are preinstalled too.

When you start nginx, a master process is created (usually with root privileges).
This master process creates worker processes which are responsible for requests handling.

## Modular Organization

nginx is composed of multiple modules; the most important one is http-module, which introduces http directive-block,
server block and location block. server block allows you to introduce virtual hosts. You can think of virtual hosts as sites
which can be found within nginx http-server.

The server..server_name directive assigns one or more hostnames to the server block. When NGINX
receives an HTTP request, it matches the Host header of the request against all server blocks. The
first server block to match this hostname is selected.
