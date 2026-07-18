# Web Servers

## Different kinds of Web Servers

There is a separation between an HTTP server and an application server.
Here are examples of HTTP servers: nginx, apache.
Examples of application servers: gunicorn, uwsgi.

Your project will usually have both types of servers:

* HTTP server handles HTTP related stuff;
* Application server transforms HTTP request into a programming language entities and vice versa.

      For example, uvicorn python application aerver will transform
      an incoming HTTP request into a python entity which a framework will then use.

      The reverse is also true: a python entity will be transformed
      into an HTTP response, which will be later handled by an HTTP server.

## Static and Dynamic Web Servers

Static web servers just return the requested document,
whereas dynamic web server does document processing.

## NGINX

### Overview

One NGINX instance can handle multiple sites.
You should define sites using `server` directive.
A site is called a virtual host.

When NGINX starts,
if contains a master process which spawns worker processes which handle requests.
You configure NGINX using directives, and directives become available by NGINX modules.

### Server Directive

The server -> server_name directive assigns one or more host names to a virtual host.
When NGINX receives an HTTP request,
it tries to match the `Host` header of the request against all server blocks;
the first appropriate server block to match this header is selected.

### Location Directive

# TODO: Complete this section.
