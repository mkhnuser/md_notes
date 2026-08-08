# Nginx

## Sites

One nginx instance can handle multiple sites.
One defines sites using `server` block.
A site is called a virtual host.

## Processes

When nginx starts, a master process will spawn worker processes to handle requests.
You configure nginx using directives, and directives become available through nginx modules.

## server_name directive

`server_name` directive assigns one or more host names to a virtual host.

When NGINX receives an HTTP request,
it will match the `Host` header of the request against all server blocks found;
the first appropriate server block to match this header is selected.

## location directive

Each location directive has its priority depending on its type.

## Upstream load balancing

Nginx can route traffic to multiple hosts depending on routing strategy.
We specify these hosts under `upstream` directive.
