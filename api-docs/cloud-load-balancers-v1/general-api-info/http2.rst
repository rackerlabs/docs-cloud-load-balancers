.. _http2:

==============
HTTP/2 Support
==============

HTTP/2 is the next major iteration of the HTTP protocol and is
intended as a replacement for HTTP/1.x. HTTP/2 is designed
to improve page-load times over high latency connections,
most notably by supporting transaction
multiplexing over a single TCP connection.

HTTP/2 is supported in Cloud Load Balancers for client-side requests.
This allows HTTP/2 enabled clients making request to Cloud Load Balancers
to take advantage of the performance gains at the load balancer
without the need to upgrade the server application.

HTTP/2 is enabled by default for all client connections to a configured
load balancer. If an HTTP/2 client connects to a configured load balancer the
HTTP/2 data received from a client will be translated to HTTP/1.1
before processing it and forwarding it to the load balanced application defined
by the configured load balancer `nodes`.

Some browsers do not support HTTP/2 over an unencrypted connection.
To maximize the number of users who can access the service using HTTP/2,
it is recommended that you enable `SSL Termination` feature for your
load balancer. 
